---
title: Задание ориентации текстового поля (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5b9a3e2df3b95b6d186c5a68af5f1322e951072b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205004"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Задание ориентации текстового поля (построитель отчетов и службы SSRS)
  Направление ориентации текстового поля может быть различным: горизонтальным, вертикальным (текст читается сверху вниз) или повернутым на 270 градусов (текст читается снизу вверх). Поскольку ориентация задается для текстового поля, а не для текста, ориентация применяется ко всему тексту в поле. Для различных областей текста нельзя указать различную ориентацию. Чтобы разместить разворачиваемый текст, задайте значения ширины столбца и высоты строки вручную.  
  
 Свойство WritingMode, которое используется для указания ориентации текста, недоступен в **свойства текстового поля** диалоговое окно. Необходимо открыть панель свойств и задать свойства в ней. Возможные значения для свойства WritingMode **горизонтальной** (текст читается слева направо), **вертикальной** (текст читается сверху вниз), **поворот на 270 градусов** (текст читается. снизу вверх). Чтобы разместить текст, необходимо вручную указать значения ширины столбца и высоты строки.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a>Задание ориентации текста  
  
1.  Создайте новый отчет или откройте существующий отчет.  
  
2.  Если панель свойств не открыта, перейдите на вкладку **Вид** и установите флажок **Свойства** .  
  
3.  Щелкните текстовое поле, для которого необходимо изменить ориентацию текста.  
  
4.  Найдите свойство WritingMode свойства в панели «Свойства» и в раскрывающемся списке выберите ориентацию текста для применения к текстовому полю.  
  
    > [!NOTE]  
    >  Если свойства на панели свойств упорядочены по категориям, свойство WritingMode относится к категории **Локализация** .  
  
5.  В списке выберите **Горизонтально**, **Вертикально**или **Поворот на 270 градусов**.  
  
## <a name="see-also"></a>См. также  
 [Текстовые поля &#40;построитель отчетов и службы SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [Учебник. Форматирование текста (построитель отчетов)](../tutorial-format-text-report-builder.md)  
  
  
