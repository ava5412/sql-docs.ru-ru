---
title: sys.database_scoped_credentials (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords:
- sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: ebf2bff55e94aad4143c32ab91ca8ab9ea820281
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39538254"
---
# <a name="sysdatabasescopedcredentials-transact-sql"></a>sys.database_scoped_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Возвращает по одной строке для каждой базы данных учетных данных в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|Идентификатор базы данных, учетных данных. Является уникальным в базе данных.|  
|name|**sysname**|Имя базы данных учетных данных. Является уникальным в базе данных.|  
|credential_identity|**nvarchar(4000)**|Имя применяемого идентификатора. Обычно это пользователь Windows. Это имя не обязательно должно быть уникальным.|  
|create_date|**datetime**|Время создания учетных данных области базы данных.|  
|modify_date|**datetime**|Время последнего изменения учетных данных области базы данных.|  
|target_type|**Nvarchar(100)**|Тип базы данных учетных данных. Возвращает `NULL` учетные данные уровня базы данных.|  
|target_id|**int**|Идентификатор объекта, который сопоставляется с учетные данные уровня базы данных. Возвращает значение 0 для базы данных учетные данные|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `CONTROL` на базу данных.  
  
## <a name="see-also"></a>См. также  
 [Учетные данные (ядро СУБД)](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
