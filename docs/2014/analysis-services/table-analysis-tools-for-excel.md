---
title: Средства анализа таблиц для Excel | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- getting started
ms.assetid: 6d9d1481-18e4-4108-9efa-68152b0940c9
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dde976376aa356a0b349e769821b0137eb0be29c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312344"
---
# <a name="table-analysis-tools-for-excel"></a>Средства анализа таблиц для Excel
  Средства интеллектуального анализа данных в **анализ** панель инструментов являются самым простым способом приступить к работе с интеллектуальным анализом данных. Каждое средство автоматически анализирует распределение и тип данных, а также задает параметры для получения допустимых результатов. Нет необходимости выбирать алгоритмы и настраивать сложные параметры.  
  
 ![DM](media/dm-tabletoolsanalyze.gif "DM")  
  
 **Анализ** ленты содержит следующие средства:  
  
 [Анализ ключевых факторов влияния &#40;средства анализа таблиц для Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Пользователь выбирает нужный столбец или выходное значение, а затем алгоритм анализирует все входные данные для определения факторов, которые имеют наибольшее влияние на целевой объект. Кроме того, можно создать отчет, который сравнивает любые два значения, чтобы увидеть, как изменяются основные факторы.  
  
 **Анализ ключевых факторов влияния** средстве используется алгоритм Байеса (Майкрософт).  
  
 [Поиск категорий &#40;средства анализа таблиц для Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
 Это средство позволяет добавить любой набор данных и применить кластеризацию, чтобы найти группы данных. Средство полезно для поиска подобия данных и создания групп для дальнейшего анализа.  
  
 **Поиск категорий** средстве используется алгоритм кластеризации (Майкрософт).  
  
 [Заполнение по примеру &#40;средства анализа таблиц для Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
 Это средство помогает добавить отсутствующие значения. Пользователь предоставляет несколько примеров отсутствующих значений, после чего средство формирует закономерности на основе всех данных в таблице, а затем рекомендует новые значения на основе закономерностей в данных.  
  
 **Заполнение по примеру** средстве используется алгоритм логистической регрессии (Майкрософт).  
  
 [Прогноз &#40;средства анализа таблиц для Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
 Это средство принимает данные, которые меняются с течением времени, и прогнозирует будущие значения.  
  
 **Прогноз** средство использует алгоритм временных рядов Майкрософт.  
  
 [Выделение исключений &#40;средства анализа таблиц для Excel&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
 Это средство анализирует закономерности в таблице данных и находит строки и значения, которые не относятся к закономерности. Затем можно просмотреть и исправить их и повторно применить модель или отметить значения для последующего анализа.  
  
 **Выделение исключений** средстве используется алгоритм кластеризации (Майкрософт).  
  
 [Сценарий поиска решения &#40;средства анализа таблиц для Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
 В **поиск решения** средства, можно указать целевое значение, оно определяет базовые факторы, которые необходимо изменить для соответствия цели. Например, если известно, что нужно увеличить уровень обслуживания входящих звонков на 20 %, можно настроить модель на прогнозирование факторов, изменение которых позволяет достигнуть этой цели.  
  
 **Поиск решения** средстве используется алгоритм логистической регрессии (Майкрософт).  
  
 [Что, если сценарий &#40;средства анализа таблиц для Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
 **Анализ гипотетических вариантов** средство дополняет **поиск решения** средство. Средство позволяет ввести значение, которое нужно изменить, а модель прогнозирует, будет ли это изменение достаточно для достижения желаемого результата. Например, можно попросить модель определить, увеличит ли добавление дополнительного оператора удовлетворенность заказчика на один пункт.  
  
 **Гипотетических** средстве используется алгоритм логистической регрессии (Майкрософт).  
  
 [Расчет прогноза &#40;средства анализа таблиц для Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Это средство создает модель, которая анализирует факторы, позволяющие получить целевой результат, а затем предсказывает результат для новых входных данных на основе правил оценки, полученных из данных. Это средство также создает интерактивный лист принятия решений, который позволяет легко оценивать новые входные данные. Также можно создать печатную версию листа оценки для автономного использования.  
  
 **Расчет прогноза** средстве используется алгоритм логистической регрессии (Майкрософт).  
  
 [Анализ покупательского поведения &#40;таблиц средства анализа для Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
 Это средство позволяет определять закономерности, которые можно использовать при осуществлении связанных или сопутствующих продаж. Оно определяет группы продуктов, часто приобретаемых вместе, а также создает отчеты на основе цен связанных продуктов для помощи в принятии решений.  
  
 Это средство не ограничивается анализом покупательского поведения. Его можно применить к любой задаче, которая поддается анализу взаимосвязей. Например, его также можно использовать для событий, которые часто возникают вместе, факторов, позволяющих поставить диагноз, или любого другого набора потенциальных причин и результатов.  
  
 **Анализа покупательского поведения** средстве используется алгоритм взаимосвязей (Майкрософт).  
  
## <a name="requirements-for-the-table-analysis-tools-for-excel"></a>Требования для средств анализа таблиц для Excel  
 Чтобы использовать средства анализа таблиц для Excel, необходимо создать соединение с экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Это соединение обеспечивает доступ к алгоритмам интеллектуального анализа данных Майкрософт, необходимым для анализа данных. Если у вас нет доступа к экземпляру, рекомендуется попросить администратора настроить экземпляр, который можно использовать для экспериментов с интеллектуальным анализом данных. Дополнительные сведения см. в разделе [подключение к данным источника &#40;клиент интеллектуального анализа данных для Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Для работы с данными с помощью средств анализа таблиц необходимо преобразовать диапазон этих данных в таблицы Excel.  
  
 Если вы не видите **анализ** ленты, попробуйте сначала щелкнуть внутри таблицы данных. Меню не открывается, пока не выбрана таблица данных.  
  
## <a name="see-also"></a>См. также  
 [Клиент интеллектуального анализа данных для Excel &#40;надстройки интеллектуального анализа данных SQL Server&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)   
 [Устранение неполадок с диаграммами интеллектуального анализа данных Visio &#40;надстройки интеллектуального анализа данных SQL Server&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)   
 [Состав надстройки интеллектуального анализа данных для Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  