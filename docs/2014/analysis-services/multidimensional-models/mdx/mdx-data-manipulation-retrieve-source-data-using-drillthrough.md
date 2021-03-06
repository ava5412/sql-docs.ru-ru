---
title: С помощью функции DRILLTHROUGH извлечение данных из источника (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8b98ebd1516d2aa26fa1e3a66edebdaf99f0f181
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204424"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a>Извлечение данных из источника с помощью функции DRILLTHROUGH (многомерные выражения)
  В языке многомерных выражений для извлечения набора строк из источника данных для ячейки куба используется инструкция [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough).  
  
 Чтобы в кубе можно было выполнять инструкцию `DRILLTHROUGH`, для него следует определить действие детализации. Чтобы определить действие детализации, в конструкторе кубов в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]на панели **Действия** выберите на панели инструментов пункт **Создать действие детализации**. Для действия детализации укажите имя, цель и условие действия, а также столбцы, возвращаемые инструкцией `DRILLTHROUGH`.  
  
## <a name="drillthrough-statement-syntax"></a>Синтаксис инструкции DRILLTHROUGH  
 `DRILLTHROUGH` Инструкция использует следующий синтаксис:  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 `SELECT` Предложение определяет ячейку куба, содержащую исходные данные должны быть получены. Это предложение `SELECT` эквивалентно обычной инструкции многомерных выражений `SELECT`, за исключением того, что в предложении `SELECT` на каждой оси можно указывать только один элемент. Если на оси указано несколько элементов, возникает ошибка.  
  
 Синтаксическая конструкция `<Max_Rows>` задает максимальное количество строк в каждом возвращаемом наборе строк. Если поставщик OLE DB, используемый для соединения с источником данных, не поддерживает параметр `DBPROP_MAXROWS`, аргумент `<Max_Rows>` не учитывается.  
  
 Синтаксическая конструкция `<First_Rowset>` определяет секцию, набор строк которой возвращается первым.  
  
 Синтаксическая конструкция `<Return_Columns>` определяет возвращаемые столбцы базовой базы данных.  
  
## <a name="drillthrough-statement-example"></a>Пример инструкции DRILLTHROUGH  
 В следующем примере показано использование `DRILLTHROUGH` инструкции. В этом примере инструкция DRILLTHROUGH обращается с запросом к концевым элементам измерений Store, Product и Time вдоль измерения Stores (ось среза) и возвращает группу мер Department, идентификатор отдела и имя сотрудника.  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a>См. также  
 [Обработка данных &#40;многомерных Выражений&#41;](mdx-data-manipulation-manipulating-data.md)  
  
  
