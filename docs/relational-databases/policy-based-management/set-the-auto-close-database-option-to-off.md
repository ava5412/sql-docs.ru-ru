---
title: Задание значения OFF для параметра базы данных AUTO_CLOSE | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c17d672b5d2d78da3f96cf869432dba86143253a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952468"
---
# <a name="set-the-autoclose-database-option-to-off"></a>Задание значения OFF для параметра базы данных AUTO_CLOSE
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет, имеет ли параметр AUTO_ CLOSE значение OFF. Если параметр AUTO_CLOSE имеет значение ON, это может привести к снижению производительности баз данных, к которым часто выполняются обращения, из-за увеличения издержек на открытие и закрытие базы данных после каждого соединения. Параметр AUTO_CLOSE также очищает кэш процедур после каждого соединения.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 При частом обращении к базе данных присвойте параметру AUTO_CLOSE базы данных значение OFF.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
