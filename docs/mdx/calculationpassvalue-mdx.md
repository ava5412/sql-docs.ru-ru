---
title: CalculationPassValue (многомерные Выражения) | Документы Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ca5966492ac83599cd4a053ea526e2ce366e4b0e
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739993"
---
# <a name="calculationpassvalue-mdx"></a>CalculationPassValue (многомерные выражения)


  Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      Numeric syntax  
CalculationPassValue(Numeric_Expression,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
String syntax  
CalculationPassValue(String_Expression ,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
 *String_Expression*  
 Допустимое строковое выражение (обычно многомерное выражение над координатами ячейки), возвращающее число, представленное в виде строки.  
  
 *Pass_Value*  
 Допустимое числовое выражение, указывающее номер этапа вычислений.  
  
 ABSOLUTE  
 Значение флага доступа, указывающее, что *Pass_Value* параметр содержит отсчитываемый от нуля индекс этапа вычисления. Если флаг доступа не указан, это значение используется по умолчанию.  
  
 RELATIVE  
 Значение флага доступа, указывающее, что *Pass_Value* параметр содержит относительное смещение этапа запущенного вычисления. Если смещение указывает на этап вычисления с отрицательным номером, используется этап с номером «0», и ошибка не возникает.  
  
 ALL  
 Если указан этот флаг, все значения, кроме тех, которые загружаются подсистемой хранилища, равны NULL. В противном случае рассчитывается статистическое значение без применения каких-либо вычислений.  
  
## <a name="remarks"></a>Примечания  
 Если числовое выражение указано, функция возвращает его числовое значение на заданном этапе вычисления посредством вычисления многомерного выражения, при необходимости изменяя его в соответствии с флагом доступа и модификатором флага доступа.  
  
 Если строковое выражение указано, функция возвращает строковое значение, оценивая указанного строкового выражения MDX в указанном этапе вычисления и при необходимости была изменена с флагом доступа и модификатором флага доступа *.*  
  
 Автоматическое разрешение рекурсии в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], эта функция имеет практически не используется.  
  
> [!NOTE]  
>  Только администраторы могут использовать **CalculationPassValue** функции в скрипте многомерных Выражений. Возникнет ошибка, если скрипт многомерных выражений, содержащий данную функцию, выполняется в контексте роли, не имеющей прав администратора.  
  
## <a name="see-also"></a>См. также  
 [CalculationCurrentPass &#40;многомерных Выражений&#41;](../mdx/calculationcurrentpass-mdx.md)   
 [IIf &#40;многомерных Выражений&#41;](../mdx/iif-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
