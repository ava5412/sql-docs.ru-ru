---
title: Создать псевдоним для столбца модели | Документация Майкрософт
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
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: db477052fb30a9759ad61df1ff42652fe9ed594a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228264"
---
# <a name="create-an-alias-for-a-model-column"></a>создать псевдоним для столбца модели
  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]для столбца модели можно создать псевдоним. Необходимость в этом может возникнуть, если имя структуры интеллектуального анализа данных имеет слишком большую длину и с ним неудобно работать, или если необходимо присвоить столбцу другое имя, более точно описывающее его содержимое или назначение в модели. Например, если создается копия столбца структуры, а затем дискретизация столбца выполняется различно для конкретной модели, можно переименовать столбец, чтобы его имя более точно отражало его содержимое.  
  
 Чтобы создать псевдоним для столбца модели, можно воспользоваться панелью **Свойства** и задать свойство [Name](../scripting/properties/name-element-assl.md) столбца.  
  
 На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных псевдоним отображается в круглых скобках рядом с меткой использования столбца.  
  
 Дополнительные сведения о задании свойств в модели интеллектуального анализа данных см. в разделе [Столбцы модели интеллектуального анализа данных](mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Добавление псевдонима к столбцу модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** конструктора моделей интеллектуального анализа данных щелкните правой кнопкой мыши ячейку в модели интеллектуального анализа данных для столбца интеллектуального анализа, которую необходимо изменить, и выберите пункт **Свойства**.  
  
2.  В окне **Свойства** в правой части экрана щелкните ячейку рядом со свойством Name и удалите текущее значение. Введите новое имя столбца.  
  
## <a name="see-also"></a>См. также  
 [Задачи модели интеллектуального анализа данных и инструкции по](mining-model-tasks-and-how-tos.md)   
 [Свойства модели интеллектуального анализа данных](mining-model-properties.md)  
  
  
