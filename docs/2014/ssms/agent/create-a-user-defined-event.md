---
title: Создание пользовательского события | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4c59bfb6f5f2c9621d212dc52a92daecd79fad7b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37313324"
---
# <a name="create-a-user-defined-event"></a>Создание пользовательского события
  Можно создать пользовательское событие, если нужно производить мониторинг событий, отличных от предопределенных системой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно назначить уровень серьезности для каждого пользовательского события.  
  
> [!NOTE]  
>  При использовании среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]выберите параметр **Записать журнал событий приложений Windows** для каждого сообщения определяемого пользователем события, чтобы регистрировать данные сообщения. По умолчанию после возникновения определяемые пользователем сообщения с уровнем серьезности, меньшим 19, не отправляются в журнал приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Определяемые пользователем сообщения с уровнем серьезности, меньшим 19, не приводят к возникновению предупреждения агента SQL Server.  
  
 Определяемые пользователем события должны обладать уникальными номерами сообщений. Номера сообщений для определяемых пользователем событий должны превышать 50 000. Можно определить сообщения для событий на нескольких языках. Однако перед добавлением сообщений на других языках должно быть создано сообщение об ошибке **En-US** .  
  
 При управлении многоязыковым окружением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо создать пользовательские сообщения на всех поддерживаемых языках. Например, если создается новое сообщение события, которое будет использоваться и на английском, и на немецком сервере, то необходимо использовать один и тот же номер сообщения и один и тот же уровень серьезности для обоих серверов, но на каждый из них назначить сообщение на соответствующем языке.  
  
 В следующих задачах приводятся сведения о том, как создавать пользовательские события и реагирующие на них предупреждения.  
  
 **Создание предупреждения по номеру сообщения**  
  
-   [Среда Среда SQL Server Management Studio](create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **Создание предупреждения по уровню серьезности**  
  
-   [Среда Среда SQL Server Management Studio](create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **Определение ответа на предупреждение**  
  
-   [Среда Среда SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 **Создание сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 **Изменение сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 **Удаление сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 **Отключение или повторное включение предупреждения**  
  
-   [Среда Среда SQL Server Management Studio](disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
  
