---
title: MSSQLSERVER_18264 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4067cde7352144c9ade23999b85b7cdaf45d5f97
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420133"
---
# <a name="mssqlserver18264"></a>MSSQLSERVER_18264
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|Microsoft SQL Server|  
|Идентификатор события|18264|  
|Источник события|MSSQLENGINE|  
|Компонент|SQLEngine|  
|Символическое имя|STRMIO_DBDUMP|  
|Текст сообщения|Выполнено резервное копирование базы данных. База данных: %s, дата (время) создания: % s(%s), страниц в дампе: %d, первый номер LSN: %s, последний номер LSN: %s, число устройств хранения: %d, сведения об устройствах: (%s). Это информационное сообщение. Вмешательство пользователя не требуется.|  
  
## <a name="explanation"></a>Объяснение  
 По умолчанию после каждого успешного создания резервной копии это информационное сообщение добавляется к журналу регистрации ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и к журналу системных событий. Если резервные копии журнала транзакций создаются очень часто, эти сообщения могут быстро накапливаться, создавая весьма крупные журналы регистрации ошибок, из-за чего возникают затруднения при поиске других сообщений.  
  
## <a name="user-action"></a>Действие пользователя  
 Вы можете отключить эти записи журнала в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью флага трассировки **3226**. Включение этого флага трассировки может потребоваться, если резервное копирование журналов выполняется часто и если ни один из применяемых скриптов не зависит от указанных записей.  
  
 Сведения об использовании флагов трассировки см. в электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Флаги трассировки (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
