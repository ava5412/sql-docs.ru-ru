---
title: CDC.index_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc.index_columns_TSQL
- cdc.index_columns
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.index_columns
ms.assetid: 256ec8a5-3031-40a8-9fdb-99db42ea453d
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0e955837317912d1f77c0964be575bff4cc490e8
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103622"
---
# <a name="cdcindexcolumns-transact-sql"></a>cdc.index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждого столбца индекса, связанного с таблицей изменений. Столбцы индекса используются в системе отслеживания измененных данных для уникальной идентификации строк исходной таблицы. По умолчанию столбцы первичного ключа исходной таблицы также включены в индексацию. Однако, если исходной таблице после активации системы отслеживания измененных данных был присвоен уникальный индекс, то вместо столбцов первичного ключа используются столбцы указанного индекса. Первичный ключ или уникальный индекс исходной таблицы используется при отслеживании сетевых изменений. Дополнительные сведения см. в разделе [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 Не рекомендуется непосредственно запрашивать системные таблицы. Вместо этого выполните [sys.sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md) хранимой процедуры.  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор таблицы изменений.|  
|**column_name**|**sysname**|Имя столбца индекса.|  
|**index_ordinal**|**tinyint**|Порядковый номер (нумерация начинается с 1) столбца внутри индекса.|  
|**column_id**|**int**|Идентификатор столбца в исходной таблице.|  
  
## <a name="see-also"></a>См. также  
 [CDC.change_tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
