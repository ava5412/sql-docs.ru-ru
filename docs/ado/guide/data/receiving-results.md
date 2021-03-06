---
title: Получение результатов | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 950a4d88d525afd713209982cbeaa77ed060395a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272403"
---
# <a name="receiving-results"></a>Получение результатов
Большинство команд в ADO привести некоторые сведения, возвращается вызывающему. Команды, возвращение набора строк, будут получены в **записей** объект, который, возможно, наиболее часто используемые объекты ADO.  
  
 Существует несколько способов для получения данных в **записей** из источника данных, включая вызов следующие:  
  
-   [Метод Connection.Execute](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Метод Command.Execute](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Метод Recordset.Open](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection.NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [Connection.StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 Получение данных в **записей** объекта завершает процесс получения данных с участием **подключения** объекта и **команда** объекта неявно или явным образом. В системе приложения обычно клиент сервер, весь процесс получения данных требуется цикл обработки по сети для каждого заполнения **записей**.  
  
 Для получения нескольких результирующих наборов означает необходимо сделать несколько циклов приема-передачи по сети, по одной для каждого набора данных, содержащийся в **записей** объекта. Для сетей медленная или перегружена сокращения числа циклов приема-передачи может повысить производительность приложения. Таким образом, некоторые поставщики предлагают поддержки для получения нескольких **записей**s в рамках одного цикла обработки. Это описано в следующем разделе:  
  
-   [Получение нескольких наборов записей](../../../ado/guide/data/receiving-multiple-recordsets.md)
