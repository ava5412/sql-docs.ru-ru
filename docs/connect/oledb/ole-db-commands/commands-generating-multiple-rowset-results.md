---
title: Команды, формирующие результаты с несколькими наборами строк | Документация Майкрософт
description: Команды, формирующие результаты с несколькими наборами строк
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- OLE DB Driver for SQL Server, commands
- OLE DB Driver for SQL Server, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 579fae980b0f612aa1317407f797be9d1ff02ed3
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109626"
---
# <a name="commands-generating-multiple-rowset-results"></a>Команды, формирующие результаты с несколькими наборами строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server может возвращать несколько наборов строк из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] инструкций. Инструкции [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращают результаты, содержащие несколько наборов строк, в следующих случаях.  
  
-   Пакетные инструкции SQL представляются как единая команда.  
  
-   Хранимые процедуры реализуют пакет инструкций SQL.  
  
## <a name="batches"></a>Пакеты  
 Драйвер OLE DB для SQL Server распознает символ точки с запятой как разделитель пакета для инструкций SQL:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Отправка нескольких инструкций SQL в одном пакете более эффективна, чем выполнение каждой инструкции SQL по отдельности. Отправка одного пакета уменьшает количество циклов приема-передачи данных с клиента на сервер.  
  
## <a name="stored-procedures"></a>Хранимые процедуры  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает результирующий набор для каждой инструкции в хранимой процедуре, поэтому большинство хранимых процедур [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает несколько результирующих наборов.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Обработка нескольких результирующих наборов с помощью интерфейса IMultipleResults](../../oledb/ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>См. также:  
 [Команды](../../oledb/ole-db-commands/commands.md)  
  
  
