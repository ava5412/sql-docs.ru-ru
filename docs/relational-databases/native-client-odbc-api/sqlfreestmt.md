---
title: SQLFreeStmt | Документация Майкрософт
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 2e83bc03d42f3b3ed1fde43bdc43c441c3304be8
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39537474"
---
# <a name="sqlfreestmt"></a>Функция SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Как правило   
      Не рекомендуется применять функцию**SQLFreeStmt** в ODBC 3.0 и более поздних версиях. Однако если приложению требуется повторно использовать инструкцию следует по-прежнему использовать **SQLFreeStmt** с **SQL_RESET_PARAMS** и **SQL_UNBIND** параметры). Можно также использовать [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), и [ SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) заменить или дублируют функцию **SQLFreeStmt** и вместо него следует использовать их.  
  
 Как правило более эффективным будет повторное использование инструкций, чем их удаление и выделение. Тем не менее в некоторых ситуациях, как повторное использование инструкций, SQLFreeStmt по-прежнему необходимо использовать.  
  
## <a name="see-also"></a>См. также  
 [SQLFreeStmt, функция](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
