---
title: Свойства браузера SQL Server (вкладка "Вход в систему") | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 814b8f9f6c94e0c0907ee662565fd5377455a5a9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38022622"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Свойства браузера SQL Server (вкладка «Вход в систему»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
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
>  Используйте учетную запись с минимальными правами. Дополнительные сведения о разрешениях, необходимых для службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделе "Безопасность" статьи [Служба обозревателя SQL Server](../../tools/configuration-manager/sql-server-browser-service.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Служба обозревателя SQL Server](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
