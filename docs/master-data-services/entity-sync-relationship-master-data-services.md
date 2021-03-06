---
title: Отношение синхронизации сущностей (Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 27a3a66a9fb4b31e96f7a09082ba6867b36be722
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046302"
---
# <a name="entity-sync-relationship-master-data-services"></a>Отношение синхронизации сущностей (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Синхронизация сущностей — это односторонняя повторяемая синхронизация между версиями сущности. Она позволяет разным моделям совместно использовать данные сущностей. Можно поддерживать единый источник истины в одной модели и использовать эти основные данные в других моделях. Например, можно хранить данные о штатах США в сущности одной модели и использовать эти данные в других моделях.  
  
 Синхронизация сущностей также позволяет сделать однократную копию данных.  
  
 Все конечные элементы с атрибутами свободных форм и файлов в исходной сущности будут синхронизированы с целевой сущностью в ходе синхронизации. При этом создаются, удаляются и изменяются схема сущности и ее элементы.  
  
 После установления отношения синхронизации целевая сущность может быть изменена только в ходе синхронизации. Отношение синхронизации в любое время можно удалить, чтобы сделать целевую сущность доступной для редактирования.  
  
## <a name="see-also"></a>См. также:  
 [Создание и выполнение отношений синхронизации сущностей (Master Data Services)](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [Создание и удаление отношения синхронизации сущностей (Master Data Services)](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  
