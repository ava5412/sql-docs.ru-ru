---
title: Свойства браузера SQL Server (вход в систему) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bacd58650b9c86a455714cfc464b9b995396a83e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273780"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Свойства браузера SQL Server (вкладка «Вход в систему»)
  Программа браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в качестве службы на сервере. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает входящие запросы к ресурсам [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и предоставляет сведения об экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , установленных на компьютере.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Браузер прослушивает UDP-порт и принимает запросы без проверки подлинности с использованием протокола разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSRP).  
  
 Изменение пароля учетной записи вступает в силу немедленно, без перезапуска службы.  
  
## <a name="options"></a>Параметры  
 **Локальная системная учетная запись**  
 Запустите службу « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , браузер» в контексте безопасности локальной системной учетной записи. По возможности используйте учетную запись с небольшим набором прав.  
  
 **Эта учетная запись**  
 Укажите локальную или доменную учетную запись, использующую аутентификацию Windows. Для служб рекомендуется использовать доменную учетную запись с минимальными правами. Дополнительные сведения о выборе учетной записи см. в разделе «Настройка учетных записей служб Windows» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Обзор**  
 Выберите пользователя или встроенного субъекта безопасности.  
  
> [!IMPORTANT]  
>  Используйте учетную запись с минимальными правами. Дополнительные сведения о разрешениях, необходимых для службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделе "Безопасность" статьи [Служба обозревателя SQL Server](../../../2014/tools/configuration-manager/sql-server-browser-service.md).  
  
 **Пароль**  
 Введите пароль субъекта безопасности.  
  
 **Подтверждение пароля**  
 Подтвердите пароль субъекта безопасности.  
  
 **Состояние службы**  
 Указывает, была ли служба запущена, остановлена или отключена. «**…**» указывает, что ожидается изменение состояния.  
  
 **Запуск**  
 Запустить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Остановить**  
 Остановить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Приостановить**  
 Приостановить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Возобновить**  
 Возобновить работу приостановленной службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Служба обозревателя SQL Server](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
