---
title: символ 0xFFFF не является допустимым идентификатором объекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46a8134e2685cd41e59e1cfbe39c3bfd1fc48708
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257890"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>Символ с кодом 0xFFFF не является допустимым идентификатором объекта
  Помощник по обновлению обнаружил символ 0xFFFF в идентификаторе объекта. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях такие объекты, как базы данных, таблицы и столбцы, идентификаторы которых содержат этот символ, не могут быть переименованы или указаны по ссылке, если для режима совместимости базы данных установлено значение 90 или больше. При обновлении до [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] пользовательские базы данных сохраняют свой режим совместимости. Прежде чем задать для режима совместимости значение 90 или выше, переименуйте объект, который содержит символ 0xFFFF.  
  
 Дополнительные сведения см. в разделе «Идентификаторы» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о режимах совместимости базы данных см. в разделе «sp_dbcmptlevel» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
