---
title: Набор строк DMSCHEMA_MINING_STRUCTURES | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0aac1d7fb0d8c54ae18cd7b45f5f414a02eafffe
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030515"
---
# <a name="dmschemaminingstructures-rowset"></a>Набор строк DMSCHEMA_MINING_STRUCTURES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Перечисляет информацию о структурах интеллектуального анализа данных в текущем каталоге.  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DMSCHEMA_MINING_STRUCTURES** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Длина|Описание|  
|-----------------|--------------------|------------|-----------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**||Имя каталога.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**||Неполное имя схемы. Значение**NULL** , если схемы не поддерживаются поставщиком.|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**||Имя структуры. Этот столбец не может содержать значение **NULL**.|  
|**STRUCTURE_GUID**|**DBTYPE_GUID**||Идентификатор GUID, который однозначно определяет структуру. Значение**NULL** , если не поддерживается поставщиком.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Краткое описание структуры. Значение**NULL** , если со структурой не связано описание.|  
|**STRUCTURE_PROPID**|**DBTYPE_UI4**||Идентификатор свойства структуры. Значение**NULL** , если не поддерживается поставщиком.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||Дата создания структуры. Значение**NULL** , если не предоставляется поставщиком.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Дата последнего изменения структуры. Значение**NULL** , если не предоставляется поставщиком.|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**||Инструкция, которая использовалась для создания первоначальной модели интеллектуального анализа данных (необязательно).|  
|**IS_POPULATED**|**DBTYPE_BOOL**||Логическое значение, которое указывает, заполнена ли структура.<br /><br /> **VARIANT_TRUE** , если структура заполнена; **VARIANT_FALSE** в противном случае.|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**||Дата последней обработки структуры. Значение**NULL** , если не предоставляется поставщиком.|  
|**HOLDOUT_MAXPERCENT**|**DBTYPE_ UI1**||Заданное пользователем значение, которое указывает максимальную процентную долю входных вариантов, зарезервированных как проверочный набор.<br /><br /> 0 или значение **NULL** указывает на отсутствие ограничения.|  
|**HOLDOUT_MAXCASES**|**DBTYPE_UI8**||Заданное пользователем значение, которое указывает максимальное количество входных вариантов, зарезервированных как проверочный набор.<br /><br /> 0 или значение **NULL** указывает на отсутствие ограничения.|  
|**HOLDOUT_SEED**|**DBTYPE_UI8**||Заданное пользователем значение, которое используется как начальное значение для повторяемого секционирования.<br /><br /> Значение 0 указывает, что в качестве начального значения используется хэш идентификатора структуры интеллектуального анализа данных.|  
|**HOLDOUT_ACTUAL_SIZE**|**DBTYPE_UI8**||Если структура интеллектуального анализа данных обработана, это значение указывает фактический размер проверочного набора данных, выраженный как количество вариантов.<br /><br /> Значение**NULL** указывает, что структура интеллектуального анализа данных не обработана.|  
  
 Набор строк отсортирован по **STRUCTURE_CATALOG**, **STRUCTURE_SCHEMA**, **STRUCTURE_NAME**.  
  
## <a name="restriction-columns"></a>Столбцы ограничений  
 Набор строк **DMSCHEMA_MINING_STRUCTURES** может быть ограничен столбцами, перечисленными в следующей таблице.  
  
|Имя столбца|Индикатор типа|Состояние ограничения|  
|-----------------|--------------------|-----------------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**|Необязательно.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**|Необязательно.|  
|**STRUCTURE_NAME**|**DBTYPE_WSTR**|Необязательно.|  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк схемы интеллектуального анализа данных](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
