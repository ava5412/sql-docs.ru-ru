---
title: "Элемент Tuple (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Tuple Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.tuple
- urn:schemas-microsoft-com:xml-analysis#Tuple
- http://schemas.microsoft.com/analysisservices/2003/engine#Tuple
helpviewer_keywords:
- Tuple element
ms.assetid: d65aba10-55e1-49c1-81bc-0756c39c0da2
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 11a9d3b633e680154787615c04ee1f08b65b8139
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="tuple-element-xmla"></a>Элемент Tuple (XML для аналитики)
  Содержит коллекцию элементов [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md), содержащихся в родительском элементе [Tuples](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Tuples>  
   <Tuple>  
      <Member>...</Member>  
   </Tuple>  
   ...  
</Tuples>  
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
|Родительские элементы|[Кортежи](../../../analysis-services/xmla/xml-elements-properties/tuples-element-xmla.md)|  
|Дочерние элементы|[Член](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Когда клиентское приложение устанавливает для свойства **AxisFormat** значение *TupleFormat*, ось представляется в виде набора кортежей. Каждый элемент **Axis** содержит элемент **Tuples**, представляющий набор кортежей на этой оси. Каждый кортеж представлен с помощью элемента **Tuple**, содержащего элементы **Member** из каждой иерархии оси.  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется структура элемента **Tuple**, если клиент указывает значение *TupleFormat* или *CustomFormat* для XMLA-свойства **AxisFormat**, а на оси имеются следующие элементы:  
  
|||||  
|-|-|-|-|  
|Иерархия **Time**|1999|1999|2000|  
|Иерархия **Category**|Actual|Budget|Budget|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  