---
title: Реализация сжатия Юникода | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 216e2278418747a713575c165f14390c7b785e71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37156341"
---
# <a name="unicode-compression-implementation"></a>Реализация сжатия Юникода
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует алгоритм стандартной схемы сжатия Юникода (SCSU), при этом сохраняются данные в сжатых объектах строк или страниц. Для этих объектов сжатие Юникода для столбцов типов `nchar(n)` и `nvarchar(n)` выполняется автоматически. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] хранит данные Юникода как 2 байта, независимо от локали. Такая кодировка называется UCS-2. Для некоторых локалей реализация сжатия по алгоритму SCSU в SQL Server может сэкономить до 50 % места в хранилище.  
  
## <a name="supported-data-types"></a>Поддерживаемые типы данных  
 Сжатие Юникода поддерживает типы данных фиксированной длины `nchar(n)` и `nvarchar(n)`. Внестрочные значения данных и значения, хранящиеся в столбцах `nvarchar(max)`, не сжимаются.  
  
> [!NOTE]  
>  Сжатие Юникода не поддерживается для `nvarchar(max)` даже в том случае, если они хранятся в строке данных. Однако сжатие страниц может быть полезно для этого типа данных.  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a>Обновление с предыдущих версий SQL Server  
 При обновлении базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]все изменения, связанные со сжатием Юникода, не оказывают влияния на объекты базы данных, сжатые или распакованные. После обновления базы данных ситуация с объектами выглядит следующим образом.  
  
-   Если объект не сжат, то никаких изменений не происходит и объект продолжает работать как раньше.  
  
-   Сжатые объекты строк и страниц продолжают работу как раньше. Распакованные данные остаются в распакованной форме до тех пор, пока их значение не будет обновлено.  
  
-   Для новых строк, вставляемых в таблицу, сжатую на уровне строк или страниц, производится сжатие Юникода.  
  
    > [!NOTE]  
    >  Для использования всех преимуществ сжатия Юникода объект необходимо перестроить с использованием сжатия страниц или строк.  
  
## <a name="how-unicode-compression-affects-data-storage"></a>Влияние сжатия Юникода на хранилище данных  
 При создании или перестройке индекса, а также при изменении значения в таблице, сжатой на уровне строк или страниц, соответствующий индекс или значение сохраняется в сжатом виде только в том случае, если его размер в сжатом виде будет меньше текущего. Сжатие Юникода позволяет предотвратить разрастание размера строк в таблице или индексе.  
  
 Объем места в хранилище, сэкономленного благодаря сжатию, зависит от характеристик сжимаемых данных и локали данных. Следующая таблица содержит данные по экономии, достижимой для некоторых локалей.  
  
|Локаль|Процент сжатия|  
|------------|-------------------------|  
|Английский|50%|  
|German|50%|  
|Hindi|50%|  
|Турецкий|48 %|  
|Вьетнамский|39 %|  
|Японский|15 %|  
  
## <a name="see-also"></a>См. также  
 [Сжатие данных](data-compression.md)   
 [sp_estimate_data_compression_savings (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql)   
 [Реализация сжатия страниц](page-compression-implementation.md)   
 [sys.dm_db_persisted_sku_features (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql)  
  
  
