---
title: "Службы SCM. Изменение пароля учетных записей | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fb2daae1f2e891dbf51c096793bb493cea67f9d4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="scm-services---change-the-password-of-the-accounts-used"></a>Службы SCM. Изменение пароля учетных записей
  В этом разделе описано, как менять пароль для учетных записей, используемых компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] и агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью диспетчера конфигурации SQL Server. Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускаются на компьютере как службы, с заданными при установке учетными данными. Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается с учетной записью домена, а пароль для этой учетной записи изменен, то пароль, используемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо обновить. Если этого не сделать, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может потерять доступ к некоторым ресурсам домена и, в случае остановки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , служба не перезапустится до тех пор, пока не будет обновлен пароль.  
  
 Сведения об изменении паролей для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Срок действия пароля истек](http://msdn.microsoft.com/library/9831b194-9ad5-47b0-8009-59c7aef4319b).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разработан для изменения параметров служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и обладает для этого всеми правами. Редактирование параметров службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в диспетчере управления службами Windows (**services.msc**) не всегда меняет все необходимые параметры, что может привести к неправильной работе службы. Однако в кластерной среде после изменения пароля на активном узле с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо изменить пароль и на пассивном узле с помощью диспетчера управления службами.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Для изменения пароля службы необходимо быть администратором компьютера.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a>Изменение пароля службы SQL Server (компонент Database Engine)  
  
1.  Нажмите кнопку **Пуск** , укажите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
    > [!NOTE]  
    >  Так как диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите на **начальной странице**SQLServerManager13.msc (для [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 13 на меньшее число. Если щелкнуть SQLServerManager13.msc, откроется диспетчер конфигурации. Чтобы закрепить диспетчер конфигурации на начальной странице или панели задач, щелкните правой кнопкой мыши SQLServerManager13.msc и выберите пункт **Открыть папку с файлом**. В проводнике щелкните правой кнопкой мыши SQLServerManager13.msc, а затем выберите команду **Закрепить на начальном экране** или **Закрепить на панели задач**.  
    > -   **Windows 8**:  
    >          Чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью чудо-кнопки **Поиск**, введите на вкладке **Приложения** текст **SQLServerManager\<версия>.msc** (например, **SQLServerManager13.msc**) и нажмите клавишу **ВВОД**.  
  
2.  В диспетчере конфигурации SQL Server выберите пункт **Службы SQL Server**.  
  
3.  На панели подробных сведений щелкните **SQL Server (**\<имя_экземпляра>**>)** правой кнопкой мыши и выберите пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства SQL Server (**\<имя_экземпляра>**)** на вкладке "Вход" введите для учетной записи, указанной в поле **Имя учетной записи**, новый пароль в полях **Пароль** и **Подтверждение пароля** и нажмите кнопку **ОК**.  
  
     Новый пароль вступает в силу немедленно, без перезагрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a>Изменение пароля с помощью службы агента SQL Server  
  
1.  Нажмите кнопку **Пуск** , укажите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
2.  В диспетчере конфигурации SQL Server выберите пункт **Службы SQL Server**.  
  
3.  На панели подробных сведений правой кнопкой мыши щелкните **Агент SQL Server (**\<имя_экземпляра>**)** и выберите пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства агента SQL Server (**\<имя_экземпляра>**)** на вкладке "Вход" введите для учетной записи, указанной в поле **Имя учетной записи**, новый пароль в полях **Пароль** и **Подтверждение пароля** и нажмите кнопку **ОК**.  
  
     На отдельном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]пароль вступает в силу сразу же, без перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В кластеризованном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может выключить ресурс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , после чего потребуется перезапуск.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции по управлению службами (диспетчер конфигурации SQL Server)](http://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6)  
  
  
