---
title: Определение действий в ответ на предупреждение (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 91eebf84cdcb9750e7a5aef10b88b1c3b0bbc31e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200704"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a>Определение реакция на предупреждение (среда SQL Server Management Studio)
  В этом разделе описано, как определить реакцию [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на предупреждения агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Определение ответа на предупреждение**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Режимы отправки уведомлений с помощью пейджера и команды **net send** будут удалены из агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в следующей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
-   Обратите внимание, что для использования компонента Database Mail для отправки операторам уведомлений по электронной почте и на пейджер агент SQL Server необходимо настроить для использования компонента Database Mail. Дополнительные сведения см. в разделе [Назначить предупреждения для оператора](http://msdn.microsoft.com/library/ms190038.aspx).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Только члены предопределенной роли сервера **sysadmin** могут задавать отклик на предупреждение.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-define-the-response-to-an-alert"></a>Определение ответа на предупреждение  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, содержащий предупреждение, для которого необходимо задать отклик.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Чтобы развернуть папку **Предупреждения** , щелкните значок "плюс".  
  
4.  Щелкните правой кнопкой предупреждение, для которого необходимо определить отклик, и выберите **Свойства**.  
  
5.  В разделе *Выбор страницы* диалогового окна **Свойства предупреждения***имя_предупреждения** выберите **Отклик**.  
  
6.  Выберите флажок **Выполнить задание** и из списка под пунктом **Выполнить задание** выберите задание, которое необходимо выполнить при возникновении предупреждения. Чтобы выбрать новое задание, нажмите кнопку **Создать задание**. Для получения дополнительных сведений о заданиях нажмите кнопку **Просмотр заданий**. Дополнительные сведения о параметрах, доступных в диалоговых окнах **Создание задания** и *Свойства задания***имя_задания*, см. в разделах [Создание задания](create-a-job.md) и [Просмотр задания](view-a-job.md).  
  
7.  Выберите флажок **Уведомлять операторов** , если необходимо уведомлять операторов в момент активации предупреждения. В списке **Список операторов**выберите один или несколько из следующих методов оповещения оператора или операторов: **Электронная почта**, **Пейджер**или **Net send**. Вы можете создать нового оператора, нажав кнопку **Создать оператора**. Вы можете просмотреть дополнительные сведения об операторе, нажав кнопку **Просмотр оператора**. Дополнительные сведения о доступных параметрах в диалоговых окнах **Создать оператора** и **Просмотр свойств оператора** см. в разделах [Create an Operator](create-an-operator.md) и [View Information About an Operator](view-information-about-an-operator.md).  
  
8.  После завершения нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-define-the-response-to-an-alert"></a>Определение ответа на предупреждение  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that François Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'François Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).  
  
  
