---
title: sys.asymmetric_keys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- asymmetric_keys
- sys.asymmetric_keys_TSQL
- asymmetric_keys_TSQL
- sys.asymmetric_keys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.asymmetric_keys catalog view
ms.assetid: bbca796a-9bb5-4a62-9ca8-1d255984553d
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 094827a645440b2503adbc413042ec99de44adb2
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553614"
---
# <a name="sysasymmetrickeys-transact-sql"></a>sys.asymmetric_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого асимметричного ключа.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя ключа. Уникален в пределах базы данных.|  
|**principal_id**|**int**|Идентификатор участника базы данных, который является владельцем этого ключа.|  
|**asymmetric_key_id**|**int**|Идентификатор ключа. Уникален в пределах базы данных.|  
|**pvt_key_encryption_type**|**char(2)**|Способ шифрования ключа.<br /><br /> NA = не зашифрован<br /><br /> MK = ключ шифруется главным ключом<br /><br /> PW = ключ шифруется пользовательским паролем<br /><br /> MK = ключ шифруется главным ключом службы.|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|Описание способа шифрования закрытого ключа.<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**отпечаток**|**varbinary(32)**|Хэш ключа SHA-1. Хэш глобально уникален.|  
|**алгоритм**|**char(2)**|Алгоритм, используемый с ключом.<br /><br /> 1R = 512-разрядный RSA<br /><br /> 2R = 1024-разрядный RSA<br /><br /> 3R = 2048-разрядный RSA|  
|**algorithm_desc**|**nvarchar(60)**|Описание алгоритма, используемого с ключом.<br /><br /> RSA_512<br /><br /> RSA_1024<br /><br /> RSA_2048|  
|**key_length**|**int**|Длина ключа в битах.|  
|**ИД безопасности**|**varbinary(85)**|Идентификатор безопасности имени входа для этого ключа. Для ключей системы расширенного управления ключами это значение будет равно NULL.|  
|**string_sid**|**nvarchar(128)**|Строковое представление входного идентификатора SID ключа. Для ключей системы расширенного управления ключами это значение будет равно NULL.|  
|**public_key**|**varbinary(max)**|Открытый ключ.|  
|**attested_by**|**nvarchar(260)**|Только для системного использования.|  
|**provider_type**|**nvarchar(120)**|Тип поставщика служб шифрования.<br /><br /> CRYPTOGRAPHIC PROVIDER = ключи системы расширенного управления ключами<br /><br /> NULL = ключи, не относящиеся к расширенному управлению ключами|  
|**cryptographic_provider_guid**|**uniqueidentifier**|Идентификатор GUID поставщика служб шифрования. Для ключей, не относящихся к системе расширенного управления ключами, это значение будет равно NULL.|  
|**cryptographic_provider_algid**|**sql_variant**|Идентификатор алгоритма для поставщика служб шифрования. Для ключей, не относящихся к системе расширенного управления ключами, это значение будет равно NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
  
  
