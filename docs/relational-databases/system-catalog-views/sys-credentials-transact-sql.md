---
title: sys.Credentials (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.credentials
- sys.credentials_TSQL
- credentials_TSQL
- credentials
dev_langs:
- TSQL
helpviewer_keywords:
- sys.credentials catalog view
ms.assetid: ea48cf80-904a-4273-a950-6d35b1b0a1b6
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: d94a60edd7dac48b8510a112fe7cbfe1e5ad40ec
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560604"
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Возвращает одну строку для каждых учетных данных на уровне сервера.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|Идентификатор учетных данных. Уникально в пределах сервера.|  
|name|**sysname**|Имя учетных данных. Уникально в пределах сервера.|  
|credential_identity|**nvarchar(4000)**|Имя применяемого идентификатора. Обычно это пользователь Windows. Это имя не обязательно должно быть уникальным.|  
|create_date|**datetime**|Время создания учетных данных.|  
|modify_date|**datetime**|Время последнего изменения учетных данных.|  
|target_type|**Nvarchar(100)**|Тип учетных данных. Возвращает значение NULL для традиционных учетных данных и значение CRYPTOGRAPHIC PROVIDER для учетных данных, сопоставленных с поставщиком служб шифрования. Дополнительные сведения о поставщиках управлении ключами см. в разделе [расширенного управления ключами &#40;расширенного управления Ключами&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  
|target_id|**int**|Идентификатор объекта, с которым сопоставлены учетные данные. Возвращает значение 0 для традиционных учетных данных и значение, отличное от 0, для учетных данных, сопоставленных с поставщиком служб шифрования. Дополнительные сведения о поставщиках управлении ключами см. в разделе [расширенного управления ключами &#40;расширенного управления Ключами&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  

## <a name="remarks"></a>Примечания  
Учетные данные уровня базы данных, см. в разделе [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).
  
## <a name="permissions"></a>Разрешения  
 Требует либо `VIEW ANY DEFINITION` разрешение или `ALTER ANY CREDENTIAL` разрешение. Кроме того, участник не должно быть запрещено `VIEW ANY DEFINITION` разрешение.  
  
## <a name="see-also"></a>См. также  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [Учетные данные (ядро СУБД)](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
