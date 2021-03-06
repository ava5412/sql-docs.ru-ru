---
title: sys.spatial_index_tessellations (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- spatial_index_tessellations
- sys.spatial_index_tessellations_TSQL
- spatial_index_tessellations_TSQL
- sys.spatial_index_tessellations
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_index_tessellations catalog view
ms.assetid: 8b17a9a4-b57f-4220-8138-fc73581b1670
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 766b756ab0b00c3e5239a2fe5063e22eed230861
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221825"
---
# <a name="sysspatialindextessellations-transact-sql"></a>sys.spatial_index_tessellations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

 Представляет сведения о схеме тесселяции и параметрах каждого пространственного индекса.  
  
> [!NOTE]  
>  Сведения о тесселяции в см. в разделе [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md).  
  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта, на котором определен индекс. Каждый (object_id, index_id) пары имеет соответствующую запись [sys.spatial_indexes](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md).|  
|index_id|**int**|Идентификатор пространственного индекса, в котором определен столбец.|  
|tessellation_scheme|**sysname**|Имя схемы тесселяции, один из: GEOMETRY_GRID, GEOGRAPHY_GRID|  
|bounding_box_xmin|**float(53)**|Координата X левого нижнего угла ограничивающего поле один из: NULL = неприменимо для заданной схемы тесселяции (например, GEOGRAPHY_GRID) *n* =, если параметр tessellation_scheme имеет значение координаты x-min GEOMETRY_GRID.                     **Примечание:** координаты определяются параметры ограничивающего прямоугольника, интерпретируются для каждого объекта в соответствии с его [идентификатор пространственной ссылки (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).|  
|bounding_box_ymin|**float(53)**|Y-координата левого нижнего угла ограничивающего поле один из: NULL = неприменимо для заданной схемы тесселяции (например, GEOGRAPHY_GRID) *n* =, если параметр tessellation_scheme имеет значение GEOMETRY_GRID значение координаты y-min|  
|bounding_box_xmax|**float(53)**|Координата X верхнего правого угла ограничивающего поле один из: NULL = неприменимо для заданной схемы тесселяции (например, GEOGRAPHY_GRID) *n* =, если параметр tessellation_scheme имеет значение координаты x-max GEOMETRY_GRID|  
|bounding_box_ymax|**float(53)**|Координата Y верхнего правого угла ограничивающего поле один из: NULL = неприменимо для заданной схемы тесселяции (например, GEOGRAPHY_GRID) *n* =, если параметр tessellation_scheme имеет значение координаты y-max GEOMETRY_GRID|  
|level_1_grid|**smallint**|Плотность сетки верхнего уровня. Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, один из: 16 = сетка 4 на 4 (LOW) 64 = 8, сетка 8 (средний) 256 = 16 сеткой 16 (ВЫСОКИЙ) NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_1_grid_desc|**nvarchar(60)**|Плотность сетки верхнего уровня, один из: низкий средний высокой NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_2_grid|**smallint**|Плотность сетки второго уровня. Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, один из: 16 = сетка 4 на 4 (LOW) 64 = 8, сетка 8 (средний) 256 = 16 сеткой 16 (ВЫСОКИЙ) NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_2_grid_desc|**nvarchar(60)**|Плотность сетки второго уровня, один из: низкий средний высокой NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_3_grid|**smallint**|Плотность сетки третьего уровня.   Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, один из: 16 = сетка 4 на 4 (LOW) 64 = 8, сетка 8 (средний) 256 = 16 сеткой 16 (ВЫСОКИЙ) NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_3_grid_desc|**nvarchar(60)**|Плотность сетки третьего уровня, один из: низкий средний высокой NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_4_grid|**smallint**|Плотность сетки четвертого уровня. Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, один из: 16 = сетка 4 на 4 (LOW) 64 = 8, сетка 8 (средний) 256 = 16 сеткой 16 (ВЫСОКИЙ) NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_4_grid_desc|**nvarchar(60)**|Плотность сетки четвертого уровня, один из: < низкий средний высокой NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|cells_per_object|**int**|Число ячеек на пространственный объект, один из: Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, *n* = число ячеек на объект NULL = неприменимо для заданного типа или тесселяции схему пространственного индекса|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
