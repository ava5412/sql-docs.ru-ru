---
title: CollectionAggregate (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geography)
ms.assetid: e49a644a-dbf2-46c3-98f5-4b3ec197e2ad
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 269afe0ba9a5bb8a5bd625441ec8dc902ceadfb6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37980215"
---
# <a name="collectionaggregate-geography-data-type"></a>CollectionAggregate (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Создает экземпляр **GeometryCollection** из набора объектов **geography**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geography_operand*  
 Столбец типа **geography**, представляющий набор объектов **geography**, которые будут указаны в экземпляре **GeometryCollection**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
## <a name="exception"></a>Исключение  
 Вызывает исключение `FormatException` при наличии недопустимых входных значений. См. раздел [STIsValid (тип данных geography)](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)  
  
## <a name="remarks"></a>Remarks  
 Метод возвращает значение **NULL**, если входные данные пусты или содержат различные идентификаторы пространственных ссылок. См. раздел [Идентификаторы пространственных ссылок (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Метод не обрабатывает входные значения **NULL**.  
  
> [!NOTE]  
>  Метод возвращает значение **NULL**, если входными являются значения **NULL**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает экземпляр `GeometryCollection`, содержащий набор объектов **geography**.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::CollectionAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические географические методы](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
