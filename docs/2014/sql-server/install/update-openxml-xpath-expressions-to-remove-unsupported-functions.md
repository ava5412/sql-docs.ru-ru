---
title: Обновите выражения OPENXML XPath, удалив неподдерживаемые функции | Документация Майкрософт
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
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 87a35ea41c36250c1173df22204e6222dae0d384
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172075"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a>Обновите выражения XPath OPENXML, удалив неподдерживаемые функции
  Помощник по обновлению обнаружил использование функциональности XPath. Работу некоторых приложений могут затронуть изменения в функциональности XPath для компонентов OPENXML после обновления.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 MSXML 3.0 является теперь базовым обработчиком выражений XPath, используемых в запросах OPENXML. MSXML 3.0 имеет ядро, более строго соответствующее спецификации XPath 1.0, где была отменена поддержка следующих функций:  
  
-   format-number();  
  
-   formatNumber();  
  
-   current();  
  
-   element-available();  
  
-   function-available();  
  
-   system-property().  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Вместо функций format-number() и formatNumber() можно использовать [!INCLUDE[tsql](../../includes/tsql-md.md)]. Для других неподдерживаемых функций, перечисленных ранее, прямой альтернативы нет.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
