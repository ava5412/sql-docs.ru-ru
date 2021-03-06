---
title: Перспективы | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bb27b635b450b8815087d3ac5a93f9e360cddf96
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155305"
---
# <a name="perspectives"></a>перспективами
  Перспективой называется определение, позволяющее пользователям рассматривать куб с помощью более простого способа. Перспектива — это подмножество средств куба. Перспектива позволяет администраторам создавать представление куба и помогает пользователям сосредоточиться на данных, имеющих для них наибольшую значимость. Перспектива содержит подмножества множества всех объектов куба. Перспектива не может включать элементы, которые не определены в родительском кубе.  
  
 Простой объект <xref:Microsoft.AnalysisServices.Perspective> состоит из основной информации, измерений, групп мер, вычислений, ключевых показателей эффективности и действий. Основная информация включает имя и меру перспективы по умолчанию. Измерения — это подмножество измерений куба. Группы мер — это подмножество групп мер куба. Вычисления — это подмножество вычислений куба. Ключевые показатели эффективности представляют собой подмножество ключевых показателей производительности куба. Действия — это подмножество действий куба.  
  
 Вначале должны быть проведены обновление и обработка куба, и только после этого появляется возможность использовать перспективу.  
  
 Кубы могут быть очень сложными объектами для исследования в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Один куб может представлять содержимое целого хранилища данных, при этом несколько групп мер в кубе будут представлять несколько таблиц фактов и несколько измерений, основанных на нескольких таблицах измерений. Такой куб представляет собой очень сложную конструкцию с высокоразвитой структурой, что может отпугнуть пользователей, которым для удовлетворения своих запросов в области бизнес-аналитики и отчетности зачастую необходимо взаимодействовать только с небольшой частью куба.  
  
 В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], можно использовать перспективу для упрощения восприятия куба в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Перспектива определяет просматриваемое подмножество куба, которое предоставляет точки зрения на данные куба, учитывающие особенности предприятия и приложения. Перспектива контролирует видимость объектов, содержащихся в кубе. В перспективе можно отображать или скрывать следующие объекты:  
  
-   Измерения  
  
-   Атрибуты  
  
-   Иерархии  
  
-   Группы мер  
  
-   меры  
  
-   Ключевые показатели эффективности  
  
-   Вычисления (вычисляемые элементы, именованные наборы и команды скриптов)  
  
-   Действия  
  
 Например **Adventure Works** кубе [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] пример [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] база данных содержит одиннадцать групп мер и двадцать одно различное измерение куба, представляющее продажи, прогнозы продаж и финансовые данные. Клиентское приложение может напрямую указывать весь куб, но такая точка зрения может быть перегружена для пользователя, пытающегося извлечь основные сведения о прогнозах продаж. Вместо этого можно использовать тот же пользователь **цели продаж** перспективу, можно ограничить представление **Adventure Works** куба объектами, относящимися к прогнозированию продаж.  
  
 Даже те объекты куба, которые не видны пользователю в перспективе, могут быть указаны напрямую и извлечены с помощью инструкций XML для аналитики, многомерных выражений или расширений интеллектуального анализа данных. Перспективы не ограничивают доступ к объектам в кубе и не должны использоваться с такой целью. Перспективы используются для улучшения качества работы пользователя с кубом.  
  
 Перспектива является представлением куба в режиме только для чтения. Перспективу нельзя использовать для переименования или изменения объектов в кубе. Также с помощью перспективы нельзя изменить поведение или возможности куба, например использование визуальных итогов.  
  
## <a name="security"></a>безопасность  
 Перспективы предназначены для использования не в качестве механизма обеспечения безопасности, а как средство улучшения качества работы пользователя в приложениях бизнес-аналитики. Все параметры безопасности перспективы наследуются из базового куба. Например, перспективы не могут обеспечить доступ к объектам куба, к которым пользователь еще не имеет доступа. Безопасность куба должна быть разрешена прежде, чем будет предоставлен доступ к объектам в кубе через перспективу.  
  
  
