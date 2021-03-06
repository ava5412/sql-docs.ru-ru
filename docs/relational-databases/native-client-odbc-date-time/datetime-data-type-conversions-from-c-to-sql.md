---
title: Преобразования из C в SQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC], C to SQL
ms.assetid: 7ac098db-9147-4883-8da9-a58ab24a0d31
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: f983a9ae2d98b5e93b08b65938b6627e1ea83c6c
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39542554"
---
# <a name="datetime-data-type-conversions-from-c-to-sql"></a>Преобразования типа данных datetime из C в SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В этом разделе перечислены проблемы, которые следует учитывать при преобразовании типов C в типы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы даты и времени.  
  
 Преобразования, описанные в следующей таблице, относятся к преобразованиям, совершаемым на клиенте. В случаях, когда клиент задает точность в долях секунды для параметра, который отличается от, определенные на сервере, клиентское преобразование может быть выполнена успешно, но сервер возвратит ошибку при **SQLExecute** или  **SQLExecuteDirect** вызывается. В частности, ODBC рассматривает любое усечение долей секунды как ошибку, тогда как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] их округляет; например, округление выполняется при переходе от **datetime2(6)** для **datetime2(2)**. Значения столбцов даты-времени округляются до 1/300 секунды, а в значениях типа smalldatetime сервер устанавливает для секунд значение, равное нулю.  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
||SQL_TYPE_DATE|SQL_TYPE_TIME|SQL_SS_TIME2|SQL_TYPE_TIMESTAMP|SQL_SS_TIMSTAMPOFFSET|SQL_CHAR|SQL_WCHAR|  
|SQL_C_DATE|1|-|-|1,6|1,5,6|1,13|1,13|  
|SQL_C_TIME|-|1|1|1,7|1,5,7|1,13|1,13|  
|SQL_C_SS_TIME2|-|1,3|1,10|1,7|1,5,7|1,13|1,13|  
|SQL_C_BINARY(SQL_SS_TIME2_STRUCT)|Недоступно|Недоступно|1,10,11|Недоступно|Недоступно|Недоступно|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|1,2|1,3,4|1,4,10|1,10|1,5,10|1,13|1,13|  
|SQL_C_SS_TIMESTAMPOFFSET|1,2,8|1,3,4,8|1,4,8,10|1,8,10|1,10|1,13|1,13|  
|SQL_C_BINARY(SQL_SS_TIMESTAMPOFFSET_STRUCT)|Недоступно|Недоступно|Недоступно|Недоступно|1,10,11|Недоступно|Недоступно|  
|SQL_C_CHAR/SQL_WCHAR (date)|9|9|9|9,6|9,5,6|Недоступно|Недоступно|  
|SQL_C_CHAR/SQL_WCHAR (time2)|9|9,3|9,10|9,7,10|9,5,7,10|Недоступно|Недоступно|  
|SQL_C_CHAR/SQL_WCHAR (datetime)|9,2|9,3,4|9,4,10|9,10|9,5,10|Недоступно|Недоступно|  
|SQL_C_CHAR/SQL_WCHAR (datetimeoffset)|9,2,8|9,3,4,8|9,4,8,10|9,8,10|9,10|Недоступно|Недоступно|  
|SQL_C_BINARY(SQL_DATE_STRUCT)|1,11|Недоступно|Недоступно|Недоступно|Недоступно|Недоступно|Недоступно|  
|SQL_C_BINARY(SQL_TIME_STRUCT)|Недоступно|Недоступно|Недоступно|Недоступно|Недоступно|Недоступно|Недоступно|  
|SQL_C_BINARY(SQL_TIMESTAMP_STRUCT)|Недоступно|Недоступно|Недоступно|Недоступно|Недоступно|Недоступно|Недоступно|  
  
## <a name="key-to-symbols"></a>Расшифровка символов  
  
-   **-**: Преобразование не поддерживается. Создается запись диагностики с кодом SQLSTATE 07006 и сообщением «Нарушение атрибута ограниченного типа данных».  
  
-   **1**: создается Если передаваемых данных не является допустимым, создается запись диагностики с кодом SQLSTATE 22007 и сообщением «недопустимые дата и время формат».  
  
-   **2**: поля времени должны быть равны нулю или диагностическая запись с кодом SQLSTATE 22008 и сообщением «Частичное усечение».  
  
-   **3**: долей секунды должно быть равно нулю или диагностическая запись с кодом SQLSTATE 22008 и сообщением «Частичное усечение».  
  
-   **4**: компонент даты учитывается.  
  
-   **5**: часовой пояс устанавливается для клиента с часовым поясом.  
  
-   **6**: время установлено равным нулю.  
  
-   **7**: дата устанавливается в текущую дату.  
  
-   **8**: время приводится от часового пояса клиента в формате UTC. Если во время этого преобразования возникла ошибка, создается запись диагностики с кодом SQLSTATE 22008 и сообщением «Переполнение поля datetime».  
  
-   **9**: строка анализируется и преобразуется, datetime, datetimeoffset, значение даты или времени, в зависимости от первого встреченного знака препинания и наличия остальных компонентов. Затем строка преобразуется в целевой тип согласно правилам, описанным в приведенной выше таблице для типа исходных данных, который выясняется в процессе анализа. Если во время синтаксического анализа обнаружена ошибка, то создается диагностическая запись с кодом SQLSTATE 22018 и сообщением «Недопустимое значение символа для спецификации преобразования». Для параметров типа datetime и smalldatetime, если значение года выходит за пределы допустимого диапазона, создается диагностическая запись с кодом SQLSTATE 22007 и сообщением «Недопустимый формат даты и времени».  
  
     Значение datetimeoffset после преобразования во времени в формате UTC должно находиться в пределах диапазона, даже если преобразование во времени в формате UTC не требуется. Причина этого заключается в том, что поток табличных данных и сервер всегда нормализуют время в значениях datetimeoffset для времени в формате UTC, поэтому клиент должен проверять, что значение времени после преобразования во времени в формате UTC находится в пределах поддерживаемого диапазона. Если переданы недопустимые для поддерживаемого диапазона времени в формате UTC данные, то создается диагностическая запись с кодом SQLSTATE 22007 и сообщением «Недопустимый формат даты и времени».  
  
-   **10**: Если происходит усечение с потерей данных, то диагностики создается запись с кодом SQLSTATE 22008 и сообщением «недопустимый формат времени». Эта ошибка также возникает в том случае, если значение выходит за пределы диапазона, который может быть представлен диапазоном времени в формате UTC, используемым сервером.  
  
-   **11**: Если байтовая длина данных равен размеру структуры, необходимые для типа SQL, то диагностики создается запись с ошибкой SQLSTATE 22003 и сообщением «Численное значение вне допустимого диапазона».  
  
-   **12**: Если байтовая длина данных равна 4 или 8, данные отправляются на сервер в необработанном формате smalldatetime или datetime TDS. Если байтовая длина данных в точности равна размеру структуры SQL_TIMESTAMP_STRUCT, данные преобразуются в формат потока табличных данных для типа datetime2.  
  
-   **13**: Если происходит усечение с потерей данных, то диагностики создается запись с кодом SQLSTATE 22001 и сообщением «Строковые данные, усечение справа».  
  
     Число разрядов для дробной секунды (масштаб) определяется размером целевого столбца согласно следующей таблице.  
  
    ||||  
    |-|-|-|  
    |Тип|Подразумеваемый масштаб<br /><br /> 0|Подразумеваемый масштаб<br /><br /> 1..9|  
    |SQL_C_TYPE_TIMESTAMP|19|21..29|  
  
     Однако для типа SQL_C_TYPE_TIMESTAMP, если доли секунды можно представить в трех разрядах без потери данных, и размер столбца больше или равен 23, для дробной доли секунды создаются ровно три разряда. Это поведение обеспечивает обратную совместимость с приложениями, разработанными в расчете на более старые драйверы ODBC.  
  
     Для размеров столбцов, превышающих диапазон таблицы, подразумевается масштаб 9. Это преобразование должно учитывать доли секунд с точностью до девяти значащих цифр — максимум, поддерживаемый ODBC.  
  
     Если для столбца установлен размер, равный нулю, в ODBC это означает неограниченный размер для символьных типов переменной длины (9 разрядов там, где не работает правило трех разрядов для типа SQL_C_TYPE_TIMESTAMP). Задать размер столбца, равный нулю, для символьных типов фиксированной длины будет ошибкой.  
  
-   **Н/д**: существующие [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более ранних поведение сохраняется.  
  
## <a name="see-also"></a>См. также  
 [Дата и время улучшения &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
