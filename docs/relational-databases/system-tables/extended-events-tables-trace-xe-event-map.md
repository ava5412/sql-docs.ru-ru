---
title: trace_xe_event_map (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- trace_xe_event_map_TSQL
- trace_xe_event_map
dev_langs:
- TSQL
helpviewer_keywords:
- trace_xe_event_map
- extended events [SQL Server], tables
ms.assetid: 537aa292-3540-47e8-be28-56dc01abc343
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0bf9c9db02063fd46b2119866d755b60757e9ded
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="extended-events-tables---tracexeeventmap"></a>Таблицы расширенных событий - trace_xe_event_map
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого события из числа расширенных событий, сопоставленного с классом событий трассировки SQL. Эта таблица хранится в базе данных master в схеме sys.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|trace_event_id|**smallint**|Идентификатор сопоставленного класса событий трассировки SQL.|  
|package_name|**nvarchar(60)**|Имя пакета расширенных событий, в котором находится сопоставленное событие.|  
|xe_event_name|**nvarchar(60)**|Имя события расширенных событий, которое сопоставлено с классом событий трассировки SQL.|  
  
## <a name="remarks"></a>Замечания  
 Чтобы выявить события расширенных событий, эквивалентные классам событий трассировки SQL, можно использовать следующий запрос:  
  
```  
SELECT te.name, xe.package_name, xe.xe_event_name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NOT NULL  
```  
  
 Не все классы событий имеют эквивалентные расширенные события. Для перечисления классов событий, не имеющих эквивалентных расширенных событий, можно использовать следующий запрос.  
  
```  
SELECT te.trace_event_id, te.name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NULL  
```  
  
 Большинство возвращенных в ответ на предыдущий запрос классов событий связаны с аудитом. Для аудита рекомендуется использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit использует расширенные события в помощь при создании аудита. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
## <a name="see-also"></a>См. также  
 [trace_xe_action_map (Transact-SQL)](../../relational-databases/system-tables/extended-events-tables-trace-xe-action-map.md)  
  
  
