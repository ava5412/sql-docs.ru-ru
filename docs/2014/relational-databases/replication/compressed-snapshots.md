---
title: Сжатые моментальные снимки | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
- compressed snapshots [SQL Server replication]
ms.assetid: 979ffa7c-3a88-4e70-8cf2-b8d452fd7a7f
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34a397f4c6597751d50aa676f07d42cc694e9c39
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303694"
---
# <a name="compressed-snapshots"></a>Сжатые моментальные снимки
  Сжатие файлов моментальных снимков уместно при передаче моментальных снимков в медленной сети или когда требуется сохранить моментальный снимок на съемный носитель, а объем несжатого моментального снимка превышает свободное место на носителе. Сжатие файлов моментальных снимков полезно в таких случаях, однако сжатие увеличивает время создания и применения моментального снимка.  
  
 Сжатые файлы моментальных снимков записываются в формате [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB, который позволяет сжимать файлы размером до 2 ГБ (если размер файлов моментальных снимков превышает 2 ГБ, их не удастся сжать). Для сжатия файлов их необходимо записать в альтернативную папку моментальных снимков (файлы, записанные в папку моментальных снимков по умолчанию, невозможно сжать). Дополнительные сведения об альтернативных папках моментальных снимков см. в статье [Альтернативные расположения папки моментальных снимков](alternate-snapshot-folder-locations.md).  
  
 Файлы распаковываются там, где запущен агент распространителя или агент слияния. Подписки по запросу, как правило, используются со сжатыми моментальными снимками, поэтому файлы распаковываются на подписчике. Когда подписчик получает сжатый файл, первоначально файл записывается во временное местоположение. После копирования сжатого файла подписчику файлы моментальных снимков в сжатом файле распаковываются по очереди при помощи средства распаковки CAB. На подписчике необходимо наличие пространства, равного размеру сжатого файла плюс размер самого большого распакованного файла.  
  
> [!NOTE]  
>  В некоторых случаях сжатые моментальные снимки повышают производительность передачи файлов моментальных снимков по сети. Однако сжатие моментального снимка требует дополнительной обработки, выполняемой агентом моментальных снимков при создании файлов моментальных снимков и агентом распространителя или агентом слияния при применении файлов моментальных снимков. Это может замедлить создание моментального снимка и в некоторых случаях увеличить время, необходимое для применения моментального снимка. Кроме того, сжатые моментальные снимки не могут быть возобновлены в случае сбоя в сети, поэтому они непригодны для ненадежных сетей. Внимательно рассмотрите перечисленные достоинства и недостатки, если планируете применять сжатые моментальные снимки в сети.  
  
 **Сжатие и доставка файлов моментальных снимков**  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Сжатие файлов моментальных снимков (среда SQL Server Management Studio)](publish/compress-snapshot-files-sql-server-management-studio.md)  
  
-   Программирование репликации на [!INCLUDE[tsql](../../includes/tsql-md.md)]: [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>См. также  
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)   
 [Параметры моментального снимка](snapshot-options.md)  
  
  
