---
title: Элемент Name описания столбца (DTA) | Документы Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: f93b61de-01fe-4237-ada4-f1e481550564
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 051b1285b175cf0fbfae512dcbe2d52b188a36f2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33069731"
---
# <a name="name-element-for-column-dta"></a>Элемент Name описания столбца (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Задает имя для столбца индекса в пользовательской конфигурации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Index>  
    <Column>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, неограниченная длина|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Требуется один раз для каждого элемента **Column** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Column описания индекса (DTA)](../../tools/dta/column-element-for-index-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец входного XML-файла с пользовательской конфигурацией (DTA)](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
