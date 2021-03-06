---
title: SQLMoreResults, функция | Документы Microsoft
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
- SQLMoreResults
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLMoreResults
helpviewer_keywords:
- SQLMoreResults function [ODBC]
ms.assetid: bf169ed5-4d55-412c-b184-12065a726e89
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d156b07358d6430ec52f000ed4bebfe1c5d19d9f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32923439"
---
# <a name="sqlmoreresults-function"></a>SQLMoreResults, функция
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ODBC  
  
 **Сводка**  
 **SQLMoreResults** определяет, доступны ли дополнительные результаты на значение, содержащее инструкции **ВЫБЕРИТЕ**, **обновление**, **вставить**, или  **Удалить** инструкций и, если да, инициализирует обработки для этих результатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, ЗНАЧЕНИЕ SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE ИЛИ SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLMoreResults** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL _HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLMoreResults** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01S02|Значение параметра было изменено|При обработке значение атрибута инструкции, изменен в пакете. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|40001|Сбой сериализации|Транзакции выполнен откат из-за взаимоблокировку ресурсов в другой транзакции.|  
|40003|Неизвестный завершение операторов|Сбой подключения во время выполнения этой функции и не удается определить состояние транзакции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. **SQLMoreResults** была вызвана функция, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* . Затем **SQLMoreResults** функция была вызвана снова на *StatementHandle*.<br /><br /> **SQLMoreResults** была вызвана функция, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*  из другого потока в многопоточных приложениях.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLMoreResults** была вызвана функция.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
 **ВЫБЕРИТЕ** инструкции возвращают результирующие наборы. **ОБНОВЛЕНИЕ**, **вставить**, и **удалить** инструкции возвращают количество затронутых строк. Если любой из этих инструкций, объединяются в пакеты, отправленные с массивами параметров (по возрастанию параметр, в том порядке, в котором они представлены в пакете под номером) или в процедурах, они могут возвращать несколько результирующих наборов или количество строк. Сведения о пакеты инструкций и массивы параметров см. в разделе [пакеты инструкций SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) и [массивы значений параметров](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 После выполнения пакета, приложение устанавливается на первый результирующий набор. Приложение может вызвать **SQLBindCol**, **SQLBulkOperations**, **SQLFetch**, **SQLGetData**, **SQLFetchScroll** , **SQLSetPos**и все функции метаданных, в первой или любые последующие результирующие наборы, точно так же, как если бы только один результирующий набор. После завершения первого результирующего набора, приложение вызывает **SQLMoreResults** для перемещения к следующему результирующему набору. Если другой результирующий набор или по количеству, **SQLMoreResults** возвращает SQL_SUCCESS и инициализирует результирующий набор или число для дополнительной обработки. Если все инструкции генерации счетчик строк отображается между привести генерации набор инструкций, они могут ступенчатых посредством вызова **SQLMoreResults**. После вызова метода **SQLMoreResults** для **обновление**, **вставить**, или **удалить** инструкций, приложение может вызвать **SQLRowCount**.  
  
 В случае отсутствия текущий результирующий набор со строками строк **SQLMoreResults** отменяет этого результирующего набора и делает следующий результирующий набор или количества доступных. Если обработаны все результаты, **SQLMoreResults** не вернет значение SQL_NO_DATA. Для некоторых драйверов выходные параметры и возвращаемые значения не будут доступны до были обработаны все результирующие наборы и счетчики строк. Для таких драйверов выходные параметры и возвращаемые значения, которые становятся доступными при **SQLMoreResults** не вернет значение SQL_NO_DATA.  
  
 Все привязки, заданные для предыдущего результирующего набора по-прежнему остаются действительными. Если столбец структуры отличаются для этого результирующего набора, затем при вызове метода **SQLFetch** или **SQLFetchScroll** может повлечь ошибки или усечения. Чтобы избежать этого, приложение должно вызвать **SQLBindCol** явно повторно привязать соответствующие (или сделать, задав поля дескриптора). Кроме того, приложение может вызвать **SQLFreeStmt** с *параметр* из SQL_UNBIND, чтобы отменить привязку всех буферах столбцов.  
  
 Значения атрибутов инструкции, такие как тип курсора, параллелизм курсоров, размер набора ключей или Максимальная длина может меняться приложение переходит к пакета на вызовы **SQLMoreResults**. В этом случае **SQLMoreResults** возвращает SQL_SUCCESS_WITH_INFO и SQLSTATE 01S02 (значение параметра было изменено).  
  
 Вызов **SQLCloseCursor**, или **SQLFreeStmt** с *параметр* из SQL_CLOSE, отменяет все результирующие наборы и количество строк, которые были доступны в результате выполнения пакет. Возвращает дескриптор инструкции, выделенной или подготовленного состояние. Вызов **SQLCancel** для отмены асинхронного выполнения функции был выполнен пакет дескриптора инструкции в выполненном, навести курсор или асинхронное состояние в результате все результаты наборов и количество строк созданный пакет, они будут удалены в случае успешного вызова "Отмена". Затем инструкция возвращает состояние подготовленный и выделенный.  
  
 Если пакет инструкций или процедуры смешаны других инструкций SQL с **ВЫБЕРИТЕ**, **обновление**, **вставить**, и **удалить** инструкций, Эти другие операторы не влияют на **SQLMoreResults**.  
  
 Дополнительные сведения см. в разделе [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Поисковое обновление, вставки или удаления инструкции в пакете инструкций не влияет на все строки в источнике данных **SQLMoreResults** возвращает SQL_SUCCESS. Это поведение отличается от регистра поисковое обновление, вставьте или удалите инструкцию, которая выполняется через **SQLExecDirect**, **SQLExecute**, или **SQLParamData**, который Возвращает значение SQL_NO_DATA, если он не влияет на все строки в источнике данных. Если приложение вызывает **SQLRowCount** для получения количества строк после вызова **SQLMoreResults** Незатронутые любые строки **SQLRowCount** вернет значение SQL_NO_DATA.  
  
 Дополнительные сведения о допустимых последовательного выполнения функций обработки результатов в разделе [приложение б: ODBC состояния перехода таблицы](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Дополнительные сведения о SQL_PARAM_DATA_AVAILABLE и потоковых выходных параметров см. в разделе [получение выходных параметров с помощью метода SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="availability-of-row-counts"></a>Доступность счетчики строк  
 Если пакет содержит несколько инструкций генерации количество последовательных строк, возможно, что эти счетчики строк сводятся счетчик только одну строку. Например если пакет содержит пять инструкций insert, то некоторые источники данных не может возвращать счетчики пяти отдельных строк. Некоторые другие источники данных возвращают счетчика только одну строку, которая представляет сумму пять количество отдельных строк.  
  
 Если пакет содержит сочетание результирующий набор генерации и инструкций генерации число строк, количество строк может или могут быть недоступны во всех. Поведения драйвера по отношению к доступности количество строк, перечисленных в тип данных SQL_BATCH_ROW_COUNT, доступные посредством вызова **SQLGetInfo**. Например, предположим, что в пакете содержится **ВЫБЕРИТЕ**, а затем два **вставить**s, а другой **ВЫБЕРИТЕ**. Затем возможны следующие варианты:  
  
-   Количество строк, соответствующих двум **вставить** инструкции доступны не во всех. Первый вызов **SQLMoreResults** будут размещены на результирующем наборе второго **ВЫБЕРИТЕ** инструкции.  
  
-   Количество строк, соответствующих двум **вставить** инструкции доступны по отдельности. (Вызов **SQLGetInfo** не возвращает бит SQL_BRC_ROLLED_UP типу информации SQL_BATCH_ROW_COUNT.) Первый вызов **SQLMoreResults** будут размещены на количестве строк первого **вставить**, и второй вызов будут размещены на количестве строк второго **вставить**. Третий вызов **SQLMoreResults** будут размещены на результирующем наборе второго **ВЫБЕРИТЕ** инструкции.  
  
-   Количество строк, соответствующих двум **вставляет** сворачиваются в один счетчик одной строки, доступен. (Вызов **SQLGetInfo** возвращает SQL_BRC_ROLLED_UP бит для типа данных SQL_BATCH_ROW_COUNT.) Первый вызов **SQLMoreResults** будут размещены на число строк свернутая, а второй вызов **SQLMoreResults** будут размещены на результирующем наборе второго **ВЫБЕРИТЕ**.  
  
 Некоторые драйверы доступность счетчиков строк только для явных пакетов, а не для хранимых процедур.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выборка блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Выборка одной строки или блока данных в направлении только вперед|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Извлечение всех или части столбца данных|[Функция SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовка ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Получение выходных параметров с помощью метода SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
