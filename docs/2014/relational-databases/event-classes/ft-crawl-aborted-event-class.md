---
title: Класс событий FT:Crawl Aborted | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Crawl Aborted event class
ms.assetid: eead8ea6-5051-4689-ab30-4dfbfda01fb9
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4cb1abdcd597524c270d43635efa7d6eaf5cc1ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311834"
---
# <a name="ftcrawl-aborted-event-class"></a>Класс событий FT:Crawl Aborted
  События класса **FT:Crawl Aborted** указывают на то, что при выполнении полнотекстового сканирования произошло исключение. Данная ошибка обычно приводит к остановке полнотекстового сканирования. Проверьте журнал сканирования и журнал событий [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows на предмет дополнительных сведений об ошибках.  
  
## <a name="ftcrawl-aborted-event-class-data-columns"></a>Столбцы данных класса событий FT:Crawl Aborted  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Идентификатор базы данных, в которой выполняется полнотекстовое сканирование. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**Ошибка**|**int**|Номер ошибки для данного события. Часто это номер ошибки, хранимый в таблице **sysmessages** .|31|Да|  
|**EventClass**|**int**|Тип события = 157.|27|Нет|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|Нет|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**ObjectID**|**int**|Назначенный системой идентификатор объекта, при полнотекстовом сканировании которого произошла ошибка.|22|Да|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Состояние**|**int**|Эквивалентно коду состояния ошибки.|30|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
