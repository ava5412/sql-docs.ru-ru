---
title: Элемент warning (XMLA) | Документация Майкрософт
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
- Warning Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Warning
- microsoft.xml.analysis.warning
- http://schemas.microsoft.com/analysisservices/2003/engine#Warning
helpviewer_keywords:
- Warning element
ms.assetid: a34a6caa-4b68-486b-8f50-cdc124c65888
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ace514fd6a35fb376846c659ef64b9a40d1c116d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215754"
---
# <a name="warning-element-xmla"></a>Элемент Warning (XML для аналитики)
  Содержит сведения о предупреждении, возвращенном экземпляром служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Message>  
   <Warning   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Сообщение](message-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="attributes"></a>Атрибуты  
  
|attribute|Описание|  
|---------------|-----------------|  
|ErrorCode|Требуется `UnsignedInt` атрибута. Содержит числовой код возврата предупреждения.|  
|Severity|Необязательный `String` атрибута. Содержит серьезность предупреждения.|  
|Описание|Необязательный `String` атрибута. Содержит описательный текст предупреждения.|  
|Source|Необязательный `String` атрибута. Содержит имя компонента, который сформировал предупреждение.|  
|HelpFile|Необязательный `String` атрибута. Содержит путь или URL-адрес к файлу или разделу справки, в котором описывается предупреждение.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Элемент Error &#40;XML для Аналитики&#41;](error-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
