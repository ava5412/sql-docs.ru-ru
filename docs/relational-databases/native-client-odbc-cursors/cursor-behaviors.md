---
title: Режимы работы курсоров | Документация Майкрософт
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: bd5ce2d661903558a0bb564f61a04e889fa071df
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39536224"
---
# <a name="cursor-behaviors"></a>Режимы работы курсоров
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC поддерживает параметры ISO, предназначенные для указания поведения курсоров, задавая их прокручиваемость и чувствительность. Эти поведения задаются с помощью параметров SQL_ATTR_CURSOR_SCROLLABLE и SQL_ATTR_CURSOR_SENSITIVITY во время вызова [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализует эти параметры, запрашивая серверные курсоры со следующими характеристиками.  
  
|Параметры режима работы курсоров|Запрошенные характеристики серверного курсора|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE и SQL_SENSITIVE|Курсор, управляемый набором ключей, и основанный на версии оптимистический параллелизм|  
|SQL_SCROLLABLE и SQL_INSENSITIVE|Статический курсор и параллелизм в режиме «только чтение»|  
|SQL_SCROLLABLE и SQL_UNSPECIFIED|Статический курсор и параллелизм в режиме «только чтение»|  
|SQL_NONSCROLLABLE и SQL_SENSITIVE|Однопроходный курсор и основанный на версии оптимистический параллелизм|  
|SQL_NONSCROLLABLE и SQL_INSENSITIVE|Результирующий набор по умолчанию (последовательный доступ, только чтение)|  
|SQL_NONSCROLLABLE и SQL_UNSPECIFIED|Результирующий набор по умолчанию (последовательный доступ, только чтение)|  
  
 Основанный на версии оптимистический параллелизм требует **timestamp** столбца в базовой таблице. Если управления оптимистичным параллелизмом на основе версии запрашивается на таблице, которая не имеет **timestamp** столбец, сервер использует основанный на значениях оптимистичного параллелизма.  
  
## <a name="scrollability"></a>Прокручиваемость  
 Если параметр SQL_ATTR_CURSOR_SCROLLABLE имеет значение SQL_SCROLLABLE, курсор поддерживает все различные значения для *FetchOrientation* параметр [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Если параметр SQL_ATTR_CURSOR_SCROLLABLE имеет значение SQL_NONSCROLLABLE, курсор поддерживает только *FetchOrientation* для SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Чувствительность  
 Если параметр SQL_ATTR_CURSOR_SENSITIVITY имеет значение SQL_SENSITIVE, курсор отражает изменения данных, произведенные текущим пользователем или зафиксированные другими пользователями. Если параметр SQL_ATTR_CURSOR_SENSITIVITY имеет значение SQL_INSENSITIVE, курсор не отражает изменения данных.  
  
## <a name="see-also"></a>См. также  
 [Использование курсоров (ODBC)](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md) [свойства курсора](properties/cursor-properties.md) 
  
  
