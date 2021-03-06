---
title: Наборы строк | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73f16529f84fd9a7eb0158061ab4f875050a8496
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411713"
---
# <a name="rowsets"></a>Наборы строк
  Набор строк — это несколько строк, содержащих столбцы данных. Наборы строк — это основные объекты, позволяющие всем поставщикам данных OLE DB представлять данные результирующих наборов в виде таблиц.  
  
 После создания сеанса с помощью **IDBCreateSession::CreateSession** метод, потребитель может использовать либо **IOpenRowset** или **IDBCreateCommand** интерфейс для сеанса, чтобы создать набор строк. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента поддерживает оба этих интерфейса. Оба эти метода описаны здесь.  
  
-   Создать набор строк путем вызова **IOpenRowset::OpenRowset** метод.  
  
     Это эквивалентно созданию набора строк из одной таблицы. Этот метод открывает и возвращает набор строк, включающий все строки одной базовой таблицы. Один из аргументов для **OpenRowset** — это идентификатор таблицы, который идентифицирует таблицу, из которой создается набор строк.  
  
-   Создать командный объект, вызвав **IDBCreateCommand::CreateCommand** метод.  
  
     Объект команд выполняет команды, поддерживаемые поставщиком. С помощью поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] потребитель может указать любую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)], например SELECT, или вызов хранимой процедуры. Создание набора строк с помощью объекта команд включает следующие шаги.  
  
    1.  Потребитель вызывает метод **IDBCreateCommand::CreateCommand** метод сеанса, чтобы получить объект команд, запрашивающий **ICommandText** интерфейса на объект команды. Это **ICommandText** интерфейса задает и получает действительный текст команды. Потребитель заполняет текст команды путем вызова **ICommandText::SetCommandText** метод.  
  
    2.  Вызывает **ICommand::Execute** метод о команде. Объект набора строк, создаваемый во время выполнения команды, содержит результирующий набор этой команды.  
  
 Потребитель может использовать **ICommandProperties** интерфейс для получения или задания свойств набора строк, возвращаемого командой, выполняемая **ICommand::Execute** интерфейсов. Наиболее часто запрашиваемыми свойствами являются интерфейсы, которые должны поддерживаться набором строк. Кроме интерфейсов, потребитель может запросить свойства, изменяющие поведение набора строк или интерфейса.  
  
 Потребители освобождают наборы строк с **IRowset::Release** метод. При освобождении набора строк освобождаются все дескрипторы строк, удерживаемые потребителем для данного набора строк. При освобождении набора строк методы доступа не освобождаются. Если у вас есть **IAccessor** интерфейс, он по-прежнему имеет к освобождению.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание набора строк с помощью интерфейса IOpenRowset](creating-a-rowset-with-iopenrowset.md)  
  
-   [Создание наборов строк с помощью метода ICommand::Execute](creating-rowsets-with-icommand-execute.md)  
  
-   [Свойства и поведение наборов строк](rowset-properties-and-behaviors.md)  
  
-   [Наборы строк и курсоры SQL Server](rowsets-and-sql-server-cursors.md)  
  
-   [Выборка строк](fetching-rows.md)  
  
-   [Выборка одной строки с помощью интерфейса IRow](fetching-a-single-row-with-irow.md)  
  
-   [Закладки](bookmarks.md)  
  
-   [Обновление данных в наборах строк](updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
