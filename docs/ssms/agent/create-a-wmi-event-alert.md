---
title: Создание предупреждения о событии WMI | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- WMI event alerts [SQL Server Management Studio]
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 62474c013c8d70f32f81c68afcb74e5f5c655535
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983666"
---
# <a name="create-a-wmi-event-alert"></a>Создание предупреждения о событии WMI
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описано, как создать предупреждение агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , вызываемое при возникновении определенного события [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , которое отслеживается поставщиком WMI для событий сервера, в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
Дополнительные сведения об использовании поставщика WMI для наблюдения за событиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] см. в разделе [Поставщик инструментария WMI для классов событий и свойств сервера](http://msdn.microsoft.com/80767fe0-32ac-406a-81a0-8212cd6ce7e4). Дополнительные сведения о разрешениях, которые требуются для получения уведомлений о событиях WMI, см. в разделе [Выбор учетной записи для службы агента SQL Server](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md). Дополнительные сведения о языке WQL см. в разделе [Использование WQL с поставщиком WMI для событий сервера](http://msdn.microsoft.com/58b67426-1e66-4445-8e2c-03182e94c4be).  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Создание предупреждения о событии WMI с помощью:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] обеспечивает простой графический способ управления всей системой предупреждений и рекомендуется для настройки инфраструктуры предупреждений.  
  
-   События, сформированные посредством процедуры **xp_logevent** , появляются в базе данных master. Поэтому **xp_logevent** не вызывает срабатывание предупреждения, если только значение аргумента **@database_name** для предупреждения не равно **'master'** или NULL.  
  
-   На компьютере, где запущен агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , поддерживаются только пространства имен WMI.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
По умолчанию только члены предопределенной роли сервера **sysadmin** могут выполнять процедуру **sp_add_alert**.  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-wmi-event-alert"></a>Создание предупреждения о событии WMI  
  
1.  В **обозревателе объектов** щелкните значок «плюс», чтобы развернуть сервер, на котором нужно создать предупреждение о событии WMI.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой пункт **Предупреждения** и выберите **Создать предупреждение**.  
  
4.  В поле **Имя** диалогового окна **Создание предупреждения** введите имя этого предупреждения.  
  
5.  Установите флажок **Включено** , чтобы разрешить выдачу предупреждения. По умолчанию флажок **Включить** установлен.  
  
6.  В списке **Тип** выберите **Предупреждение о событии WMI**.  
  
7.  В разделе **Определение условий предупреждений о событиях WMI**в поле **Пространство имен** укажите пространство имен WMI для инструкций языка WQL, определяющее события WMI, которые будут приводить к возникновению этого предупреждения.  
  
8.  В поле **Запрос** укажите инструкцию WQL, определяющую событие, на которое реагирует предупреждение.  
  
9. Нажмите кнопку **ОК**.  
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-create-a-wmi-event-alert"></a>Создание предупреждения о событии WMI  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database.',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
Дополнительные сведения см. в разделе [sp_add_alert (Transact-SQL)](http://msdn.microsoft.com/d9b41853-e22d-4813-a79f-57efb4511f09).  
  
