---
title: MSdatatype_mappings (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b4251479ebfbd542fa2da436bc7d3d47e7971969
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdatatype_mappings** представление сопоставляет типы данных SQL Server в типы данных, используемые в системах управления базами данных SQL Server (СУБД). Эта таблица хранится в **msdb** базы данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|— Это имя СУБД. Ниже приведены возможные значения и их описания.<br /><br /> **MSSQLSERVER**: назначением является база данных SQL Server.<br />**ORACLE**: целевой является база данных Oracle.<br />**DB2**: целевой является база данных IBM DB2.<br />**SYBASE**: назначением является база данных Sybase.|  
|**sql_type**|**nvarchar(128)**|— Тип данных SQL Server.|  
|**dest_type**|**nvarchar(128)**|— Имя типа данных SQL Server.|  
|**dest_prec**|**bigint**|Это точность типа данных SQL Server.|  
|**dest_create_params**|**int**|Только для внутреннего применения.|  
|**dest_nullable**|**бит**|Показывает тип данных SQL Server поддерживает значение NULL.|  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Указание сопоставления типов данных для издателя Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
