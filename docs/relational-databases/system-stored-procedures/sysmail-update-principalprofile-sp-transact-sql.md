---
title: sysmail_update_principalprofile_sp (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_update_principalprofile_sp
- sysmail_update_principalprofile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_principalprofile_sp
ms.assetid: 9fe96e9a-4758-4e4a-baee-3e1217c4426c
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a86fc4775ee1096d72451ace855bb19a1094c3c5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysmailupdateprincipalprofilesp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Обновляет данные о взаимосвязи между каким-либо участником и профилем.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sysmail_update_principalprofile_sp { @principal_id = principal_id | @principal_name = 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    [ @is_default = ] 'is_default'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@principal_id** =] *principal_id*  
 Идентификатор пользователя базы данных или роли в **msdb** базы данных для изменения взаимосвязи. *principal_id* — **int**, значение по умолчанию NULL. Либо *principal_id* или *principal_name* должен быть указан.  
  
 [ **@principal_name** =] **"***principal_name***"**  
 Имя пользователя базы данных или роли в **msdb** базы данных для обновления взаимосвязи. *principal_name* — **sysname**, значение по умолчанию NULL. Либо *principal_id* или *principal_name* может быть указан.  
  
 [ **@profile_id** =] *profile_id*  
 Идентификатор профиля для изменения взаимосвязи. *profile_id* — **int**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
 [ **@profile_name** =] **"***profile_name***"**  
 Имя профиля для изменения взаимосвязи. *profile_name* — **sysname**, значение по умолчанию NULL. Либо *profile_id* или *profile_name* должен быть указан.  
  
 [ **@is_default** =] **"***is_default***"**  
 Является ли данный профиль профилем по умолчанию для пользователя базы данных. Пользователь базы данных может иметь только один профиль по умолчанию. *is_default* — **бит**, не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Данная хранимая процедура изменяется в зависимости от того, является ли заданный профиль профилем по умолчанию для пользователя базы данных. Пользователь базы данных может иметь только один личный профиль по умолчанию.  
  
 Когда имя участника взаимосвязи является **открытый** или идентификатор участника для сопоставления **0**, то хранимая процедура изменяет открытый профиль. Может быть только один открытый (public) профиль по умолчанию.  
  
 Когда **@is_default** — "**1**' и участник связан с более чем одним профилем, то заданный профиль становится профилем по умолчанию для участника. Профиль, который ранее был профилем по умолчанию, все еще связан с участником, но не является более профилем по умолчанию.  
  
 Хранимая процедура **sysmail_update_principalprofile_sp** в **msdb** базы данных и принадлежит **dbo** схемы. Процедуру следует выполнять с трехкомпонентным именем, если текущая база данных не является **msdb**.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения для этой процедуры по умолчанию членам выполнение **sysadmin** предопределенной роли сервера.  
  
## <a name="examples"></a>Примеры  
 **А. Установка профиля в открытый профиль по умолчанию для базы данных**  
  
 Следующий пример устанавливает профиль `General Use Profile` в открытый профиль по умолчанию для пользователей в **msdb** базы данных.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'General Use Profile',  
    @is_default = '1';  
```  
  
 **Б. Установка профиля в частный профиль по умолчанию для пользователя**  
  
 Следующий пример устанавливает профиль `AdventureWorks Administrator` быть для участника профилем по умолчанию `ApplicationUser` в **msdb** базы данных. Профиль должен быть заранее связан с участником. Профиль, который ранее был профилем по умолчанию, все еще связан с участником, но не является более профилем по умолчанию.  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator',  
    @is_default = '1' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
