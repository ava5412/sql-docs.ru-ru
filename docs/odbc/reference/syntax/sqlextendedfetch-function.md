---
title: Функция SQLExtendedFetch | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLExtendedFetch
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExtendedFetch
helpviewer_keywords:
- SQLExtendedFetch function [ODBC]
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a02b1c2e050b6fc7a0724286c7f023cb376e7bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32922809"
---
# <a name="sqlextendedfetch-function"></a>Функция SQLExtendedFetch
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: рекомендуется к использованию  
  
 **Сводка**  
 **SQLExtendedFetch** Извлекает указанный набор строк данных из результирующего набора и возвращает данные для всех связанных столбцов. Наборы строк можно указать в абсолютные или относительные позиции или по закладке.  
  
> [!NOTE]  
>  В ODBC 3 *.x*, **SQLExtendedFetch** будет заменен **SQLFetchScroll**. ODBC 3 *.x* приложения не должны вызывать метод **SQLExtendedFetch**; вместо этого следует вызывать **SQLFetchScroll**. Сопоставляет диспетчера драйверов **SQLFetchScroll** для **SQLExtendedFetch** при работе с ODBC 2 *.x* драйвера. ODBC 3 *.x* драйверы должны поддерживать **SQLExtendedFetch** для работы с ODBC 2 *.x* приложений, которые вызывают его. Дополнительные сведения см. в разделе «Комментарии» и [блочных курсоров, Прокручиваемые курсоры и обратной совместимости](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) в приложении G: драйвер рекомендации для обеспечения обратной совместимости.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLExtendedFetch(  
      SQLHSTMT         StatementHandle,  
      SQLUSMALLINT     FetchOrientation,  
      SQLLEN           FetchOffset,  
      SQLULEN *        RowCountPtr,  
      SQLUSMALLINT *   RowStatusArray);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *FetchOrientation*  
 [Вход] Тип выборки. Это то же самое, как *FetchOrientation* в **SQLFetchScroll**.  
  
 *FetchOffset*  
 [Вход] Количество строк для выборки. Это то же самое, как *FetchOffset* в **SQLFetchScroll**, за одним исключением. Когда *FetchOrientation* — SQL_FETCH_BOOKMARK, *FetchOffset* — это закладка фиксированной длины, не смещения относительно закладки. Другими словами **SQLExtendedFetch** извлекает закладку из этот аргумент не атрибут инструкции SQL_ATTR_FETCH_BOOKMARK_PTR. Он не поддерживает закладки переменной длины и не поддерживает извлечение строк со смещением (отличное от 0) относительно закладки.  
  
 *RowCountPtr*  
 [Выход] Указатель на буфер, в котором для возвращения количества фактически извлеченных строк. Этот буфер используется таким же образом, как буфер, указанным в атрибуте SQL_ATTR_ROWS_FETCHED_PTR инструкции. Этот буфер используется только **SQLExtendedFetch**. Не используется **SQLFetch** или **SQLFetchScroll**.  
  
 *RowStatusArray*  
 [Выход] Указатель на массив, в котором для возвращения состояния каждой строки. Этот массив используется таким же образом, как массива, заданного параметром значения SQL_ATTR_ROW_STATUS_PTR атрибут инструкции.  
  
 Однако адрес этого массива не хранится в поле SQL_DESC_STATUS_ARRAY_PTR в IRD. Кроме того, этот массив используется только **SQLExtendedFetch** и **SQLBulkOperations** с *операции* из SQL_ADD или **SQLSetPos**при вызове после **SQLExtendedFetch**. Не используется **SQLFetch** или **SQLFetchScroll**, и не используется **SQLBulkOperations** или **SQLSetPos** при вызове после **SQLFetch** или **SQLFetchScroll**. Это также не использоваться, когда **SQLBulkOperations** с *операции* SQL_ADD называется перед вызовом любой функции выборки. Другими словами он используется только в состоянии инструкции S7. Он не используется в инструкции состояния S5 или S6. Дополнительные сведения см. в разделе [переходы инструкции](../../../odbc/reference/appendixes/statement-transitions.md) в приложении B: ODBC состояния перехода таблицах.  
  
 Приложения должны предоставить допустимый указатель в *RowStatusArray* аргумент; в противном случае поведение **SQLExtendedFetch** и поведение вызовов **SQLBulkOperations**или **SQLSetPos** после курсор был был размещен по **SQLExtendedFetch** не определены.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLExtendedFetch** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLError**. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLExtendedFetch** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное. При возникновении ошибки для одного столбца, **SQLGetDiagField** не может быть вызван с *DiagIdentifier* из SQL_DIAG_COLUMN_NUMBER определение столбца, произошла ошибка, и  **SQLGetDiagField** не может быть вызван с *DiagIdentifier* из SQL_DIAG_ROW_NUMBER, чтобы определить строки, содержащей этот столбец.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|Строка или двоичные данные, возвращаемые для столбца привело к усечению непустых символьных или двоичных данных от NULL. Если он был строковое значение, было усечено справа. Если он был числовое значение, был усечен дробную часть числа.  (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01S01|Ошибка в строке|Произошла ошибка при получении одну или несколько строк. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01S06|Попытка выборки до появления результирующий набор возвращается первый набор строк|Запрошенный набор строк перекрывающегося начала результирующий набор, если текущая позиция не после первого ряда и либо *FetchOrientation* был SQL_PRIOR или *FetchOrientation* был SQL_RELATIVE с отрицательные *FetchOffset* , абсолютное значение было меньше или равно текущей SQL_ROWSET_SIZE. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01S07|Частичное усечение|Данные, возвращенные для столбца было усечено. Для числовых типов данных был усечен, дробная часть числа. Время, отметка времени и интервальных типов данных, содержащего компонент времени дробная часть времени было усечено.<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07006|Нарушение атрибута ограниченного типа данных|Значение данных не удалось преобразовать тип данных C, указанный в *TargetType* в **SQLBindCol**.|  
|07009|Недопустимый индекс дескриптора|Столбец 0 был связан с **SQLBindCol**, и атрибут инструкции SQL_ATTR_USE_BOOKMARKS задано значение SQL_UB_OFF.|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|22002|Индикатор обязательным, но не указано|Значение NULL, данные, которые были выбраны в столбец которого *StrLen_or_IndPtr* задается **SQLBindCol** является пустым указателем.<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|22003|Численное значение вне допустимого диапазона|Возвращает числовое значение (как числовое или строковое) для одного или нескольких столбцов могло привести целиком (в отличие от доли) часть усекаемое число.<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).<br /><br /> Дополнительные сведения см. в разделе [рекомендации для интервала и числовые типы данных](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md) в типах данных приложение D:.|  
|22007|Формат недопустимые даты и времени|Символьный столбец в результирующем наборе был привязан к даты, времени или структура отметки времени C, а значение в столбце было, соответственно, неверной даты, времени или отметки времени.<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|22012|Деление на ноль|Значение от арифметического выражения был возвращен, что привело к деления на ноль.<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|22015|Переполнение поля интервала|Присвоение тип интервала C из точное числовое значение или интервал тип SQL привело к потере значащих разрядов в начале поля.<br /><br /> При получении данных для тип интервала C, возникла не представление значения в тип интервала C типа SQL.<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|22018|Недопустимое символьное значение для спецификации приведения|Тип C был точное или Приблизительное числовое, datetime или тип интервала; тип SQL столбца был в символьный тип данных; и значение в столбце не является допустимым литералом связанного типа C.<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|24000|Недопустимое состояние курсора|*StatementHandle* находился в состоянии выполнения, но результирующий набор не связан с *StatementHandle*.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLError** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*, и затем вызова функции еще раз на *StatementHandle*.<br /><br /> Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLExtendedFetch** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) указанного *StatementHandle* не находился в состоянии выполнения. Функция была вызвана без предварительного вызова функции **SQLExecDirect**, **SQLExecute**, или функции каталога.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.<br /><br /> (DM) **SQLExtendedFetch** был вызван для *StatementHandle* после **SQLFetch** или **SQLFetchScroll** был вызван и перед  **SQLFreeStmt** был вызван с параметром SQL_CLOSE.<br /><br /> (DM) **SQLBulkOperations** был вызван для инструкции перед **SQLFetch**, **SQLFetchScroll**, или **SQLExtendedFetch** был вызван, и затем **SQLExtendedFetch** был вызван перед **SQLFreeStmt** был вызван с параметром SQL_CLOSE.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY106|Тип выборки за пределами допустимого диапазона|(DM) значение, указанное для аргумента *FetchOrientation* недопустим. (В разделе «Комментарии».)<br /><br /> Аргумент *FetchOrientation* был SQL_FETCH_BOOKMARK и атрибут инструкции SQL_ATTR_USE_BOOKMARKS было задано значение SQL_UB_OFF.<br /><br /> Значение параметра инструкции SQL_CURSOR_TYPE было SQL_CURSOR_FORWARD_ONLY, а значение аргумента *FetchOrientation* не SQL_FETCH_NEXT.<br /><br /> Аргумент *FetchOrientation* был SQL_FETCH_RESUME.|  
|HY107|Значение строки за пределами диапазона|Значение, указанное с помощью параметра инструкции SQL_CURSOR_TYPE был SQL_CURSOR_KEYSET_DRIVEN, но значение, указанное с помощью атрибута инструкции SQL_KEYSET_SIZE больше 0 и меньше, чем значение, указанное с помощью атрибута инструкции SQL_ROWSET_SIZE .|  
|HY111|Недопустимый закладок|Аргумент *FetchOrientation* был SQL_FETCH_BOOKMARK и закладки, указанное в *FetchOffset* недопустимый аргумент.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Драйвер или источник данных не поддерживает тип указанного выборки.<br /><br /> Драйвер или источник данных не поддерживает преобразование, определяется сочетанием *TargetType* в **SQLBindCol** и тип данных SQL соответствующего столбца. Эта ошибка применяется только в том случае, если тип данных SQL столбца был сопоставлен с типом данных SQL специфические для драйвера.|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло раньше, чем источник данных вернул результирующий набор. Время ожидания задается с помощью **SQLSetStmtOption**, SQL_QUERY_TIMEOUT.|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Поведение **SQLExtendedFetch** идентична из **SQLFetchScroll**, за исключением следующих случаев:  
  
-   **SQLExtendedFetch** и **SQLFetchScroll** использовать различные методы для получения количества извлеченных строк. **SQLExtendedFetch** возвращает число строк, загружаемых в  *\*RowCountPtr*; **SQLFetchScroll** возвращает число возвращаемых строк непосредственно в буфере, на который указывает SQL_ATTR_ROWS_FETCHED_PTR. Дополнительные сведения см. в разделе *RowCountPtr* аргумент.  
  
-   **SQLExtendedFetch** и **SQLFetchScroll** возвращают состояние каждой строки в разных массивах. Дополнительные сведения см. в разделе *RowStatusArray* аргумент.  
  
-   **SQLExtendedFetch** и **SQLFetchScroll** используют разные методы для получения закладки при *FetchOrientation* — SQL_FETCH_BOOKMARK. **SQLExtendedFetch** не поддерживает закладки переменной длины или извлечение наборы строк со смещением отличное от 0 относительно закладки. Дополнительные сведения см. в разделе *FetchOffset* аргумент.  
  
-   **SQLExtendedFetch** и **SQLFetchScroll** использовать размеры другого набора строк. **SQLExtendedFetch** использует значение атрибута инструкции SQL_ROWSET_SIZE и **SQLFetchScroll** использует значение атрибута SQL_ATTR_ROW_ARRAY_SIZE инструкции.  
  
-   **SQLExtendedFetch** имеет различную семантику по сравнению с ошибок **SQLFetchScroll**. Дополнительные сведения см. в разделе «Обработка ошибок» в разделе «Комментарии» [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
-   **SQLExtendedFetch** не поддерживает привязки смещения (атрибут инструкции SQL_ATTR_ROW_BIND_OFFSET_PTR).  
  
-   Вызовы **SQLExtendedFetch** невозможно комбинировать с вызовами **SQLFetch** или **SQLFetchScroll**и если **SQLBulkOperations** вызывается Перед вызовом любой функции выборки **SQLExtendedFetch** не может быть вызван, пока курсор закрыт и открыт повторно. То есть **SQLExtendedFetch** может вызываться только в состоянии инструкции S7. Дополнительные сведения см. в разделе [переходы инструкции](../../../odbc/reference/appendixes/statement-transitions.md) в приложении B: ODBC состояния перехода таблицах.  
  
 Если приложение вызывает **SQLFetchScroll** при использовании ODBC 2 *.x* драйвера, диспетчер драйверов сопоставляет этот вызов **SQLExtendedFetch**. Дополнительные сведения см. в разделе «SQLFetchScroll и ODBC 2 *.x* драйверы» в [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md).  
  
 В ODBC 2 *.x*, **SQLExtendedFetch** был вызван извлекать несколько строк и **SQLFetch** был вызван для получения одной строки. В ODBC 3 *.x*, с другой стороны, **SQLFetch** можно вызвать, чтобы извлекать несколько строк.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфера|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Выполнение инструкции bulk insert, update или delete операций|[Функция SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возврат сведений о столбце в результирующий набор|[Функция SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Выполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнения подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возвращает число результирующих столбцов набора|[Функция SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Позиционирование курсора, обновление данных в наборе строк или удаления данных в результирующем наборе|[Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|С помощью атрибута инструкции|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
