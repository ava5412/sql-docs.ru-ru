---
title: Опрос серверов | Документация Майкрософт
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
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c2e7ded81d62f01ec739cd02358410bbae299451
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981856"
---
# <a name="poll-servers"></a>Опрос серверов
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

При использовании системы многосерверного администрирования целевые серверы периодически связываются с главным сервером для загрузки на него данных о выполненных заданиях и для получения новых заданий. Процесс взаимодействия с главным сервером называется *опросом сервера* и выполняется через равные *интервалы опроса.*  
  
## <a name="polling-intervals"></a>Интервалы опроса  
Интервал опроса (равный по умолчанию одной минуте) определяет частоту, с которой целевой сервер будет связываться с главным сервером, чтобы загрузить инструкции и передать на него результаты выполнения задания.  
  
Опрашивая главный сервер, целевой сервер считывает назначенные ему операции из таблицы **sysdownloadlist** базы данных **msdb** . Эти операции контролируют многосерверные задания и различные аспекты работы целевого сервера. Примерами таких операций могут служить удаление задания, вставка задания, запуск задания и обновление интервала опроса, заданного на целевом сервере.  
  
Операции можно опубликовать в таблице **sysdownloadlist** двумя способами:  
  
-   явно, вызвав хранимую процедуру **sp_post_msx_operation** ;  
  
-   неявно, используя другие хранимые процедуры задания.  
  
При изменении расписания выполнения многосерверного задания или шагов задания с помощью хранимых процедур задания или при использовании объектов SQL-DMO (SQL Distributed Management Objects) для контроля многосерверных заданий выполните после изменения следующую команду:  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Это обеспечивает синхронизацию целевых серверов с текущим определением задания.  
  
Если вы используете следующие элементы, явно публиковать операции не требуется:  
  
-   при использовании среды Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] для контроля многосерверных заданий;  
  
-   при использовании хранимых процедур заданий, не изменяющих расписания выполнения заданий и шагов заданий.  
  
**Принудительный опрос главного сервера целевым сервером**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>См. также:  
[Управление событиями](../../ssms/agent/manage-events.md)  
  
