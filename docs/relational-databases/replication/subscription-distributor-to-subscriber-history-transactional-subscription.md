---
title: Подписка, вкладка "Журнал операций от распространителя к подписчику" (транзакционная подписка) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.disttosub.f1
ms.assetid: 1aad5b82-592e-4907-92f7-b90794175be5
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 7a6baf502f8599950931b3c81586099cf607223b
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39545044"
---
# <a name="subscription-distributor-to-subscriber-history-transactional-subscription"></a>Подписка, журнал от распространителя к подписчику (подписка на публикацию транзакций)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Вкладка **Журнал операций от распространителя к подписчику** отображает подробные сведения об агенте распространителя, включая состояние, журнал, информационные сообщения и любые сообщения об ошибках.  
  
## <a name="options"></a>Параметры  
 В меню **Вид** выберите сеансы, какого агента распространителя необходимо просмотреть, а затем в сетке **Сеансы агента распространителя**выберите определенный сеанс. Подробные сведения об этом сеансе отображаются в сетке, помеченной как **Действия в выбранном сеансе**. Если выбранный сеанс закончен с ошибкой, также выводится на экран текстовое поле, помеченное как **Описание ошибки или сообщение выбранного сеанса** .  
  
 **Вид**  
 Выберите агента распространителя, сеансы которого необходимо просмотреть. Как правило, агент распространителя работает постоянно, поэтому просмотреть можно только один сеанс.  
  
 **Состояние**  
 Состояние агента распространителя. Возможные значения состояния показаны в следующем списке:  
  
-   Ошибка  
  
-   Завершен  
  
-   Повтор  
  
-   Запущен  
  
 **Start Time**  
 Время начала сеанса.  
  
 **Время окончания**  
 Время окончания сеанса. Если агент не остановлен, это поле остается пустым.  
  
 **Длительность**  
 Длительность работы агента распространителя в этом сеансе. Если в данный момент агент работает, отображается время его работы, после завершения сеанса агента отображается общая длительность сеанса.  
  
 **Сообщение об ошибке**  
 Если сеанс завершился ошибкой, в данном поле отображается последнее сообщение об ошибке, зарегистрированное агентом распространителя. Если сеанс завершился без ошибки, это поле остается пустым.  
  
 **Сообщение действия**  
 Все информационные сообщения и сообщения об ошибках, зарегистрированные агентом распространителя в течение выбранного сеанса.  
  
 **Время действия**  
 Время, когда было выполнено действие, описанное в столбце **Сообщение действия** .  
  
 **Описание ошибки или сообщение выбранного сеанса**  
 Выводится, только если выбранный сеанс отображает значение **Ошибка** в столбце **Состояние** . Это текстовое поле отображает подробные данные об ошибке и о выполняемой во время возникновения ошибки команде. Также содержит ссылки на дополнительные данные, имеющие отношение к ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Запуск монитора репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
