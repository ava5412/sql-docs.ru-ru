---
title: Исключить файлы из системы управления версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b3507f06db699e8e88de2fe2e22f870b97b896e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330444"
---
# <a name="exclude-files-from-source-control"></a>Исключение файлов из системы управления версиями
  Если вы работаете над решение содержит файлы, не требующие служб управления версиями, можно использовать **исключить из системы управления версиями** команду, чтобы исключить файл из системы управления версиями. В этом случае файл остается в базе данных [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, но его возврат и извлечение в проекте невозможны.  
  
 Следует использовать **исключить из системы управления версиями** команду только к создаваемым файлам. Созданный файл — это приложения, может быть полностью воссоздан [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] на основе содержимого другого файла в решении.  
  
### <a name="to-exclude-a-file-from-source-control"></a>Исключение файла из управления версиями  
  
1.  В обозревателе решений выберите файл, который необходимо исключить.  
  
2.  На **файл** последовательно выберите пункты **системы управления версиями**, а затем нажмите кнопку **исключить**  *\<имя файла >* **из Система управления версиями**.  
  
## <a name="see-also"></a>См. также  
 [Основы системы управления версиями](../../2014/database-engine/source-control-basics.md)   
 [Задайте параметры системы управления версиями](../../2014/database-engine/set-source-control-options.md)   
 [Изменение соединений с системой управления версиями](../../2014/database-engine/change-source-control-connections.md)  
  
  
