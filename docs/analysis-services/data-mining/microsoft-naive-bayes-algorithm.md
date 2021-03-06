---
title: Алгоритма Байеса (Майкрософт) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b3cbe50437011bc97ba4f4e1e246ee85e89495c1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34017241"
---
# <a name="microsoft-naive-bayes-algorithm"></a>Упрощенный алгоритм Байеса (Майкрософт)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Упрощенный алгоритм Байеса ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) — это алгоритм классификации, основанный на теоремах Байеса, который можно использовать как для изучения данных, так и для прогнозного моделирования. Слово «упрощенный» в его названии указывает на то, что алгоритм использует методы Байеса, но не учитывает возможные зависимости.  
  
 Данный алгоритм требует меньшего количества вычислений, чем другие алгоритмы [!INCLUDE[msCoName](../../includes/msconame-md.md)] , и может применяться для быстрого формирования моделей интеллектуального анализа данных для обнаружения отношений между входными и прогнозируемыми столбцами. Этот алгоритм можно использовать для первоначального исследования данных, а затем применить результаты для создания дополнительных моделей интеллектуального анализа с другими алгоритмами, требующими большего количества вычислений и являющимися более точными.  
  
## <a name="example"></a>Пример  
 В рамках постоянной стратегии продвижения отдел маркетинга компании Adventure Works Cycle решил разослать листовки потенциальным клиентам. Чтобы снизить себестоимость, было принято решение рассылать листовки только тем клиентам, которые, вероятно, ответят. Компания хранит в базе данных демографические данные и сведения об ответах на предыдущие рассылки. Необходимо использовать эти данные для определения возможности применения таких демографических показателей, как возраст и место проживания, для прогнозирования ответа на рекламную кампанию путем сравнения потенциальных клиентов с клиентами, которые обладают подобными характеристиками и которые осуществляли покупки в компании в прошлом. Необходимо определить различия между теми клиентами, которые купили велосипед, и теми, которые не купили.  
  
 Используя упрощенный алгоритм Байеса [!INCLUDE[msCoName](../../includes/msconame-md.md)] , отдел маркетинга может быстро спрогнозировать результат для конкретного профиля клиентов и определить, какие клиенты с наибольшей вероятностью ответят на листовки. Используя средство просмотра упрощенного алгоритма Байеса [!INCLUDE[msCoName](../../includes/msconame-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], они могут визуально исследовать, какие конкретные входные столбцы способствуют положительному ответу на листовки.  
  
## <a name="how-the-algorithm-works"></a>Принцип работы алгоритма  
 Упрощенный алгоритм Байеса [!INCLUDE[msCoName](../../includes/msconame-md.md)] рассчитывает вероятность состояния каждого входного столбца при каждом возможном состоянии прогнозируемого столбца.  
  
 Разобраться в работе этого метода можно с помощью средства просмотра упрощенного алгоритма Байеса ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] (см. рисунок). Оно позволяет в наглядном режиме исследовать, как происходит распределение состояний в рамках этого алгоритма.  
  
 ![Упрощенный алгоритм Байеса распределения состояний](../../analysis-services/data-mining/media/naive-bayes.gif "упрощенного алгоритма Байеса распределения состояний")  
  
 Здесь средство просмотра упрощенного алгоритма Байеса [!INCLUDE[msCoName](../../includes/msconame-md.md)] содержит список всех входных столбцов в наборе данных и показывает, как распределяются состояния каждого из столбцов при каждом из состояний прогнозируемого столбца.  
  
 С помощью этого представления модели можно определить входные столбцы, которые важны для разграничения состояний прогнозируемого столбца.  
  
 Например, в строке для поля Commute Distance, как показано здесь, распределение входных значений наглядно отличается для покупателей и тех, кто не покупает. Показанные данные указывают на то, что входное значение Commute Distance = 0-1,6 км потенциально имеет влияние на результат прогноза.  
  
 Средство просмотра также отображает значения для отдельных классов продуктов таким образом, что можно увидеть, что для клиентов, которые преодолевают расстояние от 1 до 3,3 километра от дома до рабочего места, вероятность приобретения велосипеда составляет 0,387, а вероятность его неприобретения — 0,287. В данном примере для прогнозирования вероятности покупки велосипеда алгоритм использует числовые данные, полученные из характеристик клиентов, например расстояния до работы.  
  
 Дополнительные сведения об использовании средства просмотра упрощенного алгоритма Байеса ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ) см. в статье [Просмотр модели с помощью средства просмотра упрощенного алгоритма Байеса (Майкрософт)](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md).  
  
## <a name="data-required-for-naive-bayes-models"></a>Данные, необходимые для моделей упрощенного алгоритма Байеса  
 При подготовке данных, предназначенных для использования в обучении модели упрощенного алгоритма Байеса, следует учитывать требования алгоритма, в том числе необходимый объем данных и способ их использования.  
  
 Далее приводятся требования для модели упрощенного алгоритма Байеса.  
  
-   **Единичный ключевой столбец** Каждая модель должна содержать один числовой или текстовый столбец, который уникальным образом определяет каждую запись. Применение составных ключей не допускается.  
  
-   **Входные столбцы**. В модели упрощенного алгоритма Байеса все столбцы должны быть дискретными или иметь сегментированные значения. Сведения о дискретизации (сегментировании) столбцов см. в разделе [Методы дискретизации (интеллектуальный анализ данных)](../../analysis-services/data-mining/discretization-methods-data-mining.md).  
  
-   **Переменные должны быть независимыми.** Для модели упрощенного алгоритма Байеса также важно обеспечить независимость входных атрибутов друг от друга. Это особенно важно, когда модель используется для прогнозирования. Если использовать два столбца данных, которые тесно связаны между собой, то это приведет к умножению значений этих столбцов, что может затруднить интерпретацию других факторов, влияющих на результат.  
  
     Напротив, возможность алгоритма определять связи между переменными полезна при исследовании модели или набора данных для обнаружения связей между входными данными.  
  
-   **По крайней мере один прогнозируемый столбец** Прогнозируемый атрибут должен содержать дискретные или дискретизированные значения.  
  
     Значения в прогнозируемом столбце могут рассматриваться как входные. Такая практика может оказаться полезной при исследовании нового набора данных для обнаружения связей между столбцами.  
  
## <a name="viewing-the-model"></a>Просмотр модели  
 Для просмотра модели используется **средство просмотра упрощенного алгоритма Байеса (Майкрософт)**. Средство просмотра показывает, как входные атрибуты связаны с прогнозируемым атрибутом. Также приводится подробный профиль каждого кластера, список атрибутов, отличающих кластер от остальных, и характеристики всего набора данных для обучения. Дополнительные сведения см. в разделе [Просмотр модели с помощью средства просмотра упрощенного алгоритма Байеса (Майкрософт)](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md).  
  
 Чтобы получить более подробные сведения, можно просмотреть модель с помощью [средства просмотра деревьев содержимого общего вида (Майкрософт) (интеллектуальный анализ данных)](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c). Дополнительные сведения о типе данных, хранимых в модели, см. в разделе [Содержимое моделей интеллектуального анализа данных для моделей упрощенного алгоритма Байеса (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md).  
  
## <a name="making-predictions"></a>Составление прогнозов  
 После обучения модели результаты хранятся в виде набора закономерностей, которые можно исследовать или делать на их основе прогнозы.  
  
 Можно создавать запросы, возвращающие прогнозы о связи новых данных с прогнозируемым атрибутом, или получать статистику, описывающую взаимосвязи, обнаруженные моделью.  
  
 Дополнительные сведения о создании запросов к модели интеллектуального анализа данных см. в разделе [Запросы интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-queries.md). Примеры использования запросов с моделью упрощенного алгоритма Байеса см. в разделе [Примеры запросов к модели упрощенного алгоритма Байеса](../../analysis-services/data-mining/naive-bayes-model-query-examples.md).  
  
## <a name="remarks"></a>Замечания  
  
-   Поддерживается использование языка разметки прогнозирующих моделей (PMML) для создания моделей интеллектуального анализа данных.  
  
-   Поддерживается детализация.  
  
-   Не поддерживается создание измерений интеллектуального анализа данных.  
  
-   Поддерживается использование моделей интеллектуального анализа OLAP.  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных & #40; Службы Analysis Services — Интеллектуальный анализ данных & #41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Выбор компонентов & #40; интеллектуального анализа данных & #41;](../../analysis-services/data-mining/feature-selection-data-mining.md)   
 [Примеры запросов к модели упрощенного алгоритма Байеса](../../analysis-services/data-mining/naive-bayes-model-query-examples.md)   
 [Содержимое модели интеллектуального анализа данных для моделей упрощенного алгоритма Байеса & #40; Службы Analysis Services — Интеллектуальный анализ данных & #41;](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)   
 [Технический справочник Майкрософт упрощенный алгоритм Байеса](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
  
