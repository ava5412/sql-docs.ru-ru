---
title: "Инструкция FREEZE (многомерные Выражения) | Документы Microsoft"
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
- FREEZE
dev_langs:
- kbMDX
helpviewer_keywords:
- FREEZE statement
- locking cell values [MDX]
ms.assetid: 59f1e860-6f37-41af-97d6-7708bdaac933
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ff9fab5df513cea71db43f5ca26f08ccae93d553
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-scripting---freeze"></a>Сценарии многомерных Выражений - ЗАКРЕПЛЕНИЯ
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Фиксирует текущие значения ячеек заданного вложенного куба. Когда ячейки зафиксированы, изменения в других ячейках не влияют на них.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Аргументы  
 *Subcube_Expression*  
 Допустимое многомерное выражение, возвращающее вложенный куб.  
  
## <a name="remarks"></a>Замечания  
 **ЗАКРЕПИТЬ** инструкции фиксирует значения ячеек заданного вложенного куба, предотвращает последующие инструкции многомерных выражений передает сценарий изменять их значения в последующих вычислений.  
  
 В следующем примере A и B представляют вложенные кубы в скрипте вычисления многомерного выражения:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 На данном этапе как A, так и B равно 3.  
  
 Теперь введите **закрепить** функция заблокировать ячейки вложенного куба:  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 Теперь A равно 2, а B равно 3.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции сценариев многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
