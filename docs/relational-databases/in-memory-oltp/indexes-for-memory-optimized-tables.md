---
title: Индексы для оптимизированных для памяти таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 11/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.component: in-memory-oltp
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eecc5821-152b-4ed5-888f-7c0e6beffed9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: aee77102736555249afa814d21cb0359b8a8e044
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39563408"
---
# <a name="indexes-on-memory-optimized-tables"></a>Индексы для оптимизированных для памяти таблиц
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

В каждой таблице, оптимизированной для памяти, должен использоваться как минимум один индекс, так как индексы объединяют строки. В таблице, оптимизированной для памяти, каждый индекс также будет оптимизирован для памяти. Между оптимизированными для памяти индексами и традиционными индексами в дисковой таблице есть несколько различий:  

- Строки данных хранятся не на страницах. Поэтому нельзя сослаться на коллекции страниц, экстенты, разделы или единицы размещения, чтобы получить все страницы таблицы. Есть понятие страниц для одного из доступных типов индексов, но они хранятся не так, как индексы таблиц на основе дисков. Они не приводят к традиционной фрагментации на странице, поэтому не имеют коэффициента заполнения.
- Изменение индексов в таблицах, оптимизированных для памяти, во время работы с данными никогда не записываются на диск. В журнал транзакций записываются только строки данных и изменения данных. 
- Оптимизированные для памяти индексы перестраиваются, когда база данных переходит в оперативный режим. 

При восстановлении базы данных все индексы в таблицах, оптимизированных для памяти, создаются на основе определений индексов.

Индекс должен быть одним из следующих:  
  
- хэш-индекс;  
- некластеризованный индекс, оптимизированный для памяти (т. е. внутренняя структура сбалансированного дерева по умолчанию). 
  
*Хэш*-индексы для таблиц, оптимизированных для памяти, более подробно рассматриваются в [этом разделе](../../relational-databases/sql-server-index-design-guide.md#hash_index).
*Некластеризованные* индексы для таблиц, оптимизированных для памяти, более подробно рассматриваются в [этом разделе](../../relational-databases/sql-server-index-design-guide.md#inmem_nonclustered_index).  
Индексы*columnstore* рассматриваются в [другой статье](../../relational-databases/indexes/columnstore-indexes-overview.md).  

## <a name="syntax-for-memory-optimized-indexes"></a>Синтаксис индексов, оптимизированных для памяти  
  
Каждая операция CREATE TABLE для таблицы, оптимизированной для памяти, должна включать индекс либо явно посредством INDEX, либо неявно посредством ограничения PRIMAY KEY или UNIQUE.
  
Чтобы быть объявленной с параметром DURABILITY = SCHEMA\_AND_DATA по умолчанию, таблица, оптимизированная для памяти, должна иметь первичный ключ. Предложение PRIMARY KEY NONCLUSTERED в следующей инструкции CREATE TABLE отвечает двум требованиям:  
  
- предоставляет индекс, благодаря чему выполняется требование наличия по крайней мере одного индекса в инструкции CREATE TABLE;  
- предоставляет первичный ключ, необходимый для предложения SCHEMA\_AND_DATA.  

    ```sql
    CREATE TABLE SupportEvent  
    (  
        SupportEventId   int NOT NULL  
            PRIMARY KEY NONCLUSTERED,  
        ...  
    )  
        WITH (  
            MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA\_AND_DATA);  
    ```
> [!NOTE]  
> В [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] действует ограничение в 8 индексов на таблицу, оптимизированную для памяти, или тип таблицы. Начиная с версии [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] и в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] больше не применяются ограничения числа индексов для таблиц, оптимизированных для памяти, и типов таблиц.
  
### <a name="code-sample-for-syntax"></a>Пример кода для синтаксиса  
  
В этом подразделе приведен блок кода Transact-SQL, демонстрирующий синтаксис для создания различных индексов в таблице, оптимизированной для памяти. Этот код демонстрирует следующее.  
  
1. Создание оптимизированной для памяти таблицы.  
2. Используйте инструкции ALTER TABLE для добавления двух индексов.  
3. Вставьте (INSERT) несколько строк данных.  
   
    ```sql
    DROP TABLE IF EXISTS SupportEvent;  
    go  

    CREATE TABLE SupportEvent  
    (  
        SupportEventId   int               not null   identity(1,1)  
        PRIMARY KEY NONCLUSTERED,  

        StartDateTime        datetime2     not null,  
        CustomerName         nvarchar(16)  not null,  
        SupportEngineerName  nvarchar(16)      null,  
        Priority             int               null,  
        Description          nvarchar(64)      null  
    )  
        WITH (  
        MEMORY_OPTIMIZED = ON,  
        DURABILITY = SCHEMA\_AND_DATA);  
    go  
        
        --------------------  
        
    ALTER TABLE SupportEvent  
        ADD CONSTRAINT constraintUnique_SDT_CN  
        UNIQUE NONCLUSTERED (StartDateTime DESC, CustomerName);  
    go  

    ALTER TABLE SupportEvent  
        ADD INDEX idx_hash_SupportEngineerName  
        HASH (SupportEngineerName) WITH (BUCKET_COUNT = 64);  -- Nonunique.  
    go  
        
        --------------------  
        
    INSERT INTO SupportEvent  
        (StartDateTime, CustomerName, SupportEngineerName, Priority, Description)  
        VALUES  
        ('2016-02-23 13:40:41:123', 'Abby', 'Zeke', 2, 'Display problem.'     ),  
        ('2016-02-24 13:40:41:323', 'Ben' , null  , 1, 'Cannot find help.'    ),  
        ('2016-02-25 13:40:41:523', 'Carl', 'Liz' , 2, 'Button is gray.'      ),  
        ('2016-02-26 13:40:41:723', 'Dave', 'Zeke', 2, 'Cannot unhide column.');  
    go 
    ``` 
  
## <a name="duplicate-index-key-values"></a>Повторяющиеся значения ключа индекса

Повторяющиеся значения ключа индекса могут повлиять на производительность операций с оптимизированными для памяти таблицами. Большое число повторяющихся значений (например, более 100) делают обслуживание индекса неэффективным, так как для большинства операций с индексом требуется проход по повторяющимся цепочкам. Это явление можно наблюдать при выполнении операций `INSERT`, `UPDATE` и `DELETE` в таблицах, оптимизированных для памяти. 

Особенно наглядно эта проблема проявляется в случае с хэш-индексами из-за более низких затрат на каждую операцию и конфликтов больших повторяющихся цепочек с цепочкой хэш-конфликтов. Чтобы уменьшить число повторяющихся значений в индексе, используйте некластеризованный индекс и добавьте дополнительные столбцы (например, из первичного ключа) в конец ключа индекса. Дополнительные сведения о хэш-конфликтах см. в разделе о [хэш-индексах для таблиц, оптимизированных для памяти](../../relational-databases/sql-server-index-design-guide.md#hash_index).

Например, рассмотрим таблицу `Customers` с первичным ключом в `CustomerId` и индексом в столбце `CustomerCategoryID`. Как правило, в каждой категории есть несколько клиентов, поэтому для отдельного ключа в индексе по столбцу "Код категории клиента" значения повторяются. В такой ситуации рекомендуется использовать некластеризованный индекс в `(CustomerCategoryID, CustomerId)`. Этот индекс можно использовать для запросов с предикатом, включающим столбец `CustomerCategoryID`. Он не содержит повторяющихся значений и поэтому не снижает эффективность обслуживания индекса.

В следующем запросе показано среднее число повторяющихся значений ключа индекса для индекса `CustomerCategoryID` в таблице `Sales.Customers`в образце базы данных [WideWorldImporters](../../sample/world-wide-importers/wide-world-importers-documentation.md).

```sql
SELECT AVG(row_count) FROM
    (SELECT COUNT(*) AS row_count 
        FROM Sales.Customers
        GROUP BY CustomerCategoryID) a
```

Чтобы вычислить среднее число повторяющихся ключей индекса для таблицы и индекса, замените `Sales.Customers` именем таблицы, а `CustomerCategoryID` — списком столбцов ключей индекса.

## <a name="comparing-when-to-use-each-index-type"></a>Сравнение с использованием каждого типа индекса  
  
Наиболее подходящий тип индекса определяется характером конкретных запросов.  

При реализации оптимизированных для памяти таблиц в существующем приложении действует общая рекомендация — начинать с некластеризованных индексов, так как их возможности больше похожи на возможности традиционных кластеризованных и некластеризованных индексов в таблицах на диске. 
  
### <a name="recommendations-for-nonclustered-index-use"></a>Рекомендации по использованию некластеризованных индексов  
  
Некластеризованный индекс является предпочтительным по сравнению с хэш-индексом, когда:  
  
- Запросы содержат предложение `ORDER BY` для индексированного столбца.  
- Используются запросы, в которых проверяются только первые столбцы для индекса, состоящего из нескольких столбцов.  
- Запросы проверяют индексированный столбец с помощью предложения `WHERE`, в котором содержится:  
  - неравенство `WHERE StatusCode != 'Done'`;  
  - проверка диапазонов значений `WHERE Quantity >= 100`.  
  
Во всех следующих инструкциях SELECT некластеризованный индекс является предпочтительным по сравнению с хэш-индексом:  

```sql
SELECT CustomerName, Priority, Description 
FROM SupportEvent  
WHERE StartDateTime > DateAdd(day, -7, GetUtcDate());  
    
SELECT CustomerName, Priority, Description 
FROM SupportEvent  
WHERE CustomerName != 'Ben';  
    
SELECT StartDateTime, CustomerName  
FROM SupportEvent  
ORDER BY StartDateTime;  
    
SELECT CustomerName  
FROM SupportEvent  
WHERE StartDateTime = '2016-02-26';  
```
  
### <a name="recommendations-for-hash-index-use"></a>Рекомендации по использованию хэш-индексов   
  
[Хэш-индексы](../../relational-databases/sql-server-index-design-guide.md#hash_index) в основном используются для уточняющих запросов, а не для проверок диапазона.

Хэш-индекс предпочтительнее некластеризованного, если при запросах используются предикаты равенства, а предложение `WHERE` сопоставляет все ключевые столбцы индекса, как показано в следующем примере:  
  
```sql
SELECT CustomerName 
FROM SupportEvent  
WHERE SupportEngineerName = 'Liz';
```  

### <a name="multi-column-index"></a>Индекс для нескольких столбцов  
  
Для нескольких столбцов может использоваться как некластеризованный индекс, так и хэш-индекс. Предположим, что индекс включает столбцы col1 и col2. Учитывая следующую инструкцию `SELECT`, для оптимизатора запросов применим только некластеризованный индекс:  
  
```sql
SELECT col1, col3  
FROM MyTable_memop  
WHERE col1 = 'dn';  
```

Для хэш-индекса в предложении `WHERE` должен быть задан тест на равенство для каждого столбца в ключе. Без него хэш-индекс не будет полезен для оптимизатора запросов.  
  
Тип индекса также не будет иметь значения, если предложение `WHERE` определяет только второй столбец ключа индекса.  

### <a name="summary-table-to-compare-index-use-scenarios"></a>Сводная таблица, в которой сравниваются сценарии использования индексов  
  
В следующей таблице перечислены все операции, поддерживаемые различными типами индексов. В таблице *Да* означает, что индекс может эффективно обслуживать запрос, а *Нет* — что не может. 
  
| Операция | Оптимизированная для памяти, <br/> Хэш | Оптимизированная для памяти, <br/> некластеризованный | Дисковая <br/> (не)кластеризованная |  
| :-------- | :--------------------------- | :----------------------------------- | :------------------------------------ |  
| Сканирование индекса, получение всех строк таблицы. | Да | Да | Да |  
| Поиск по индексу с использованием предикатов равенства (=). | Да <br/> (Требуется полный ключ.) | Да  | Да |  
| Поиск по индексу с использованием неравенства и предикатов диапазона <br/> (>, <, <=, >=, `BETWEEN`). | нет <br/> (Результаты в сканировании индекса.) | Да <sup>1</sup> | Да |  
| Получение строк в порядке сортировки, соответствующем определению индекса. | нет | Да | Да |  
| Получение строк в порядке сортировки, соответствующем обратному определению индекса. | нет | нет | Да |  

<sup>1</sup> Для некластеризованного индекса, оптимизированного для памяти, полный ключ не требуется.  

## <a name="automatic-index-and-statistics-management"></a>Автоматическое управление индексами и статистикой

Используйте такие решения, как [Адаптивная дефрагментация индексов](http://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag), чтобы автоматически управлять дефрагментацией индексов и обновлениями статистики для одной базы данных или нескольких. Эта процедура автоматически выбирает, следует ли перестроить или реорганизовать индекс, сверяясь с уровнем фрагментации и другими параметрами, и обновляет статистику на основе линейных пороговых значений.

## <a name="Additional_Reading"></a> См. также:   
 [Руководство по проектированию индексов SQL Server](../../relational-databases/sql-server-index-design-guide.md)   
 [Хэш-индексы для таблиц, оптимизированных для памяти](../../relational-databases/sql-server-index-design-guide.md#hash_index)   
 [Некластеризованные индексы для таблиц, оптимизированных для памяти](../../relational-databases/sql-server-index-design-guide.md#inmem_nonclustered_index)    
 [Адаптивная дефрагментация индексов](http://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag)  
