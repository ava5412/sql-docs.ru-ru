---
title: Назначение резервного оператора | Документация Майкрософт
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
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e86a296ae43c197aeaad3a92dc2c1c8a01de0fc2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38002956"
---
# <a name="designate-a-fail-safe-operator"></a>Назначение резервного оператора
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Резервный оператор — это пользователь, который получает предупреждение, если нужный оператор недоступен. В этом разделе описана настройка резервного оператора для получения уведомлений от агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [Ограничения](#Restrictions)  
  
    [безопасность](#Security)  
  
-   **Назначение резервного оператора с помощью:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
  
-   Режимы отправки уведомлений с помощью пейджера и команды **net send** будут удалены из агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в следующей версии [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Старайтесь не использовать эти функции в новых разработках и предусмотрите соответствующие изменения в приложениях, которые используют их в настоящее время.  
  
-   Обратите внимание, что для использования компонента Database Mail для отправки операторам уведомлений по электронной почте и на пейджер агент SQL Server необходимо настроить для использования компонента Database Mail. Дополнительные сведения см. в разделе [Назначить предупреждения для оператора](http://msdn.microsoft.com/library/ms190038.aspx).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
### <a name="Security"></a>безопасность  
  
#### <a name="Permissions"></a>Permissions  
Только члены предопределенной роли сервера **sysadmin** могут назначать резервных операторов.  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-designate-a-fail-safe-operator"></a>Назначение резервного оператора  
  
1.  В **обозревателе объектов** щелкните знак "плюс", чтобы развернуть сервер, который содержит оператора агента SQL Server, назначаемого в качестве резервного.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server** и выберите пункт **Свойства**.  
  
3.  В диалоговом окне *Свойства агента SQL —***имя_сервера* в разделе **Выберите страницу** выберите **Система предупреждений**.  
  
4.  В разделе **Резервный оператор**выберите **Включить резервный оператор**.  
  
5.  В списке **Оператор** выберите оператор, который необходимо сделать резервным.  
  
6.  Установите некоторые или все указанные флажки для выбора способа уведомления оператора: **Электронная почта**, **Пейджер**или **Net send**.  
  
7.  После завершения нажмите кнопку **ОК**.  
  
