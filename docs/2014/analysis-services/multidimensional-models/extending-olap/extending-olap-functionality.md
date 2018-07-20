---
title: Расширение функциональных возможностей OLAP | Документация Майкрософт
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
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d55ef159195d42935db271c3b3a51860fd698ec9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220264"
---
# <a name="extending-olap-functionality"></a>Расширение функциональных возможностей OLAP
  Программист может расширять службы Analysis Services, написав сборки, персонализированные расширения и хранимые процедуры, обеспечивающие нужные функциональные возможности, которые можно использовать один или несколько раз в разнообразных приложениях базы данных. Сборки используются для расширения функциональных возможностей многомерных моделей путем добавления новых процедур и функций в язык многомерных выражений или путем встраивания персонализации.  
  
 Хранимые процедуры могут использоваться для вызова внешних подпрограмм, упрощая разработку и внедрение баз данных служб Analysis Services за счет однократной разработки общего программного кода и сохранения его в единственном местоположении. Хранимые процедуры можно использовать для расширения функциональности приложений за счет добавления дополнительных функций к собственной функциональности многомерных выражений.  
  
 Персонализации представляют собой пользовательские объекты, которые могут добавляться в куб для обеспечения функций, которые отличаются от пользователя к пользователю. Персонализации не являются постоянными объектами куба, но представляют собой объекты, которые динамически применяются клиентским приложением во время сеанса конкретного пользователя. Например, изменение валют в денежном выражении в зависимости от пользователя, который осуществляет доступ к данным, предоставление индивидуальных ключевых показателей эффективности или целевых списков предложений для постоянных покупателей в сети.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Расширение OLAP через личные настройки](extending-olap-through-personalizations.md)  
  
 [Расширения персонализации служб Analysis Services](analysis-services-personalization-extensions.md)  
  
 [Определение хранимых процедур](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  