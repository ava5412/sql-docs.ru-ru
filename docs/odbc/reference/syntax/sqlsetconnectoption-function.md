---
title: "Функция SQLSetConnectOption | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b5499852e3574c597e3a424347b22021d0887ca9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectoption-function"></a>Функция SQLSetConnectOption
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: рекомендуется к использованию  
  
 **Сводка**  
 В ODBC 3*.x*, функция ODBC 2.0 **SQLSetConnectOption** будет заменен **SQLSetConnectAttr**. Дополнительные сведения см. в разделе [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]  
>  Дополнительные сведения о том, что диспетчер драйверов преобразует эту функцию для при ODBC 2*.x* при работе с ODBC 3*.x* драйвера, в разделе [сопоставление устаревшие функции](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Замечания  
 В разделе [сведения ODBC 64-разрядных](../../../odbc/reference/odbc-64-bit-information.md), если приложение будет выполняться на 64-разрядной операционной системе.  
  
> [!NOTE]  
>  Атрибут SQL_ASYNC_DBC_FUNCTION_ENABLE появились в ODBC 3.8 не поддерживается в **SQLSetConnectOption**. Приложения, использующие асинхронной операции на дескрипторе соединения необходимо использовать **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)