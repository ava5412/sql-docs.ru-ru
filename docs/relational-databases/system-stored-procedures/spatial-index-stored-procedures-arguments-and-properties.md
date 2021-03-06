---
title: Аргументы и свойства пространственного индекса хранимых процедур | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- spatial indexes [SQL Server], stored procedures
ms.assetid: ee26082b-c0ed-40ff-b5ad-f5f6b00f0475
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 20c747b51bd4fc20e21bedfed1f826005b1037a1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262897"
---
# <a name="spatial-index-stored-procedures---arguments-and-properties"></a>Хранимые процедуры - аргументов и свойств пространственного индекса
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе перечислены аргументы и свойства хранимых процедур пространственного индекса.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
 Синтаксис определенных хранимых процедур пространственного индекса см. в следующих разделах.  
  
-   [sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [sp_help_spatial_geometry_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [sp_help_spatial_geography_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [sp_help_spatial_geography_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="arguments"></a>Аргументы  
 [  **@tabname =**] **"***tabname***"**  
 Полное или неполное имя определенной таблицы, для которой был указан пространственный индекс.  
  
 Кавычки требуются, только если определяется уточненная таблица. Если предоставлено полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. *tabname* — **nvarchar**(776) и не имеет значения по умолчанию.  
  
 [  **@indexname =** ] **"***indexname***"**  
 Имя указанного пространственного индекса. *имя_индекса* — **sysname** без значения по умолчанию.  
  
 [  **@verboseoutput =** ] **"***verboseoutput***"**  
 Диапазон возвращаемых имен свойств и значений.  
  
 0 = основные свойства  
  
 \>0 = все свойства  
  
 *verboseoutput* — **tinyint** без значения по умолчанию.  
  
 [  **@query_sample =** ] **"***query_sample***"**  
 Это репрезентативный образец запроса, который можно использовать для проверки ценности индекса. Это может быть репрезентативный объект или окно запроса. *query_sample* — **geometry** без значения по умолчанию.  
  
 [  **@xml_output =** ] **"***xml_output***"**  
 Этот выходной параметр возвращает результирующий набор во фрагменте XML. *xml_output* — **xml** без значения по умолчанию.  
  
## <a name="properties"></a>Свойства  
 Задать **@verboseoutput** = 0 для возврата основных свойств, как показано в таблице ниже. **@verboseoutput** > 0 для возврата всех свойств пространственного индекса.  
  
 **Base_Table_Rows**  
 Количество строк в базовой таблице. Значение — **bigint**.  
  
 **Столбцах Bounding_Box_xmin**  
 Свойства ограничивающего прямоугольника пространственного индекса для X-minimum **geometry** типа. Это свойство имеет значение NULL для **geography**типа. Значение — **float**.  
  
 **Bounding_Box_ymin**  
 Минимальная свойства ограничивающего прямоугольника пространственного индекса для оси Y **geometry** типа. Это свойство имеет значение NULL для **geography** типа. Значение — **float**.  
  
 **Bounding_Box_xmax**  
 Свойства ограничивающего прямоугольника пространственного индекса для X-maximum **geometry** типа. Это свойство имеет значение NULL для **geography** типа. Значение — **float**.  
  
 **Bounding_Box_ymax**  
 Свойства ограничивающего прямоугольника пространственного индекса для Y-maximum **geometry** типа. Это свойство имеет значение NULL для **geography** типа. Значение — **float**.  
  
 **Grid_Size_Level_1**  
 Плотность сетки первого уровня пространственного индекса:  
  
 16 для LOW  
  
 64 для MEDIUM  
  
 256 для HIGH  
  
 Значение — **int**.  
  
 **Grid_Size_Level_2**  
 Плотность сетки второго уровня пространственного индекса:  
  
 16 для LOW  
  
 64 для MEDIUM  
  
 256 для HIGH  
  
 Значение — **int**.  
  
 **Grid_Size_Level_3**  
 Плотность сетки третьего уровня пространственного индекса:  
  
 16 для LOW  
  
 64 для MEDIUM  
  
 256 для HIGH  
  
 Значение — **int**.  
  
 **Grid_Size_Level_4**  
 Плотность сетки четвертого уровня пространственного индекса:  
  
 16 для LOW  
  
 64 для MEDIUM  
  
 256 для HIGH  
  
 Значение — **int**.  
  
 **Cells_Per_Object**  
 Число ячеек на пространственный объект (свойство индекса). Значение — **int**.  
  
 **Total_Primary_Index_Rows**  
 Количество строк в индексе. Значение — **bigint**.  
  
 **Total_Primary_Index_Pages**  
 Количество страниц в индексе. Значение — **bigint**.  
  
 **Average_Number_Of_Index_Rows_Per_Base_Row**  
 Количество строк в индексе / количество строк в базовой таблице. Значение — **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample**  
 Указывает, попадают ли образец репрезентативного запроса за пределами ограничивающего прямоугольника **geometry** индекса и в корневую ячейку (ячейка уровня 0). Это либо значение 0 (не в ячейке уровня 0), либо 1. Если входит в ячейку уровня 0, то анализируемый индекс не может быть использован в образце запроса. Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level0_In_Index**  
 Количество экземпляров ячеек индексированных объектов тесселируются на уровне 0 (корневая ячейка, вне ограничивающего прямоугольника для **geometry**). Это свойство является основным. Значение — **bigint**.  
  
 Для **geometry** индексов, это происходит, если ограничивающий прямоугольник индекса меньше, чем домен данных. Большое количество объектов на уровне 0 может потребоваться дополнительные фильтры, если окно запроса не входит полностью в ограничивающий прямоугольник и снизит производительность индекса (например, **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample** -1). Если окно запроса не входит в ограничивающий прямоугольник, то большое количество объектов на уровне 0 может действительно повысить производительность индекса.  
  
 NULL и пустые экземпляры считаются на уровне 0, но не влияют на производительность. На уровне 0 имеется столько же ячеек, что и для NULL, при этом пустые экземпляры входят в базовую таблицу. Для **geography** индексов уровня 0 будет столько ячеек, как значения NULL и пустые экземпляры + 1 ячейка, поскольку образец запроса считается за 1.  
  
 **Total_Number_Of_ObjectCells_In_Level1_In_Index**  
 Количество экземпляров ячеек индексированных объектов тесселируются с точностью первого уровня. Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level2_In_Index**  
 Количество экземпляров ячеек индексированных объектов тесселируются с точностью второго уровня. Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level3_In_Index**  
 Количество экземпляров ячеек индексированных объектов тесселируются с точностью третьего уровня. Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_ObjectCells_In_Level4_In_Index**  
 Количество экземпляров ячеек индексированных объектов тесселируются с точностью четвертого уровня. Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level1_In_Index**  
 Количество ячеек, которые полностью входят в объект на уровне 1 и таким образом, являются внутренними для объекта. (Cell_attributevalue составляет 2). Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level2_In_Index**  
 Количество ячеек, которые полностью входят в объект на уровне 2 и таким образом, являются внутренними для объекта. (Cell_attribute имеет значение 2.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level3_In_Index**  
 Число ячеек, которые полностью входят в объект на уровне тесселяции 3 и таким образом, являются внутренними для объекта. (Cell_attribute имеет значение 2.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_interior_ObjectCells_In_Level4_In_Index**  
 Количество ячеек, которые полностью входят в объект на уровне тесселяции 4 и, следовательно, являются внутренними для объекта. (Cell_attribute имеет значение 2.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level1_In_Index**  
 Число ячеек, которые пересекаются объектом на уровне 1. (Cell_attribute имеет значение 1.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level2_In_Index**  
 Число ячеек, которые пересекаются объектом на уровне 2. (Cell_attribute имеет значение 1.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level3_In_Index**  
 Число ячеек, которые пересекаются объектом на уровне 3. (Cell_attribute имеет значение 1.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level4_In_Index**  
 Число ячеек, которые пересекаются объектом на уровне тесселяции 4. (Cell_attribute имеет значение 1.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_For_QuerySample**  
 Указывает, находится ли образец запроса в корневой ячейке 0 вне ограничивающего прямоугольника, но на границе с ним. Это свойство является основным. Значение — **bigint**.  
  
> [!NOTE]  
>  Эти данные используются только при определении наличия объектов, которые почти соприкасаются с ограничивающим прямоугольником.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_In_Index**  
 Количество объектов на уровне 0, которые граничат с ограничивающим прямоугольником. (Cell_attribute имеет значение 0.)  Значение — **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level1_In_Index**  
 Количество ячеек, которые граничат границе ячейке сетки на уровне тесселяции 1. (Cell_attribute имеет значение 0.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level2_In_Index**  
 Количество ячеек, которые граничат границе ячейке сетки на уровне тесселяции 2. (Cell_attribute имеет значение 0.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level3_In_Index**  
 Количество ячеек, которые граничат границе ячейке сетки на уровне тесселяции 3. (Cell_attribute имеет значение 0.) Это свойство является основным. Значение — **bigint**.  
  
 **Total_Number_Of_Border_ObjectCells_In_Level4_In_Index**  
 Количество ячеек, которые граничат с ячейкой сетки на уровне тесселяции 4. (Cell_attribute имеет значение 0.) Это свойство является основным. Значение — **bigint**.  
  
 **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 Доля в процентах от общей области (общее количество конечных ячеек) сетки, в которой содержатся конечные ячейки, входящие в объект.  
  
 Например, объект тесселируется в 10 ячеек на 4 различных уровнях сетки, покрывая область, которая эквивалентна общему числу 100 конечных ячеек. Предположим, существует 3 внутренних ячейки, которые полностью входят в объект. Область, которая покрывается 3 внутренними ячейками, эквивалентна 42 конечным ячейкам. Таким образом, доля в процентах составляет 42 (процента). Это показатель того, насколько целесообразно распределены объекты в индексе.  
  
 Значение — **float**.  
  
 **Intersecting_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 То же, что **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**, за исключением того, что эти ячейки частично покрыты. Значение — **float**.  
  
 **Border_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 То же, что **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage** за исключением того, что это граничные ячейки. Значение — **float**.  
  
 **Average_Cells_Per_Object_Normalized_To_Leaf_Grid**  
 Среднее число ячеек на объект, нормализованных в сетке конечных ячеек. Это дает представление о пространственном размере объектов, то есть об их величине. Значение — **float**.  
  
 **Average_Objects_PerLeaf_GridCell**  
 Разреженность индекса. Среднее число объектов на конечную ячейку. Значение — **float**.  
  
 **Number_Of_SRIDs_Found**  
 Количество уникальных SRID в индексе и столбце. Значение — **int**.  
  
 Поскольку в столбце может содержаться более одного SRID и объекты различных SRID никогда не пересекаются, то количество SRID указывает на избирательность индекса.  
  
 **Width_Of_Cell_In_Level1**  
 Свойство ширины ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Width_Of_Cell_In_Level2**  
 Свойство ширины ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Width_Of_Cell_In_Level3**  
 Свойство ширины ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Width_Of_Cell_In_Level4**  
 Свойство ширины ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Height_Of_Cell_In_Level1**  
 Свойство высоты ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Height_Of_Cell_In_Level2**  
 Свойство высоты ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Height_Of_Cell_In_Level3**  
 Свойство высоты ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Height_Of_Cell_In_Level4**  
 Свойство высоты ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Area_Of_Cell_In_Level1**  
 Свойство площади ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Area_Of_Cell_In_Level2**  
 Свойство площади ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Area_Of_Cell_In_Level3**  
 Свойство площади ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **Area_Of_Cell_In_Level4**  
 Свойство площади ячейки в индексированной сетке. Единица измерения обеспечивается индексом и зависит от SRID индексированных данных. Значение — **float**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level1**  
 Процент покрытия ограничивающего прямоугольника в ячейке уровня 1. Значение — **float**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level2**  
 Процент покрытия ограничивающего прямоугольника в ячейке уровня 2. Значение — **float**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level3**  
 Процент покрытия ограничивающего прямоугольника в ячейке уровня 3. Значение — **float**.  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level4**  
 Доля покрытия в процентах ограничивающего прямоугольника ячейки уровня 4. Значение — **float**.  
  
 **Number_Of_Rows_Selected_By_Primary_Filter**  
 Количество строк, выбранных основным фильтром. Это свойство является основным. Значение — **bigint.**  
  
 **Number_Of_Rows_Selected_By_Internal_Filter**  
 Количество строк, выбранных внутренним фильтром. Фильтрация по дополнительному фильтру для этих строк не вызвана. Это свойство является основным. Значение — **bigint.**  
  
 Возвращенное число применимо только для **STintersects**.  
  
 **Number_Of_Times_Secondary_Filter_Is_Called**  
 Количество вызовов дополнительного фильтра. Это свойство является основным. Значение — **bigint.**  
  
 **Percentage_Of_Rows_NotSelected_By_Primary_Filter**  
 Если в базовой таблице содержится N строк, а основным фильтром выбрано P, то возвращается доля в процентах (N-P)/N. Это свойство является основным. Значение — **число с плавающей запятой.**  
  
 **Percentage_Of_Primary_Filter_Rows_Selected_By_internal_Filter**  
 Если основным фильтром выбрано P строк, а S строк выбрано внутренним фильтром, то возвращается доля в процентах S/P. Чем выше доля в процентах, тем выше уровень индекса в области избегания использования дополнительного фильтра, более требовательного к производительности. Это свойство является основным. Значение — **число с плавающей запятой.**  
  
 **Number_Of_Rows_Output**  
 Количество строк, выведенных при запросе. Это свойство является основным. Значение — **bigint.**  
  
 **Internal_Filter_Efficiency**  
 Если O представляет собой количество выведенных строк, то возвращается доля в процентах S/O. Это свойство является основным. Значение — **число с плавающей запятой.**  
  
 **Primary_Filter_Efficiency**  
 Если выбрано P строк, с основным фильтром и O — количество строк вывода, этот returnsO/P в процентах. Чем выше эффективность основного фильтра, тем меньше ложных положительных результатов необходимо обработать дополнительному фильтру. Это свойство является основным. Значение — **число с плавающей запятой.**  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен быть членом **открытый** роли. Необходимо разрешение READ ACCESS на сервере и объекте. Это относится ко всем хранимым процедурам пространственного индекса.  
  
## <a name="remarks"></a>Замечания  
 Свойства, которые содержат значения NULL, не включаются в набор возвращаемых значений.  
  
## <a name="examples"></a>Примеры  
 Примеры см. в следующих разделах:  
  
-   [sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [sp_help_spatial_geometry_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [sp_help_spatial_geography_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [sp_help_spatial_geography_index_xml &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры пространственного индекса &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)   
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Основы языка XQuery](../../xquery/xquery-basics.md)   
 [Справочник по языку XQuery (SQL Server)](../../xquery/xquery-language-reference-sql-server.md)  
  
  
