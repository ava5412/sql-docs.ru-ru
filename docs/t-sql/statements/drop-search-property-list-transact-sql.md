---
title: DROP SEARCH PROPERTY LIST (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP_SEARCH_PROPERTY_LIST_TSQL
- DROP SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- DROP SEARCH PROPERTY LIST statement
- search property lists [SQL Server], dropping
- search property lists [SQL Server], deleting
ms.assetid: 7c7ce52a-6b77-4a1c-9abf-d5feb664bea8
caps.latest.revision: 23
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0f05ebd72155b66ece1e1a125d519b076a404e24
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785711"
---
# <a name="drop-search-property-list-transact-sql"></a>DROP SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет список свойств из текущей базы данных, если список свойств поиска в настоящее время не связан с каким-либо полнотекстовым индексом в базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP SEARCH PROPERTY LIST property_list_name  
;  
```  
  
## <a name="arguments"></a>Аргументы  
 *property_list_name*  
 Имя списка свойств поиска для удаления. *property_list_name* — это идентификатор.  
  
 Чтобы просмотреть имена существующих списков свойств, используйте представление каталога [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md) следующим образом:  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
## <a name="remarks"></a>Remarks  
 Нельзя удалить список свойств поиска из базы данных, пока он связан с каким-либо полнотекстовым индексом, попытки сделать это приводят к ошибкам. Чтобы удалить список свойств поиска из данного полнотекстового индекса, воспользуйтесь инструкцией [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) и укажите предложение SET SEARCH PROPERTY LIST либо с параметром OFF, либо с именем другого списка свойств поиска.  
  
 **Просмотр списков свойств поиска на экземпляре сервера**  
  
-   [sys.registered_search_property_lists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
 **Просмотр списков свойств, связанных с полнотекстовыми индексами**  
  
-   [sys.fulltext_indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
  
 **Удаление списка свойств из полнотекстового индекса**  
  
-   [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> Permissions  
 Необходимо разрешение CONTROL для списка свойств поиска.  
  
> [!NOTE]  
>  Разрешения CONTROL для списка могут быть предоставлены владельцем списка свойств. По умолчанию владельцем списка свойств поиска является пользователь, создавший этот список. Владельца можно изменить с помощью инструкции [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере список свойств `JobCandidateProperties` удаляется из базы данных `AdventureWorks2012`.  
  
```  
DROP SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER SEARCH PROPERTY LIST (Transact-SQL)](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [CREATE SEARCH PROPERTY LIST (Transact-SQL)](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_properties (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [sys.registered_search_property_lists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [sys.registered_search_property_lists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
  
  
