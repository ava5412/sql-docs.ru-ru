---
title: Измените приложения, чтобы значения типа bigint из sysperfinfo.cntr_value | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 303faa85853825b07eab52043929b92cbc601326
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249684"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntrvalue"></a>Измените приложения, чтобы они использовали значения bigint из столбца sysperfinfo.cntr_value
  Возвращает представление sysperfinfo `bigint` значение для столбца cntr_value.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Внесите изменения в приложения, использующие представление sysperfinfo, чтобы убедиться, что они могут обрабатывать значение типа `bigint` столбца cntr_value.  
  
> [!NOTE]  
>  представление sysperfinfo является представлением совместимости. Вместо него следует использовать динамическое административное представление sys.dm_os_performance_counters.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
