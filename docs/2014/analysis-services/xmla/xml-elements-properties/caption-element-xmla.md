---
title: Заголовок элемента (XMLA) | Документация Майкрософт
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
- Caption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Caption
- http://schemas.microsoft.com/analysisservices/2003/engine#Caption
- microsoft.xml.analysis.caption
helpviewer_keywords:
- Caption element
ms.assetid: 3d10ee68-98ab-4da0-a409-800dea2f1c32
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 42a979937e087a1404393fe3bf4f6c6566ca5678
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37239614"
---
# <a name="caption-element-xmla"></a>Элемент Caption (XML для аналитики)
  Содержит сведения о заголовке родительского [HierarchyInfo](hierarchyinfo-element-xmla.md) или [член](member-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <Caption>...</Caption>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[HierarchyInfo](hierarchyinfo-element-xmla.md), [Member](member-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для элементов `HierarchyInfo` элемент `Caption` содержит имя свойства, которое предоставляет заголовки элементов в этой иерархии. Это значение эквивалентно значению свойства MEMBER_CAPTION, определенного для наборов строк оси в спецификации OLE DB для OLAP.  
  
 Для элементов `Member` элемент `Caption` содержит заголовок родительского элемента `Member` на языке, указанном для сеанса XMLA. Если не доступен ни один заголовок, этот элемент содержит уникальное имя элемента.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
