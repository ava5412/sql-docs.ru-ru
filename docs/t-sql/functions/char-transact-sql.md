---
title: CHAR (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- char_TSQL
- char
dev_langs:
- TSQL
helpviewer_keywords:
- converting int ACSII code to character
- control characters
- tab
- ASCII conversions
- CHAR function
- carriage return
- inserting control characters
- characters [SQL Server], control
- line feed
- printing ASCII values
ms.assetid: 955afe94-539c-465d-af22-16ec45da432a
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: e466a39e0d00a8be29a74028dd54a599da53f1ac
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39453788"
---
# <a name="char-transact-sql"></a>CHAR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция преобразует код ASCII **int** в значение символа.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CHAR ( integer_expression )  
```  
  
## <a name="arguments"></a>Аргументы  
*integer_expression*  
Целое число от 0 до 255. `CHAR` возвращает значение `NULL` для целочисленных выражений, выходящих за пределы этого диапазона.
  
## <a name="return-types"></a>Типы возвращаемых данных
**char(1)**
  
## <a name="remarks"></a>Remarks  
Функция `CHAR` может использоваться для вставки управляющих символов в символьные строки. В этой таблице показаны некоторые часто используемые управляющие символы.
  
|Управляющий символ|Значение|  
|---|---|
|Вкладка|**char(9)**|  
|Перевод строки|**char(10)**|  
|Возврат каретки|**char(13)**|  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-ascii-and-char-to-print-ascii-values-from-a-string"></a>A. Использование ASCII и CHAR для отображения значений ASCII из строки  
В этом примере отображается значение ASCII и символ для каждого символа в строке `New Moon`.
  
```sql
SET TEXTSIZE 0;  
-- Create variables for the character string and for the current   
-- position in the string.  
DECLARE @position int, @string char(8);  
-- Initialize the current position and the string variables.  
SET @position = 1;  
SET @string = 'New Moon';  
WHILE @position <= DATALENGTH(@string)  
   BEGIN  
   SELECT ASCII(SUBSTRING(@string, @position, 1)),   
      CHAR(ASCII(SUBSTRING(@string, @position, 1)))  
   SET @position = @position + 1  
   END;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------- -
78          N  
----------- -  
101         e  
----------- -  
119         w  
----------- -  
32  
----------- -  
77          M  
----------- -  
111         o  
----------- -  
111         o  
----------- - 
110         n  
```
  
### <a name="b-using-char-to-insert-a-control-character"></a>Б. Использование функции CHAR для вставки управляющего символа  
В этом примере используется выражение `CHAR(13)`, чтобы отображать имя и адрес электронной почты сотрудника в отдельных строках, когда результаты запроса возвращаются в виде текста. В этом примере используется база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
SELECT p.FirstName + ' ' + p.LastName, + CHAR(13)  + pe.EmailAddress   
FROM Person.Person p JOIN Person.EmailAddress pe  
ON p.BusinessEntityID = pe.BusinessEntityID  
AND p.BusinessEntityID = 1;  
GO  
```
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Ken Sanchez
ken0@adventure-works.com
  
(1 row(s) affected)
```
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-ascii-and-char-to-print-ascii-values-from-a-string"></a>В. Использование ASCII и CHAR для отображения значений ASCII из строки  
В этом примере используется набор символов ASCII. В нем возвращается значение символа для шести разных числовых значений символов ASCII.
  
```sql
SELECT CHAR(65) AS [65], CHAR(66) AS [66],   
CHAR(97) AS [97], CHAR(98) AS [98],   
CHAR(49) AS [49], CHAR(50) AS [50];  
```
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
65   66   97   98   49   50  
---- ---- ---- ---- ---- ----  
A    B    a    b    1    2  
```
  
### <a name="d-using-char-to-insert-a-control-character"></a>Г. Использование функции CHAR для вставки управляющего символа  
В этом примере используется `CHAR(13)` для получения сведений из файла sys.databases в отдельных строках, когда результаты запроса возвращаются в виде текста.
  
```sql
SELECT name, 'was created on ', create_date, CHAR(13), name, 'is currently ', state_desc   
FROM sys.databases;  
GO  
```
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
name     create_date    name    state_desc  
------------------------------------------------------------  
master                   was created on  2003-04-08 09:13:36.390   
master                   is currently  ONLINE  
tempdb                   was created on  2014-01-10 17:24:24.023   
tempdb                   is currently  ONLINE  
AdventureWorksPDW2012    was created on  2014-05-07 09:05:07.083 
AdventureWorksPDW2012    is currently  ONLINE  
```
  
## <a name="see-also"></a>См. также раздел
 [ASCII (Transact-SQL)](../../t-sql/functions/ascii-transact-sql.md)  
 [NCHAR (Transact-SQL)](../../t-sql/functions/nchar-transact-sql.md)  
 [UNICODE (Transact-SQL)](../../t-sql/functions/unicode-transact-sql.md)  
 [+ (объединение строк) (Transact-SQL)](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
 [Строковые функции (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)
  
  

