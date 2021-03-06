---
title: Определение исходных сведений (мастер измерений) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionmaintable.f1
ms.assetid: 0538b490-5185-49e1-a783-4ce3539a0de5
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fe54261f04a7e4064bca482c31149a558e1ea779
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181031"
---
# <a name="specify-source-information-dimension-wizard"></a>Определение исходных сведений (мастер измерений)
  Страница **Выбор основной таблицы измерения** позволяет выбрать представление источника данных, главную таблицу измерения, ключевые столбцы и столбец имен элементов для создаваемого измерения.  
  
 **Чтобы открыть мастер измерений**  
  
-   В **обозревателе решений** [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] щелкните правой кнопкой мыши папку **Измерения** для проекта [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , а затем выберите команду **Новое измерение**.  
  
## <a name="options"></a>Параметры  
 **Представление источника данных**  
 Выберите представление источника данных.  
  
 **Главная таблица**  
 Выберите таблицу из выбранного представления источников данных в качестве главной таблицы для измерения.  
  
 **Ключевые столбцы**  
 Выберите ключевые столбцы из таблицы, указанной в поле **Основная таблица** , для ключевого атрибута данного измерения.  
  
> [!NOTE]  
>  Можно выбрать несколько столбцов. Если таблица содержит составной первичный ключ, выберите все столбцы, входящие в этот ключ. Важен порядок ключевых столбцов.  
  
 **Имя столбца**  
 Выберите столбец, содержащий имена членов для данного измерения, из таблицы, указанной в поле **Основная таблица** . Необходимо указать столбец имени, прежде чем составной ключ будет доступен для использования. Чтобы создать столбец имени для составного ключа, рекомендуется создать именованное вычисление в представлении источника данных, объединяющем указанные ключевые столбцы. Если используется единственный ключ, то столбец имени необязателен.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера измерений](dimension-wizard-f1-help.md)   
 [Измерения &#40;службы Analysis Services — многомерные данные&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Измерения в многомерных моделях](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
