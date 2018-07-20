---
title: Выделение данных диаграммы путем добавления полосковых линий (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: addd6137-4b6e-4e88-a7e8-9600fcd1ccce
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 4e9c8704c599a9e0b82267b4f7efe8a8e7b8d5ec
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327104"
---
# <a name="highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs"></a>Выделение данных диаграммы путем добавления полосковых линий (построитель отчетов и службы SSRS)
  Полосковые линии, или полосы, представляют собой горизонтальные или вертикальные области, которые оттеняют фон диаграммы через регулярные или заданные пользователем интервалы. Полосковые линии используют, чтобы:  
  
-   Улучшить читаемость отдельных значений диаграммы. Указывайте полосковые линии через регулярные интервалы, чтобы отделить точки данных при чтении диаграммы.  
  
-   Выделить даты, возникающие через регулярные интервалы. Например, в отчете о продажах можно воспользоваться полосковыми линиями для обозначения точек данных, соответствующих концу недели.  
  
-   Выделить конкретный ключевой диапазон. В предыдущем примере можно выделить полосковой линией наибольший диапазон продаж от 80 до 100 долларов.  
  
 Полосковые линии не применяются в фигурных и полярных типах диаграмм.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-interlaced-strip-lines-at-regular-intervals-on-a-chart"></a>Отображение на диаграмме полосковых линий, чередующихся через равные интервалы  
  
1.  Для отображения горизонтальных полосковых линий щелкните правой кнопкой мыши вертикальную ось диаграммы и выберите пункт **Свойства вертикальной оси**.  
  
     Для отображения вертикальных полосковых линий щелкните правой кнопкой мыши горизонтальную ось диаграммы и выберите пункт **Свойства горизонтальной оси**.  
  
2.  Выберите параметр **Использовать чередование** . На диаграмме появятся серые полосковые линии.  
  
3.  Укажите цвет полосковых линий с помощью расположенного рядом раскрывающегося списка **Цвет** (необязательно).  
  
### <a name="to-display-interlaced-strip-lines-at-custom-intervals-on-a-chart"></a>Отображение на диаграмме полосковых линий, чередующихся через заданные пользователем интервалы  
  
1.  Для отображения горизонтальных полосковых линий щелкните правой кнопкой мыши вертикальную ось диаграммы и выберите пункт **Свойства вертикальной оси**.  
  
     Для отображения вертикальных полосковых линий щелкните правой кнопкой мыши горизонтальную ось диаграммы и выберите пункт **Свойства горизонтальной оси**.  
  
     Ее свойства отображаются в окне «Свойства».  
  
2.  В разделе **Вид** панели свойств нажмите для свойства StripLines кнопку "Изменить коллекцию (…)", чтобы открыть **редактор коллекции ChartStripLine**.  
  
3.  Нажмите кнопку **Добавить** , чтобы добавить новую полосковую линию в коллекцию.  
  
4.  Щелкните StripWidth, чтобы задать ширину полосковой линии в отчете в дюймах. При выделении даты или времени щелкните StripWidthType и выберите интервал времени.  
  
5.  Введите значение или выражение для свойства Interval, чтобы задать частоту повторения полосковых линий.  Например, если указать интервал 10, а толщина полосковой линии равна 5, то полосковые линии появятся у значений от 0 до 5, от 15 до 20, от 30 до 35 и т. д.  
  
> [!NOTE]  
>  По умолчанию свойство Interval установлено в значение Auto. Оно означает, что диаграмма не будет вычислять интервал для пользовательских полосковых линий. Диаграмма вычисляет интервалы для полосковых линий, только если задано значение интервала.  
  
## <a name="see-also"></a>См. также  
 [Форматирование меток оси на диаграмме (построитель отчетов и службы SSRS)](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Форматирование диаграммы (построитель отчетов и службы SSRS)](formatting-a-chart-report-builder-and-ssrs.md)   
 [Добавление скользящего среднего в диаграмму &#40;построитель отчетов и службы SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
  
  