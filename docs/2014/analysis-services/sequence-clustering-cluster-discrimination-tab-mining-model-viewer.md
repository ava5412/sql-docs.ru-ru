---
title: Вкладка «сравнения кластеров» (средство просмотра моделей интеллектуального анализа данных) кластеризации последовательностей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.discrimination.f1
ms.assetid: 7dd16479-2633-4f4b-83bf-cf55972a2241
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d4debc43286ffb3fe4f87115ed15e9b4c3f74b06
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187151"
---
# <a name="sequence-clustering-cluster-discrimination-tab-mining-model-viewer"></a>Вкладка «Сравнение кластеров при кластеризации последовательностей» (средство просмотра моделей интеллектуального анализа данных)
  Вкладка  **Сравнения кластеров** в **средстве просмотра кластеризации последовательностей (Майкрософт)** сравнивает выбранные кластеры из модели кластеризации последовательностей.  
  
 Используйте представление модели кластеризации последовательностей, чтобы сравнить два кластера и обнаружить различающиеся состояния и переходы.  
  
 **Дополнительные сведения:** [Алгоритм кластеризации последовательностей (Майкрософт)](data-mining/microsoft-sequence-clustering-algorithm.md), [Просмотр модели с помощью средства просмотра кластеризации последовательностей (Майкрософт)](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Параметры  
 **Обновить содержимое средства просмотра**  
 Перезагрузить модель интеллектуального анализа данных в средстве просмотра.  
  
 **Модель интеллектуального анализа данных**  
 Выберите для просмотра модель интеллектуального анализа данных, содержащуюся в текущей структуре интеллектуального анализа данных. Модель интеллектуального анализа данных открывается в связанном средстве просмотра.  
  
 **Средство просмотра**  
 Выберите средство просмотра для обзора выбранной модели интеллектуального анализа данных. Можно использовать пользовательское средство просмотра или **средство просмотра деревьев содержимого общего вида (Майкрософт)**. Также можно использовать подключаемые модули просмотра, если они доступны.  
  
 **Кластер 1**  
 Выберите кластер из имеющихся в модели.  
  
 **Кластер 2**  
 Выберите второй кластер в модели интеллектуального анализа данных для сравнения с **Кластером 1**.  
  
 Если не выбран другой кластер, выбранный кластер по умолчанию сравнивается с его дополнением, то есть всеми вариантами в модели, не входящими в кластер 1.  
  
 **Коэффициенты сравнения для \<кластера 1 > и \<кластера 2 >**  
 Эта диаграмма содержит подробное сравнение выбранных кластеров. В целом модель кластеризации редко назначает состояния или значения исключительно одному кластеру. Поэтому средство просмотра указывает только, что определенный атрибут или состояние *подходит* к конкретному кластеру.  
  
 В общем, определенный кластер может содержать более одного состояния, например типовым состоянием может быть последовательная покупка Water Bottle и Water Bottle Cage. Однако эта последовательность может присутствовать в других кластерах, которые имеют более важные определяющие характеристики. Например, основной характеристикой другого кластера может быть очень короткое время транзакций, и в результате анализа выяснится, что элементы Water Bottle и Water Botlle Cage обычно могут быть сгруппированы в этом кластере, но не всегда.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Переменные**|Атрибут модели интеллектуального анализа данных.|  
|**Значения**|Состояние атрибута, включенного в список **Переменные**.|  
|**Подходит к \<кластера 1 >**|Содержит полосу с заливкой, обозначающую, насколько близко атрибут и состояние, указанные в полях **Переменные** и **Значение** , подходят кластеру, выбранному в **кластере 1**.|  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Просмотра моделей интеллектуального анализа &#40;конструктор моделей интеллектуального анализа данных&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Средства просмотра моделей интеллектуального анализа данных](data-mining/data-mining-model-viewers.md)  
  
  
