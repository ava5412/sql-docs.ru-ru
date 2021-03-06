---
title: Поддержка высокого уровня доступности | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2e0f6d3f-0536-46d9-8630-835e199515bf
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ae0ee26dfd95ef6f425b749e24b6e5d506ece235
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35335568"
---
# <a name="high-availability-support"></a>Поддержка высокого уровня доступности
  Служба CDC для Oracle разработана с учетом требований высокого уровня доступности. Следующие функции составляют часть функций поддержки высокого уровня доступности:  
  
-   Служба CDC для Oracle не использует никаких файлов ресурсов (локальных или сетевых). Все состояние сохраняется в целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это позволяет без труда запустить службу на другом компьютере, использующем тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если в компьютере, на котором запущена служба, произойдет сбой. Чтобы сократить время восстановления, длительные транзакции Oracle хранятся в промежуточной таблице целевого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], благодаря чему устраняется необходимость повторного сканирования множества журналов транзакций сразу после сбоя (или перезапуска службы).  
  
-   Служба CDC для Oracle может использовать кластеризованные экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для восстановления после сбоя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и последующей отработки отказа на другом узле кластера. Администратору компьютера, на котором запущена служба Oracle CDC, при создании службы Oracle CDC Service необходимо лишь указать сведения о подключении к кластеризованному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Служба CDC для Oracle может использовать функцию зеркального отображения базы данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**AlwaysOn** . Поддержка этой функции требует, чтобы MSXDBCDC и все остальные базы данных CDC находились в одной группе доступности. Также необходимо, чтобы администратор компьютера, на котором запущена служба Oracle CDC, указал необходимые сведения о подключении к группе доступности **AlwaysOn** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (например, свойства подключения `Failover_Partner and Network=dbmssocn`). Это позволяет службе CDC автоматически возобновить обработку на вторичной реплике баз данных после отработки отказа.  
  
-   Службу CDC для Oracle можно настроить как ресурс общей службы, расположенный на отказоустойчивом кластере Windows (совместно или отдельно от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), что упрощает отработку отказа, и повторить обработку CDC при помощи ресурсов кластера. Чтобы настроить службу CDC для Oracle в качестве ресурса отказоустойчивого кластера, системному администратору необходимо настроить службу CDC для Oracle в качестве ресурса общей службы — для каждого узла отказоустойчивого кластера.  
  
-   Служба CDC для Oracle поддерживает Oracle RAC, благодаря чему возможен обмен данными между ней и базой данных Oracle, а также обработка журналов вызова, даже если один из узлов Oracle RAC отключен.  
  
  
