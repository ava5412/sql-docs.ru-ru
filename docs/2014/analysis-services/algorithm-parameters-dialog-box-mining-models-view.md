---
title: Диалоговое окно Параметры алгоритма (представление моделей интеллектуального анализа данных) | Документация Майкрософт
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
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 491605a58b6a30f0f8b86afd0a2354e3c9b81ed9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178961"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a>Диалоговое окно «Параметры алгоритма» (представление моделей интеллектуального анализа данных)
  Используйте диалоговое окно **Параметры алгоритма** для регулировки параметров алгоритма, которые относятся к выбранной модели. При изменении параметра алгоритма обычно меняются результаты модели интеллектуального анализа. Способ, при котором каждый параметр влияет на результаты, зависит от данных используемого алгоритма. Дополнительные сведения см. в разделе [Настройка структуры и моделей интеллектуального анализа данных](data-mining/customize-mining-models-and-structure.md).  
  
## <a name="options"></a>Параметры  
 **Параметры**  
 Позволяет отобразить список параметров, доступных для выбранной модели интеллектуального анализа данных.  
  
 В следующем списке описываются доступные столбцы.  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Параметр**|Выведите список имен параметров.|  
|**Value**|Вводите значение только в том случае, если необходимо изменить значение параметра по умолчанию.|  
|**Default**|Выведите список значений по умолчанию для параметра, который будет использован в алгоритме, если не нужно вводить значение в столбец **Значение** .|  
|**Диапазон**|Выведите список диапазонов возможных значений, которые можно ввести в столбец **Значение** . Диапазоны может принимать одно из следующих:<br /><br /> Дискретный список, например 1, 2, 3<br /><br /> Включающий диапазон, такие как [0, 100]<br /><br /> Исключающий диапазон, например (0,...)<br /><br /> Комбинацию, например [0,...)|  
  
 **Описание**  
 Позволяет описать параметр, выбранный в списке **Параметры** .  
  
 **Добавить**  
 Нажмите, чтобы добавить в список дополнительные параметры, относящиеся к алгоритму. После добавления параметра можно ввести правильное имя в столбец **Параметр** и ввести значение в столбец **Значение** .  
  
 **Удалить**  
 Нажмите, чтобы удалить пользовательский параметр из списка.  
  
 Если удалить из списка один из параметров стандартного алгоритма служб Analysis Services, то он по-прежнему будет использоваться в модели, но со значением по умолчанию. Параметр не удаляется окончательно и появится при следующем открытии диалогового окна.  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Представление моделей интеллектуального &#40;конструктор моделей интеллектуального анализа данных&#41;](mining-models-view-data-mining-model-designer.md)   
 [Перемещение объектов интеллектуального анализа данных](data-mining/moving-data-mining-objects.md)  
  
  