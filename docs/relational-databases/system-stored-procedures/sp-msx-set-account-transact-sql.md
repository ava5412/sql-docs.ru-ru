---
title: sp_msx_set_account (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a2d776a7ad3d29c180a4a2d2b017f5e1e6d0158a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249426"
---
# <a name="spmsxsetaccount-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Задает имя и пароль учетной записи агента главного сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на целевом сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@credential_name=** ] **"***credential_name***"**  
 Учетное имя, используемое для записи журнала на главном сервере. Указанное имя должно быть именем существующей учетной записи. Либо *credential_name* или *credential_id* должен быть указан.  
  
 [  **@credential_id=** ] *credential_id*  
 Идентификатор для учетной записи, используемый для записи журнала на главном сервере. Идентификатор должен быть идентификатором существующей учетной записи. Либо *credential_name* или *credential_id* должен быть указан.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует учетные данные для хранения сведений об имени пользователя и пароле, которые целевой сервер использует для подключения к главному серверу. Эта процедура задает учетные данные, которые агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует для входа на главный сервер для этого целевого сервера.  
  
 Указанные учетные данные должны существовать. Дополнительные сведения о создании учетных данных см. в разделе [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение **sp_msx_set_account** по умолчанию предоставляются членам **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 Следующий пример устанавливает для сервера учетные данные `MsxAccount` для соединения с главным сервером.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры агента SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_get_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
