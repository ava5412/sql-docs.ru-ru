---
title: ALL (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- ALL_TSQL
- ALL
dev_langs:
- TSQL
helpviewer_keywords:
- single-column set of values [SQL Server]
- ALL (Transact-SQL)
ms.assetid: 4b0c002e-1ffd-4425-a980-11fdc1f24af7
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 13b6ce54c65aaeeeb9c46836b79e6879f17915bf
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36251616"
---
# <a name="all-transact-sql"></a>ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Сравнивает скалярное значение с набором значений, состоящим из одного столбца.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
scalar_expression { = | <> | != | > | >= | !> | < | <= | !< } ALL ( subquery )  
```  
  
## <a name="arguments"></a>Аргументы  
 *scalar_expression*  
 Любое допустимое выражение [expression](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Оператор сравнения.  
  
 *subquery*  
 Вложенный запрос, возвращающий результирующий набор, состоящий из одного столбца. Тип данных возвращаемого столбца должен совпадать с типом данных аргумента *scalar_expression*.  
  
 Ограниченная инструкция SELECT, в которой запрещено предложение ORDER BY, а также ключевое слово INTO.  
  
## <a name="result-types"></a>Типы результата  
 **Boolean**  
  
## <a name="result-value"></a>Значение результата  
 Возвращает TRUE, если заданное сравнение возвращает TRUE для всех пар (*scalar_expression ***,*** x)*, где *x* является значением из набора строк, состоящего из одного столбца; в противном случае возвращает FALSE.  
  
## <a name="remarks"></a>Remarks  
 Если аргумент *scalar_expression* установлен в значение ALL, будет выполнено сравнение каждого значения, возвращаемого вложенным запросом. Например, если вложенный запрос возвращает значения 2 и 3, то при *scalar_expression* <= ALL будет возвращаться TRUE для значения *scalar_expression*, равного 2. Если вложенный запрос возвращает значения 2 и 3, то при *scalar_expression* = ALL (subquery) будет возвращаться FALSE, так как некоторые значения вложенного запроса (значение 3) не отвечают критериям этого выражения.  
  
 Инструкции, которым необходим аргумент *scalar_expression* для сравнения каждого значения, возвращенного вложенным запросом, перечислены в разделе [SOME &#124; ANY (Transact-SQL)](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 В этом разделе имеются ссылки на выражение ALL при его использовании совместно с вложенными запросами. ALL может также использоваться с инструкциями [UNION](../../t-sql/language-elements/set-operators-union-transact-sql.md) и [SELECT](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере показано создание хранимой процедуры, определяющей, могут ли в течение заданного количества дней быть выполнены все части заказа с указанным идентификатором `SalesOrderID` из базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. В этом примере вложенный запрос используется для создания списка числовых значений `DaysToManufacture` для всех заказов с указанным идентификатором `SalesOrderID`, после чего происходит проверка того, что время производства всех заказов (`DaysToManufacture`) находится в пределах указанного числа дней.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE DaysToBuild @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays >= ALL  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'All items for this order can be manufactured in specified number of days or less.'  
ELSE   
PRINT 'Some items for this order cannot be manufactured in specified number of days or less.' ;  
  
```  
  
 Для проверки этой процедуры выполните ее, используя заказ `SalesOrderID 49080`. В него входит один компонент, производство которого занимает `2` дня, и два компонента, производство которых занимает 0 дней. Первая из нижеследующих инструкций отвечает этим критериям. Второй запрос этим критериям не отвечает.  
  
```  
EXECUTE DaysToBuild 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in specified number of days or less.`  
  
```  
EXECUTE DaysToBuild 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Some items for this order cannot be manufactured in specified number of days or less.`  
  
## <a name="see-also"></a>См. также:  
 [CASE (Transact-SQL)](../../t-sql/language-elements/case-transact-sql.md)   
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [LIKE (Transact-SQL)](../../t-sql/language-elements/like-transact-sql.md)   
 [Операторы (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)   
 [IN (Transact-SQL)](../../t-sql/language-elements/in-transact-sql.md)  
  
  
