---
title: sys.syscolumns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-enginel, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.syscolumns
- sys.syscolumns_TSQL
- syscolumns_TSQL
- syscolumns
dev_langs:
- TSQL
helpviewer_keywords:
- syscolumns system table
- sys.syscolumns compatibility view
ms.assetid: 863fd87b-ff33-4ac5-9aa9-df21140681da
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: ed20abe081acad3ef1c653f3041006c6453e4607
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39540644"
---
# <a name="syssyscolumns-transact-sql"></a>sys.syscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Возвращает по одной строке на каждый из столбцов всех таблиц и представлений и по одной строке на каждый из параметров хранимых процедур в базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя столбца или параметра процедуры.|  
|**идентификатор**|**int**|Идентификатор объекта таблицы, которому принадлежит столбец, или идентификатор хранимой процедуры, с которой связан данный параметр.|  
|**xtype**|**tinyint**|Тип физического хранилища из **sys.types**.|  
|**typestat**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|Идентификатор расширенного пользовательского типа. Вызывает переполнение или возвращает значение NULL, если количество типов данных превышает 32 767.|  
|**Длина**|**smallint**|Максимальная длина физического хранилища из **sys**. **типы**.|  
|**xprec**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**XScale**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**идентификатора столбца**|**smallint**|Идентификатор столбца или параметра.|  
|**xoffset**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Зарезервировано**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|Идентификатор значения по умолчанию для данного столбца.|  
|**Домен**|**int**|Идентификатор правила или ограничения CHECK для данного столбца.|  
|**номер**|**smallint**|Номер подпроцедуры, если процедура сгруппирована:<br /><br /> 0 = Непроцедурные элементы.|  
|**colorder**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**varbinary(8000)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**smallint**|Смещение в строке, по которому находится данный столбец.|  
|**collationid**|**int**|Идентификатор параметров сортировки для столбца. Для несимвольных столбцов содержит значение NULL.|  
|**status**|**tinyint**|Битовая карта, описывающая свойства столбца или параметра:<br /><br /> 0x08 = В столбце допускаются значения NULL;<br /><br /> 0x10 = заполнение символами ANSI был в силу, если **varchar** или **varbinary** были добавлены столбцы. Замыкающие пробелы сохраняются для **varchar** и замыкающие нули сохраняются для **varbinary** столбцов.<br /><br /> 0x40 = Параметр OUTPUT;<br /><br /> 0x80 = Столбец является столбцом идентификаторов.|  
|**type**|**tinyint**|Тип физического хранилища из **sys**. **типы**.|  
|**usertype**|**smallint**|Идентификатор определяемого пользователем типа из **sys.types**. Вызывает переполнение или возвращает значение NULL, если количество типов данных превышает 32 767.|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|Уровень точности для данного столбца:<br /><br /> -1 = **xml** или тип больших значений.|  
|**Масштаб**|**int**|Масштаб для данного столбца.<br /><br /> NULL = данные не числовые.|  
|**iscomputed**|**int**|Флаг, обозначающий, является ли столбец вычисляемым:<br /><br /> 0 = невычисляемый;<br /><br /> 1 = вычисляемый.|  
|**isoutparam**|**int**|Указывает, относится ли параметр процедуры к выходным параметрам:<br /><br /> 1 = True<br /><br /> 0 = False.|  
|**IsNullable**|**int**|Указывает, допускает ли столбец значения NULL:<br /><br /> 1 = True<br /><br /> 0 = False.|  
|**Параметры сортировки**|**sysname**|Имя параметров сортировки для данного столбца. Содержит NULL, если столбец не относится к символьному типу.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
