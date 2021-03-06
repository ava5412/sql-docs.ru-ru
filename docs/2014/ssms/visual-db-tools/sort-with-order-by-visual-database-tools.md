---
title: Сортировка с помощью предложения ORDER BY (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c8ad8958c102821c123a15217faea03478f6f4a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268060"
---
# <a name="sort-with-order-by-visual-database-tools"></a>Произведение сортировки с помощью предложения ORDER BY (визуальные инструменты для баз данных)
  Предложение ORDER BY позволяет сортировать результаты запроса по одному или нескольким столбцам. Его можно определить, выбрав параметры на панели «Подробности критериев».  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>Для сортировки результатов запроса с помощью предложения ORDER BY:  
  
1.  Откройте запрос или создайте новый.  
  
2.  На [панели критериев](visual-database-tools.md)щелкните в столбце **Тип сортировки** строку, соответствующую столбцу, по которому нужно отсортировать результаты запроса.  
  
3.  В раскрывающемся списке выберите *По возрастанию* или *По убыванию* .  
  
> [!NOTE]  
>  Очистка элемента **Тип сортировки** для столбца удаляет этот столбец из предложения ORDER BY.  
  
 Обратите внимание, что во время работы с панелью критериев предложение UNION запроса изменяется в соответствии с последними действиями.  
  
> [!NOTE]  
>  При сортировке результатов по нескольким столбцам в столбце **Порядок сортировки** укажите порядок, в котором будут просматриваться столбцы при сортировке. Дополнительные сведения см. в разделе **Как производить сортировку нескольких столбцов в запросе**.  
  
## <a name="see-also"></a>См. также  
 [Результаты запросов сортировки и группирования &#40;визуальных инструментах баз данных&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Резюмирование результатов запросов &#40;визуальных инструментах баз данных&#41;](summarize-query-results-visual-database-tools.md)   
 [Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
