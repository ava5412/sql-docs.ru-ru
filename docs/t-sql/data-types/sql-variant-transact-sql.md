---
title: "sql_variant (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql_variant
- sql_variant_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sql_variant comparisons
- storing data [SQL Server], sql_variant
- sql_variant data type
- storage [SQL Server], sql_variant
ms.assetid: 01229779-8bc1-4c7d-890a-8246d4899250
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4eb946d5b6ed5a9c6d33789166327bd2dd25d7c1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="sqlvariant-transact-sql"></a>sql_variant (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Тип данных, хранящий значения различных типов данных, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)),[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
sql_variant  
```  
  
## <a name="remarks"></a>Замечания  
**sql_variant** может использоваться в столбцах, параметрах, переменных и возвращаемых значений определяемых пользователем функций. **sql_variant** позволяет этим объектам баз данных поддерживать значения других типов данных.
  
Столбец типа **sql_variant** могут содержать строки различных типов данных. Например, столбец, определенный как **sql_variant** можно хранить **int**, **двоичных**, и **char** значения.
  
**sql_variant** Максимальная длина составляет 8 016 байт. Сюда входят сведения базового типа и значения базового типа. Максимальная длина значения соответствующего базового типа составляет 8 000 байт.
  
Объект **sql_variant** тип данных сначала должен быть приведен к ее значению базового типа данных до участия в операциях, как сложение и вычитание.
  
**sql_variant** может быть присвоено значение по умолчанию. Этот тип данных в качестве значения может содержать значение NULL, однако значению NULL не будет соответствовать базовый тип. Кроме того **sql_variant** не может иметь другой **sql_variant** как базовый тип.
  
Уникальный, первичный или внешний ключ может содержать столбцы типа **sql_variant**, но общая длина значений данных, составляющих ключ определенной строки не превышает максимальную длину индекса. Эта длина составляет 900 байт.
  
Таблица может иметь любое количество **sql_variant** столбцов.
  
**sql_variant** не может использоваться в функции CONTAINSTABLE и FREETEXTTABLE.
  
ODBC не поддерживает полностью **sql_variant**. Поэтому запросы **sql_variant** столбцы возвращаются в виде двоичных данных, при использовании поставщика Microsoft OLE DB для ODBC (MSDASQL). Например **sql_variant** столбец, содержащий данных символьной строки «PS2091» возвращается в виде 0x505332303931.
  
## <a name="comparing-sqlvariant-values"></a>Сравнение значений sql_variant  
**Sql_variant** принадлежит тип данных в верхнюю часть списка иерархии типов данных для преобразования. Для **sql_variant** сравнения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных тип иерархии разбивается на семейства типов.
  
|Иерархия типов данных|Семейство типов данных|  
|---|---|
|**sql_variant**|**sql_variant**|  
|**datetime2**|Дата и время|  
|**datetimeoffset**|Дата и время|  
|**datetime**|Дата и время|  
|**smalldatetime**|Дата и время|  
|**date**|Дата и время|  
|**time**|Дата и время|  
|**float**|Приблизительное числовое значение|  
|**real**|Приблизительное числовое значение|  
|**decimal**|Точное числовое значение|  
|**money**|Точное числовое значение|  
|**smallmoney**|Точное числовое значение|  
|**bigint**|Точное числовое значение|  
|**int**|Точное числовое значение|  
|**smallint**|Точное числовое значение|  
|**tinyint**|Точное числовое значение|  
|**bit**|Точное числовое значение|  
|**nvarchar**|Юникод|  
|**nchar**|Юникод|  
|**varchar**|Юникод|  
|**char**|Юникод|  
|**varbinary**|Двоичный|  
|**binary**|Двоичный|  
|**uniqueidentifier**|**Uniqueidentifier**|  
  
Следующие правила применяются к **sql_variant** сравнения:
-   Когда **sql_variant** сравниваются значения разные базовые типы и базовым типам данных относятся к разным семействам, значение, семейство типов которого находится выше в иерархии, считается большего из двух значений.  
-   Когда **sql_variant** сравниваются значения разных базовых типов данных и типов данных, находящихся в одном семействе типов данных, значение, базовый тип данных находится ниже в иерархии, неявно преобразуется в тип данных и затем будет выполнено сравнение.  
-   Когда **sql_variant** значения **char**, **varchar**, **nchar**, или **nvarchar** типы данных: по сравнению с, их параметры сортировки сначала сравниваются на основе следующих критериев: LCID, версия кода языка, флаги сравнения и сортировки по идентификатору. Каждый из этих критериев сравнивается как целочисленное значение в приведенном порядке. Если все эти критерии равны, то сами строковые значения сравниваются в соответствии с параметрами сортировки.  
  
## <a name="converting-sqlvariant-data"></a>Преобразование данных типа sql_variant  
При обработке **sql_variant** тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает неявное преобразование объектов других типов данных для **sql_variant** типа. Тем не менее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает неявные преобразования из **sql_variant** данных в объект с другим типом данных.
  
## <a name="restrictions"></a>Ограничения  
В следующей таблице перечислены типы значений, которые не могут храниться с помощью **sql_variant**:
  
|||  
|-|-|  
|**varchar(max)**|**varbinary(max)**|  
|**nvarchar(max)**|**xml**|  
|**text**|**ntext**|  
|**image**|**rowversion** (**timestamp**)|  
|**sql_variant**|**geography**|  
|**hierarchyid**|**geometry**|  
|Определяемые пользователем типы|**datetimeoffset**|  
  
## <a name="see-also"></a>См. также:
[Функции CAST и CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[SQL_VARIANT_PROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sql-variant-property-transact-sql.md)
  
  
