---
title: Выполнение определяемых пользователем функций | Документация Майкрософт
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: udf
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- invoking user-defined functions
- user-defined functions [SQL Server], executing
ms.assetid: 0de7744d-9b73-463f-ae80-e31a020004b5
caps.latest.revision: 35
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 5e45123eb6259601172afb084430690c84c0def3
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39539724"
---
# <a name="execute-user-defined-functions"></a>Выполнение определяемых пользователем функций
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
  Выполните определяемую пользователем функцию с помощью Transact-SQL.
  

> **Примечание.** Дополнительные сведения см. в разделах, посвященных  [определяемым пользователем функциям](user-defined-functions.md) и [созданию функций (Transact SQL](../../t-sql/statements/create-function-transact-sql.md) . 
  
 
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 В Transact-SQL параметры могут передаваться через *value* или с помощью @*parameter_name*=*value.* . Параметр не является частью транзакции, поэтому если он изменился в транзакции, которая впоследствии подверглась откату, то прежнее значение параметра не восстанавливается. Возвращаемым вызывающему значением всегда является то значение, которое существует на момент выхода из модуля.  
  
###  <a name="Security"></a> безопасность  
  
 На выполнение инструкции [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md) разрешения не требуются. Однако **необходимы** разрешения на защищаемые объекты, на которые ссылается командная строка в инструкции EXECUTE. Например, если строка содержит инструкцию [INSERT](../../t-sql/statements/insert-transact-sql.md) , вызывающий инструкцию EXECUTE пользователь должен иметь разрешение INSERT на целевую таблицу. Разрешения проверяются в месте нахождения инструкции EXECUTE, даже если она содержится внутри модуля. Дополнительные сведения см. в разделе [EXECUTE (Transact-SQL)](../../t-sql/language-elements/execute-transact-sql.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
### <a name="example"></a>Пример 
  
В этом примере используется скалярная функция `ufnGetSalesOrderStatusText` , которая доступна в большинстве выпусков `AdventureWorks`.  Функция предназначена для возврата текстового значения для состояния продаж из заданного целого числа.  Измените пример, передавая целые числа от 1 до 7 в параметр **\@Status** .
  
~~~tsql
USE [AdventureWorks2016CTP3]
GO  

-- Declare a variable to return the results of the function. 
DECLARE @ret nvarchar(15);   

-- Execute the function while passing a value to the @status parameter
EXEC @ret = dbo.ufnGetSalesOrderStatusText 
    @Status = 5; 

-- View the returned value.  The Execute and Select statements must be executed at the same time.  
SELECT N'Order Status: ' + @ret; 

-- Result:
-- Order Status: Shipped
~~~
  
  
  
