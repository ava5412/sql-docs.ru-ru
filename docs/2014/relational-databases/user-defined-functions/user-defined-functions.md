---
title: Определяемые пользователем функции | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], components
- user-defined functions [SQL Server], about user-defined functions
ms.assetid: d7ddafab-f5a6-44b0-81d5-ba96425aada4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1d8b8569a35a67d2700c0ce48c9c1cd4b29da7e1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427473"
---
# <a name="user-defined-functions"></a>Определяемые пользователем функции
  Аналогично функциям в языках программирования,  определяемые пользователем функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представляют собой подпрограммы, которые принимают параметры, выполняют действие, например, сложные вычисления, и возвращают результат этого действия в виде значения. Возвращаемое значение может быть либо единичным скалярным значением, либо результирующим набором.  
  
 **В этом разделе**  
  
 [Преимущества определяемых пользователем функций](#Benefits)  
  
 [Типы функций](#FunctionTypes)  
  
 [Рекомендации](#Guidelines)  
  
 [Инструкции, допустимые в функциях](#ValidStatements)  
  
 [Привязанные к схеме функции](#SchemaBound)  
  
 [Указание параметров](#Parameters)  
  
 [Связанные задачи](#Tasks)  
  
##  <a name="Benefits"></a> Преимущества определяемых пользователем функций  
 Определяемые пользователем функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляют следующие преимущества.  
  
-   Делают возможным модульное программирование.  
  
     Можно, однажды создав функцию, сохранить ее в базе данных, а затем любое число раз вызывать из своей программы. Определяемые пользователем функции могут быть изменены независимо от исходного кода программы.  
  
-   Позволяют ускорить выполнение.  
  
     Как и хранимые процедуры, определяемые пользователем функции [!INCLUDE[tsql](../../includes/tsql-md.md)] снижают стоимость компиляции кода [!INCLUDE[tsql](../../includes/tsql-md.md)], кэшируя и повторно используя планы выполнения. Это означает, что для определяемых пользователем функций нет необходимости выполнять повторный синтаксический анализ и оптимизацию при каждом вызове, что значительно ускоряет их выполнение.  
  
     Функции CLR дают значительное преимущество в производительности по сравнению с функциями [!INCLUDE[tsql](../../includes/tsql-md.md)] для вычислительных задач, работы со строками и бизнес-логикой. Функции [!INCLUDE[tsql](../../includes/tsql-md.md)] лучше подходят для логики с интенсивным доступом к данным.  
  
-   Позволяют уменьшить сетевой трафик.  
  
     Операция, которая фильтрует данные на основе какого-нибудь сложного ограничения и не может быть выражена одним скалярным выражением, может быть реализована в виде функции. Ее можно вызвать из предложения WHERE, чтобы уменьшить число строк, возвращаемых клиенту.  
  
> [!NOTE]  
>  Определяемые пользователем функции [!INCLUDE[tsql](../../includes/tsql-md.md)] в запросах могут выполняться только как один поток (план последовательного выполнения).  
  
##  <a name="FunctionTypes"></a> Типы функций  
 Скалярная функция  
 Пользовательские скалярные функции возвращают одно значение типа данных, заданного в предложении RETURNS. Встроенная скалярная функция не имеет тела, скалярное значение является результатом одной инструкции. Скалярная функция из нескольких инструкций имеет текст, ограниченное блоком BEGIN...END, и содержит последовательность инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , возвращающих одно значение. Тип возвращаемого значения может быть любым типом данных, за исключением `text`, `ntext`, `image`, `cursor`, и `timestamp`.  
  
 Функции с табличными значениями  
 Определяемые пользователем возвращающие табличные значения функции возвращают `table` тип данных. Встроенная функция с табличным значением не имеет текста, таблица является результирующим набором одной инструкции.  
  
 Системные функции  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет множество системных функций для выполнения различных операций. Их нельзя изменить. Дополнительные сведения см. в разделах [Встроенные функции (Transact-SQL)](/sql/t-sql/functions/functions), [Системные хранимые функции (Transact-SQL)](/sql/relational-databases/system-functions/system-functions-for-transact-sql) и [Динамические административные представления и функции (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views).  
  
##  <a name="Guidelines"></a> Рекомендации  
 Ошибки [!INCLUDE[tsql](../../includes/tsql-md.md)], которые вызывают отмену инструкции и продолжение выполнения со следующей инструкции в модуле (например в триггере или хранимой процедуре), внутри функций обрабатываются иначе. В функциях такие ошибки вызывают остановку выполнения функции. Это вызывает отмену инструкции, вызвавшей функцию.  
  
 Инструкции в блоке BEGIN...END не могут иметь каких-либо побочных эффектов. Побочными эффектами функций называются любые постоянные изменения состояния ресурса, область которого лежит за пределами функции, например изменение таблицы базы данных. Инструкции внутри функции могут изменять только локальные по отношению к этой функции объекты, например локальные курсоры или переменные. Изменения таблиц баз данных, операции с курсорами, не являющимися локальными для данной функции, отправка электронной почты, попытка изменения каталога, формирование результирующего набора, возвращаемого пользователю — это примеры действий, выполнение которых внутри функции невозможно.  
  
> [!NOTE]  
>  Если инструкция CREATE FUNCTION создает побочные эффекты в отношении ресурсов, которые не существуют во время применения инструкции CREATE FUNCTION, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет эту инструкцию. Однако [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не выполняет эту функцию при ее вызове.  
  
 Число раз, когда указанная в запросе функция будет фактически выполнена, может различаться для разных планов выполнения, построенных оптимизатором. Примером является функция, вызываемая вложенным запросом в предложении WHERE. Число раз, когда вложенный запрос и его функция будут выполнены, может различаться для разных путей доступа, выбираемых оптимизатором.  
  
##  <a name="ValidStatements"></a> Инструкции, допустимые в функциях  
 К типам инструкций, допустимым внутри функций, относятся следующие.  
  
-   Инструкции DECLARE, используемые для определения переменных и курсоров, локальных для данной функции.  
  
-   Присвоение значений объектам, локальным для данной функции, например присвоение значений скалярным и табличным локальным переменным с помощью инструкции SET.  
  
-   Операции над курсорами, обращающиеся к локальным курсорам и выполняющие их объявление, открытие, закрытие и освобождение внутри функции. Инструкции FETCH, возвращающие данные клиенту, запрещены. Разрешены только инструкции FETCH, присваивающие значения локальным переменным с помощью предложения INTO.  
  
-   Инструкции управления потоком, за исключением инструкций TRY...CATCH.  
  
-   Инструкции SELECT, содержащие списки выборки с выражениями, присваивающими значения переменным, локальным для данной функции.  
  
-   Инструкции UPDATE, INSERT и DELETE, изменяющие табличные переменные, локальные для функции.  
  
-   Инструкции EXECUTE, вызывающие расширенную хранимую процедуру.  
  
### <a name="built-in-system-functions"></a>Встроенные системные функции  
 Следующие недетерминированные встроенные функции могут быть использованы в определяемых пользователем функциях языка Transact-SQL.  
  
|||  
|-|-|  
|CURRENT_TIMESTAMP|@@MAX_CONNECTIONS|  
|GET_TRANSMISSION_STATUS|@@PACK_RECEIVED|  
|GETDATE|@@PACK_SENT|  
|GETUTCDATE|@@PACKET_ERRORS|  
|@@CONNECTIONS|@@TIMETICKS|  
|@@CPU_BUSY|@@TOTAL_ERRORS|  
|@@DBTS|@@TOTAL_READ|  
|@@IDLE|@@TOTAL_WRITE|  
|@@IO_BUSY||  
  
 Следующие недетерминированные встроенные функции в определяемых пользователем функциях на языке Transact-SQL использовать нельзя.  
  
|||  
|-|-|  
|NEWID|RAND|  
|NEWSEQUENTIALID|TEXTPTR|  
  
 Список детерминированных и недетерминированных встроенных системных функций см. в разделе [Детерминированные и недетерминированные функции](../user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
##  <a name="SchemaBound"></a> Привязанные к схеме функции  
 Инструкция CREATE FUNCTION поддерживает предложение SCHEMABINDING, позволяющее привязать функцию к схеме каких-либо объектов, на которые она ссылается, например таблиц, представлений и других пользовательских функций. Попытка изменения или удаления любого объекта, к которому обращается привязанная к схеме функция, приводит к ошибке.  
  
 Перед указанием предложения SCHEMABINDING в инструкции CREATE FUNCTION нужно соблюсти следующие условия.  
  
-   Все представления и пользовательские функции, к которым обращается функция, должны быть привязаны к схеме.  
  
-   Все объекты, к которым обращается функция, должны находиться в той же базе данных, что и функция. Обращение к объектам должно производиться по однокомпонентным либо двухкомпонентным именам.  
  
-   Для всех объектов (таблиц, представлений и пользовательских функций), к которым обращается функция, должно быть получено разрешение REFERENCES.  
  
 Для удаления привязки к схеме можно использовать инструкцию ALTER FUNCTION. В инструкции ALTER FUNCTION следует переопределить функцию без указания предложения WITH SCHEMABINDING.  
  
##  <a name="Parameters"></a> Указание параметров  
 Пользовательская функция может принимать 0 или более входных параметров и возвращать либо скалярное, либо табличное значение. Максимальное число входных параметров для функции равно 1024. Если для параметра функции установлено значение по умолчанию, необходимо указать ключевое слово DEFAULT при вызове функции, чтобы получить установленное по умолчанию значение. Это поведение отличается от использования параметров со значениями по умолчанию в пользовательских хранимых процедурах, в которых пропущенный параметр также принимает значение по умолчанию. В определяемых пользователями функциях не поддерживаются выходные параметры.  
  
##  <a name="Tasks"></a> Связанные задачи  
  
|||  
|-|-|  
|**Описание задачи**|**Раздел**|  
|Описывает, как создать определяемую пользователем функцию Transact-SQL.|[Создание определяемых пользователем функций (ядро СУБД)](../user-defined-functions/create-user-defined-functions-database-engine.md)|  
|Описывает, как создать функции CLR.|[Создание функций CLR](../user-defined-functions/create-clr-functions.md)|  
|Описывает, как создать определяемую пользователем агрегатную функцию.|[Создание пользовательских агрегатных функций](../user-defined-functions/create-user-defined-aggregates.md)|  
|Описывает, как изменить определяемую пользователем функцию Transact-SQL.|[Изменение пользовательских функций](../user-defined-functions/user-defined-functions.md)|  
|Описывает, как удалить определяемую пользователем функцию.|[Удаление пользовательских функций](../user-defined-functions/delete-user-defined-functions.md)|  
|Описывает, как создать определяемую пользователем функцию выполнения.|[Выполнение пользовательских функций](../user-defined-functions/execute-user-defined-functions.md)|  
|Описывает, как переименовать определяемую пользователем функцию|[Переименование пользовательских функций](../user-defined-functions/rename-user-defined-functions.md)|  
|Описывает, как просмотреть определяемую пользователем функцию.|[Просмотр пользовательских функций](view-user-defined-functions.md)|  
  
  
