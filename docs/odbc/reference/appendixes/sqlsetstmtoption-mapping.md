---
title: Сопоставление SQLSetStmtOption | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70bd586f601e8641c482b94d1a688bbdb1d528e9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909239"
---
# <a name="sqlsetstmtoption-mapping"></a>Сопоставление SQLSetStmtOption
Если приложение вызывает **SQLSetStmtOption** через ODBC 3 *.x* драйвера, вызов  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 приведет к следующим образом:  
  
-   Если *fOption* указывает атрибут инструкции ODBC пользователем, является строкой, диспетчер драйверов вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Если *fOption* указывает атрибут ODBC определен оператор, возвращающий значение 32-разрядное целое число, диспетчер драйверов вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Если *fOption* указывает атрибут инструкции, определяемым драйвером, диспетчер драйверов вызывает  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 В предыдущем трех случаях **StatementHandle** аргументу присвоено значение в *hstmt*, *атрибута* аргументу присвоено значение в *fOption* и *ValuePtr* аргументу присвоено значение как *vParam*.  
  
 Поскольку диспетчер драйверов не знает, определяемым драйвером инструкции атрибут, который должен быть строка или 32-разрядное целое значение, он должен передать в допустимое значение для *StringLength* аргумент **SQLSetStmtAttr**. Если драйвер определил специальную семантику для атрибутов инструкции, определяемым драйвером и должен вызываться с помощью **SQLSetStmtOption**, он должен поддерживать **SQLSetStmtOption**.  
  
 Если приложение вызывает **SQLSetStmtOption** задание параметра инструкции драйвера в ODBC 3 *.x* драйвер и параметр был определен в ODBC 2. *x* версии драйвера, новая константа манифеста должен быть определен для параметра в ODBC 3 *.x* драйвера. При использовании старых константы манифеста в вызове **SQLSetStmtOption**, диспетчер драйверов вызывает **SQLSetStmtAttr** с *StringLength* аргумент присвоено значение 0.  
  
 Если приложение вызывает **SQLSetStmtAttr** присваивается SQL_UB_ON в ODBC 3 SQL_ATTR_USE_BOOKMARKS *.x* драйвера атрибута инструкции SQL_ATTR_USE_BOOKMARKS задано значение SQL_UB_FIXED. SQL_UB_ON является одной константе как SQL_UB_FIXED. Диспетчер драйверов передает SQL_UB_FIXED через драйвер. В ODBC 3 является устаревшим SQL_UB_FIXED *.x*, а ODBC 3 *.x* драйвер должен реализовывать его для работы с ODBC 2. *x* приложений, использующих закладки фиксированной длины.  
  
 Для ODBC 3 *.x* драйвера, диспетчер драйверов больше не проверяет *параметр* — между SQL_STMT_OPT_MIN и SQL_STMT_OPT_MAX или больше, чем SQL_CONNECT_OPT_DRVR_START.
