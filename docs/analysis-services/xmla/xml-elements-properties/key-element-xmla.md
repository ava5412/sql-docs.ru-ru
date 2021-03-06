---
title: Ключ элемента (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bea00c5b5fdff010d667db19ef3af28284ce3ed9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036922"
---
# <a name="key-element-xmla"></a>Элемент Key (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит значение ключа элемента для элемента атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Keys>  
   ...  
   <Key>...</Key>  
   ...  
</Keys>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Любой|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Ключи](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Используемый этим элементом тип данных должен соответствовать типу данных надлежащего ключевого столбца указанного атрибута. Если для родителя **Key** элементы **Attribute** не указаны, то для определения модифицируемых элементов атрибута используются элементы **AttributeName** и **Name** , указанные в родительском элементе **Attribute** .  
  
## <a name="see-also"></a>См. также
 [Атрибут элемента &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)   
 [Элемент AttributeName &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)   
 [Элемент DROP &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Вставка элемента &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Элемент KeyColumn &#40;ASSL&#41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Где элемент &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
