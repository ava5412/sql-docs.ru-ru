---
title: sys.dm_exec_query_profiles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_profiles_TSQL
- sys.dm_exec_query_profiles_TSQL
- dm_exec_query_profiles
- sys.dm_exec_query_profiles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_profiles dynamic management view
ms.assetid: 54efc6cb-eea8-4f6d-a4d0-aa05eeb54081
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: f515f52c624eb0fdb0570f9346c2e5a043efa6d2
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39540525"
---
# <a name="sysdmexecqueryprofiles-transact-sql"></a>sys.dm_exec_query_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Контролирует ход выполнения запросов в реальном времени. Например, используйте данное динамическое административное представление для определения, какая часть запроса выполняется медленно.  Это динамическое административное представление можно объединять с другими за счет столбцов, определенных в поле описания. Или объедините данное динамическое административное представление с другими счетчиками производительности (такими как Системный Монитор, xperf), используя столбцы меток времени.   
  
## <a name="table-returned"></a>Возвращаемая таблица  
 Возвращаемые счетчики есть на каждом операторе и каждом потоке.   Результаты являются динамическими и не соответствую результатам существующих параметров, таких как SET STATISTICS XML ON, которые только создают вывод при завершении запроса.   
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|Определяет сеанс, в котором выполняется этот запрос. Ссылка на dm_exec_sessions.session_id.|  
|request_id|**int**|Идентифицирует целевой запрос. Ссылка на dm_exec_sessions.request_id.|  
|sql_handle|**varbinary(64)**|Идентифицирует целевой запрос. Ссылка на dm_exec_query_stats.sql_handle.|  
|plan_handle|**varbinary(64)**|Идентифицирует целевой запрос (ссылка на dm_exec_query_stats.plan_handle).|  
|physical_operator_name|**nvarchar(256)**|Имя физического оператора.|  
|node_id|**int**|Определяет узел оператора в дереве запросов.|  
|thread_id|**int**|Используется для различения потоков (для параллельного запроса), принадлежащих одному узлу оператора запроса.|  
|task_address|**varbinary(8)**|Определяет задачу SQLOS, используемую этим потоком. Ссылка на dm_os_tasks.task_address.|  
|row_count|**bigint**|Число строк, возвращенных оператором к настоящему моменту.|  
|rewind_count|**bigint**|Число сбросов к текущему моменту.|  
|rebind_count|**bigint**|Число повторных привязок к текущему моменту.|  
|end_of_scan_count|**bigint**|Количество окончаний просмотров к текущему моменту.|  
|estimate_row_count|**bigint**|Предполагаемое количество строк Может быть полезным сравнение estimated_row_count с фактическим row_count.|  
|first_active_time|**bigint**|Время, в миллисекундах, когда оператор был вызван первым.|  
|last_active_time|**bigint**|Время, в миллисекундах, когда оператор был вызван последним.|  
|open_time|**bigint**|Метка времени открытия (в миллисекундах).|  
|first_row_time|**bigint**|Метка времени открытия первой строки (в миллисекундах.)|  
|last_row_time|**bigint**|Метка времени открытия последней строки (в миллисекундах.)|  
|close_time|**bigint**|Метка времени закрытия (в миллисекундах).|  
|относятся|**bigint**|Общее количество затраченного времени (в миллисекундах), использованное к настоящему времени узловыми операциями цели. |  
|cpu_time_ms|**bigint**|Общее время ЦП (в миллисекундах), используемое к настоящему времени узловыми операциями цели.|  
|database_id|**smallint**|Идентификатор базы данных, которая содержит объект, на котором выполняются операции чтения и записи.|  
|object_id|**int**|Идентификатор объекта, на котором выполняются операции чтения и записи. Ссылки на sys.objects.object_id.|  
|index_id|**int**|Индекс (если есть), для которого открыт набор строк.|  
|scan_count|**bigint**|Количество просмотров таблиц и индексов к текущему моменту.|  
|logical_read_count|**bigint**|Количество операций логического считывания к текущему времени.|  
|physical_read_count|**bigint**|Количество операций физического считывания к текущему времени.|  
|read_ahead_count|**bigint**|Количество операций упреждающего чтения к текущему времени.|  
|write_page_count|**bigint**|Число операций записи страниц, вызванных сбросами, к текущему времени.|  
|lob_logical_read_count|**bigint**|Количество операций логического считывания LOB к текущему времени.|  
|lob_physical_read_count|**bigint**|Количество операций физического считывания LOB к текущему времени.|  
|lob_read_ahead_count|**bigint**|Количество операций упреждающего чтения LOB к текущему времени.|  
|segment_read_count|**int**|Количество операций упреждающего чтения сегментов к текущему времени.|  
|segment_skip_count|**int**|Количество сегментов, пропущенных к текущему времени.| 
|actual_read_row_count|**bigint**|Номер строки, считываемые оператор до применения остаточный предикат.| 
|estimated_read_row_count|**bigint**|**Применяется к:** начиная с версии [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] с пакетом обновления 1. <br/>Примерное число строк, считанных оператор до применения остаточный предикат.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Если запрос узла плана не имеет любых IO, все счетчики, относящиеся к IO устанавливаются в значение NULL.  
  
 Счетчики, относящиеся к IO, которые сообщаются этим динамическим административным представлением, являются более детализированными, чем те, которые сообщаются SET STATISTICS IO по следующим двум параметрам:  
  
-   SET STATISTICS IO группирует счетчики для всех IO в заданную таблицу. Благодаря этому динамическому административному представлению вы получите раздельные счетчики для каждого узла в плане запроса, которых выполняет IO в таблицу.    
  
-   Если есть параллельное сканирование, данное динамическое административное представление выдает счетчики для каждого из параллельных потоков, выполняющих сканирование.
 
 Начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, инфраструктуру профилирования статистики выполнения запросов стандарта существует side-by-side с инфраструктуру профилирования статистики выполнения упрощенных запросов. Новый запрос выполнения профилирования инфраструктуру статистики значительно сокращает затраты на производительность сбор статистики выполнения запросов по операторам, например фактического числа строк. Эту функцию можно включить с помощью глобального запуска [флаг трассировки 7412](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md), или автоматически включается при использовании query_thread_profile расширенных событий.

>[!NOTE]
> В разделе упрощенных запросов выполнения профилирования инфраструктуру статистики для уменьшения снижения производительности ЦП и затраченном времени не поддерживаются.

 ЗАДАЙТЕ STATISTICS XML ON и SET STATISTICS PROFILE ON всегда использовать инфраструктуру профилирования статистики выполнения запросов прежней версии.
  
## <a name="permissions"></a>Разрешения  

На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   
   
## <a name="examples"></a>Примеры  
 Шаг 1: Войдите в сеанс, в котором вы планируете выполнить этот запрос, который вы будете анализировать с sys.dm_exec_query_profiles. Чтобы настроить запрос для профилирования используйте SET STATISTICS PROFILE на. Выполните ваш запрос в данном сеансе.  
  
```  
--Configure query for profiling with sys.dm_exec_query_profiles  
SET STATISTICS PROFILE ON;  
GO  

--Or enable query profiling globally under SQL Server 2016 SP1 or above  
DBCC TRACEON (7412, -1);  
GO 
  
--Next, run your query in this session, or in any other session if query profiling has been enabled globally 
```  
  
 Шаг 2: Войдите в второй сеанс, который отличается от сеанса, в котором выполняется запрос.  
  
 Следующее выражение суммирует состояние, достигнутое текущим запросом в сеансе 54.  Для этого оно рассчитывает общее число выходных строк со всех потоков для каждого узла, и сравнивает его с ожидаемым числом выходных строк для этого узла.  
  
```  
--Run this in a different session than the session in which your query is running. 
--Note that you may need to change session id 54 below with the session id you want to monitor.
SELECT node_id,physical_operator_name, SUM(row_count) row_count, 
  SUM(estimate_row_count) AS estimate_row_count, 
  CAST(SUM(row_count)*100 AS float)/SUM(estimate_row_count)  
FROM sys.dm_exec_query_profiles   
WHERE session_id=54
GROUP BY node_id,physical_operator_name  
ORDER BY node_id;  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с выполнением (Transact-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

