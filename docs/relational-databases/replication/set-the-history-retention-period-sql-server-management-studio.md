---
title: Настройка срока хранения журнала (SQL Server Management Studio) | Документация Майкрософт
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
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1141d323f1fe0a2ab57b38c2935d048391abd44b
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352116"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>настроить срок хранения журнала (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Укажите срок хранения журнала на странице **Общие** диалогового окна **Свойства базы данных распространителя — \<база_данных_распространителя>**. Эта настройка управляет длительностью хранения журнала агента репликации. Эту страницу можно открыть на странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>**. Дополнительные сведения о доступе к этому диалоговому окну см. в статье [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Указание срока хранения журнала  
  
1.  На странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку свойств (**…**) для базы данных распространителя.  
  
2.  Введите значение в поле **Сохранять журнал производительности репликации не менее** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
  
  
