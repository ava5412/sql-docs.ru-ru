---
title: "CalculationCurrentPass (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CALCULATIONCURRENTPASS
dev_langs:
- kbMDX
helpviewer_keywords:
- CalculationCurrentPass function
ms.assetid: 7069f7a0-8ec8-4293-8db3-b35b9327f437
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f2510f0db6f5a2895ce00514595306ac4849b357
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="calculationcurrentpass-mdx"></a>CalculationCurrentPass (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает текущий этап вычисления куба для указанного контекста запроса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CalculationCurrentPass()  
```  
  
## <a name="remarks"></a>Замечания  
 **CalculationCurrentPass** функция возвращает отсчитываемый от нуля индекс этапа вычисления для контекста текущего запроса. Автоматическое разрешение рекурсии в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], эта функция имеет практически не используется.  
  
## <a name="see-also"></a>См. также:  
 [CalculationPassValue &#40; Многомерные Выражения &#41;](../mdx/calculationpassvalue-mdx.md)   
 [IIf &#40; Многомерные Выражения &#41;](../mdx/iif-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
