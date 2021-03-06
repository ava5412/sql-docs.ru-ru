---
title: Меры в отчете перекрестной проверки | Документация Майкрософт
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
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7d45c1ff8501dff8c74de22a16ac47b69c5375a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304646"
---
# <a name="measures-in-the-cross-validation-report"></a>Меры в отчете перекрестной проверки
  В процессе перекрестной проверки службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] разбивают данные в структуре интеллектуального анализа данных на несколько перекрестных разделов, после чего выполняется итерационное тестирование структур и всех соответствующих моделей интеллектуального анализа данных. На основании такого анализа для структуры и каждой модели выводится набор стандартных точных мер.  
  
 Отчет содержит общие сведения о количестве сверток в данных, сумму данных в каждой свертке и набор общих показателей, описывающих распределение данных. Сравнивая общие показатели, созданные для каждого разреза, можно оценить надежность структуры или модели.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] также отображают набор подробных мер для модели интеллектуального анализа данных. Такие меры зависят от типа модели и типа анализируемого атрибута, например дискретный или непрерывный.  
  
 В данном разделе предоставляется список мер, которые содержатся в отчете **Перекрестная проверка** , и разъяснения к ним. Дополнительные сведения о том, как вычисляется каждая мера, см. в разделе [Формулы перекрестной проверки](cross-validation-formulas.md).  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a>Перечень мер в отчете перекрестной проверки  
 В следующей таблице перечислены меры, используемые в отчете перекрестной проверки. Меры группируются с помощью *типа проверки*, который находится в левой столбце следующей таблицы. В правом столбце перечислены наименования мер в порядке, в котором они появляются в отчете, и краткое разъяснение к ним.  
  
|типа проверки|Меры и описания|  
|---------------|-------------------------------|  
|Кластеризация|Меры, применяемые к моделям кластеризации:<br /><br /> **Вероятность случая**: Эта мера обычно указывает на вероятность принадлежности варианта определенному кластеру. <br />                      Для перекрестной проверки оценки суммируются и затем делятся на количество вариантов, таким образом получается среднее правдоподобие кластерного варианта.|  
|Классификация|Меры, применяемые к моделям классификации:<br /><br /> **Истинный положительный результат**/<br />                      **Истинный отрицательный**/ **False положительное**/ **False положительное**: количество строк или значений в секции, в которой прогнозируемое состояние совпадает с целевым, и вероятность прогноза превышает указанное пороговое значение. Исключаются случаи с отсутствующими значениями целевого атрибута, то есть все значения могут учитываться не|  
||**Совпадение или неудача**: число строк или значений в секции, которой прогнозируемое состояние совпадает с целевым, а значение вероятности прогноза больше 0.|  
|Вероятность|Меры правдоподобия применяются к нескольким типов моделей:<br /><br /> **Поднимите**: отношение фактической вероятности прогноза к граничной вероятности в проверочных вариантах. Исключаются строки с отсутствующими значениями целевого атрибута. Данная мера обычно показывает степень улучшения вероятности конечного результата при использовании модели.<br /><br /> **Корень Среднеквадратичной погрешности**: квадратного корня из средней погрешности для всех вариантов секций, деленное на число вариантов в секции, исключая строки с отсутствующими значениями целевого атрибута. Корень среднеквадратичной погрешности является общепринятой оценкой для моделей прогнозирования. Оценка усредняет остатки для каждого варианта, чтобы выработать единственный индикатор погрешности модели.<br /><br /> **Логарифмическая Оценка**: логарифмов фактической вероятности для каждого варианта, суммируются и затем делятся по числу строк во входном наборе данных, исключая строки с отсутствующими значениями целевого атрибута. Поскольку вероятность выражается десятичной дробью, логарифмическая оценка всегда отрицательные. Чем ближе число к 0, тем выше оценка. Тогда как необработанные оценки могут содержать очень нерегулярные и асимметричные распределения, логарифмическая оценка подобна процентной доле.|  
|Оценка|Меры, применяемые только к моделям оценки, прогнозирующим непрерывный числовой атрибут:<br /><br /> **Корень Среднеквадратичной погрешности**: средняя погрешность при сравнении спрогнозированного значения с фактическим значением. Корень среднеквадратичной погрешности является общепринятой оценкой для моделей прогнозирования. Оценка усредняет остатки для каждого варианта, чтобы выработать единственный индикатор погрешности модели.<br /><br /> **Средняя абсолютная погрешность**: средняя погрешность при сравнении с прогнозируемыми значениями фактические значения, вычисляется как среднее значение абсолютной суммы ошибок. Средняя абсолютная погрешность помогает понять, насколько сделанные прогнозы приближены к настоящим значениям. Меньшая оценка означает, что прогнозы были более точными.<br /><br /> **Логарифмическая Оценка**: логарифмов фактической вероятности для каждого варианта, суммируются и затем делятся по числу строк во входном наборе данных, исключая строки с отсутствующими значениями целевого атрибута. Поскольку вероятность выражается десятичной дробью, логарифмическая оценка всегда отрицательные. Чем ближе число к 0, тем выше оценка. Тогда как необработанные оценки могут содержать очень нерегулярные и асимметричные распределения, логарифмическая оценка подобна процентной доле.|  
|Статистические вычисления|Агрегатные меры отображают дисперсию в результатах для каждой секции:<br /><br /> **Означает**: среднее значение секции значения по конкретным мерам.<br /><br /> **Стандартное отклонение**: среднее отклонение от среднего арифметического для конкретной меры с учетом всех секций в модели. Для перекрестной проверки более высокое значение этой оценки предполагает существенные различия между свертками.|  
  
## <a name="see-also"></a>См. также  
 [Тестирование и проверка &#40;интеллектуального анализа данных&#41;](testing-and-validation-data-mining.md)  
  
  
