---
title: Изменение свойств модели интеллектуального анализа данных | Документация Майкрософт
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
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ed77c0d87fc6fb62497cc68c52dd3fabeb50d2ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279819"
---
# <a name="change-the-properties-of-a-mining-model"></a>Изменение свойств модели интеллектуального анализа данных
  Некоторые свойства моделей интеллектуального анализа данных могут применяться ко всей модели, другие действуют только на отдельные столбцы. Примеры свойств, которые применяются ко всей модели `Drillthrough` свойство, которое указывает, должны ли быть доступны для запросов данных варианта, и `Description` свойство. Свойства, действующие только на определенные столбцы: `Usage` и `ModelingFlags`, управляющие использованием данных в столбце внутри модели.  
  
 Для следующих свойств модели предусмотрены расширенные редакторы, с помощью которых можно создавать выражения или настраивать сложные свойства моделей. Следующие свойства предоставляют:  
  
-   `Filter` свойство: открывает [фильтр набора данных или диалоговое окно Фильтр модели](../data-set-filter-or-model-filter-dialog-box.md).  
  
-   `AlgorithmParameters` свойство: открывает [диалоговое окно «Параметры алгоритма» &#40;представление моделей интеллектуального анализа данных&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).  
  
 Дополнительные сведения о задании свойств в модели интеллектуального анализа данных см. в разделе [Столбцы модели интеллектуального анализа данных](mining-model-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>Изменение свойств модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** в конструкторе интеллектуального анализа данных щелкните правой кнопкой мыши либо заголовок столбца, содержащего имя модели интеллектуального анализа данных, либо строку, содержащую имя алгоритма. Потом выберите **Свойства**.  
  
2.  В окне **Свойства** в правой части экрана выделите значение, соответствующее свойству, которое необходимо изменить, и введите новое значение.  
  
     Новое значение вступает в силу после выбора другого элемента в конструкторе.  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>Изменение свойств столбца модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных щелкните правой кнопкой мыши ячейку на пересечении модели интеллектуального анализа данных и столбца структуры интеллектуального анализа данных, которую нужно изменить, и выберите пункт **Свойства**.  
  
2.  В окне **Свойства** в правой части экрана выделите значение, соответствующее свойству, которое необходимо изменить, и введите новое значение.  
  
    > [!NOTE]  
    >  Если использование столбца установлено в значение `Ignore`, **свойства** пустое окно для столбца.  
  
     Новое значение вступает в силу после выбора другого элемента в конструкторе.  
  
## <a name="see-also"></a>См. также  
 [Задачи и инструкции по модели интеллектуального анализа данных](mining-model-tasks-and-how-tos.md)  
  
  