---
title: Повторная инициализация подписок — одна подписка | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.reinit.single.f1
helpviewer_keywords:
- Reinitialize Subscription(s) dialog box
ms.assetid: 9b0cf0be-d1f1-4163-a0ca-d6f095aa707e
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a73064082068aa97d1865c14b864e336b91cee6b
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37348646"
---
# <a name="reinitialize-subscriptions---one-subscription"></a>Повторная инициализация подписок — одна подписка
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При помощи диалогового окна **Повторная инициализация подписок** можно выбрать подписки для повторной инициализации. Повторная инициализация подразумевает применение моментального снимка к подписчику; она выполняется агентом распространителя для подписок на публикации транзакций и агентом слияния для подписок на публикации слиянием.  
  
## <a name="options"></a>Параметры  
 **Использовать текущий моментальный снимок**  
 Выберите, чтобы применить текущий моментальный снимок к подписчику при следующем запуске агента распространителя или агента слияния. Если допустимый моментальный снимок отсутствует, этот параметр выбрать нельзя.  
  
 **Использовать новый моментальный снимок**  
 Выберите, чтобы выполнить повторную инициализацию подписки с новым моментальным снимком. Этот моментальный снимок можно применять к подписчику только после того, как он был сформирован агентом моментальных снимков. Если агент моментальных снимков запускается по расписанию, подписка не будет повторно инициализирована до следующего запланированного запуска агента моментальных снимков.  
  
 Выберите **Создать новый моментальный снимок** для немедленного запуска агента моментальных снимков.  
  
 **Передать несинхронизированные изменения перед повторной инициализацией**  
 Только репликация слиянием. Выберите, чтобы передать все ожидающие обработки изменения из базы данных подписки, прежде чем данные подписчика будут перезаписаны моментальным снимком.  
  
 Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
 **Пометить для повторной инициализации**  
 Щелкните, чтобы отметить подписку для повторной инициализации. После того как будет доступен моментальный снимок, при следующем запуске для подписки агента распространителя или агента слияния он применяется к подписчику.  
  
## <a name="see-also"></a>См. также:  
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  
