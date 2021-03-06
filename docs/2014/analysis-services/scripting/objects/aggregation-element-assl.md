---
title: Элемент Aggregation (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Aggregation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aggregation
helpviewer_keywords:
- Aggregation element
ms.assetid: f37af388-b2b3-4234-a1d6-936ee9b7f2ae
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 51e28a8435b2891cf623ea851824809606d83620
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157195"
---
# <a name="aggregation-element-assl"></a>Элемент Aggregation (ASSL)
  Определяет один агрегат для [секции](partition-element-assl.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Aggregations>  
      <Aggregation>  
      <ID>...</ID>  
      <Name>...</Name>  
      <Dimensions>...</Dimensions>  
            <Annotations>...</Annotations>  
      <Description>...</Description>  
   </Aggregation>  
</Aggregations>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Агрегаты](../collections/aggregations-element-assl.md)|  
|Дочерние элементы|[Заметки](../collections/annotations-element-assl.md), [описание](../properties/description-element-assl.md), [измерения](../collections/dimensions-element-assl.md), [идентификатор](../properties/id-element-assl.md), [имя](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Соответствующий элемент в модели объектов объекты управления Analysis AMO — это <xref:Microsoft.AnalysisServices.Aggregation>.  
  
## <a name="see-also"></a>См. также  
 [Секции элемент &#40;ASSL&#41;](partition-element-assl.md)   
 [Элемент AggregationDesign &#40;ASSL&#41;](aggregationdesign-element-assl.md)   
 [Элемент MeasureGroup &#40;ASSL&#41;](group-element-assl.md)   
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  
