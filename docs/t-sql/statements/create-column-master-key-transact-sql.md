---
title: CREATE COLUMN MASTER KEY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SQL13.SWB.NEWCOLUMNMASTERKEYDEF.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEYDEF.GENERAL.F1
- CREATE COLUMN MASTER KEY
- COLUMN MASTER KEY
- CREATE_COLUMN_MASTER_KEY_TSQL
- COLUMN_MASTER_KEY_TSQL
- SQL13.SWB.NEWCOLUMNMASTERKEY.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEY.GENERAL.F1
dev_langs:
- TSQL
helpviewer_keywords:
- column master key definition
- column master key, create
- CREATE COLUMN MASTER KEY statement
- Always Encrypted, create column master key
ms.assetid: f8926b95-e146-4e3f-b56b-add0c0d0a30e
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a4f7c950785268f1b462c8363e4fb9e5f426055b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993136"
---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Создает объект метаданных главного ключа столбца в базе данных. Элемент метаданных главного ключа столбца, который представляет ключ, хранящийся во внешнем хранилище ключей и применяемый для защиты (шифрования) ключей шифрования столбца при использовании функции [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Использование нескольких главных ключей столбца позволяет производить их регулярную смену для повышения безопасности. Вы можете создать главный ключ столбца в хранилище ключей и соответствующий объект метаданных в базе данных с помощью обозревателя объектов в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью PowerShell. Подробные сведения см. в статье [Общие сведения об управлении ключами для постоянного шифрования](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE COLUMN MASTER KEY key_name   
    WITH (  
        KEY_STORE_PROVIDER_NAME = 'key_store_provider_name',  
        KEY_PATH = 'key_path'   
         )   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *key_name*  
 Имя, под которым главный ключ столбца будет доступен в базе данных.  
  
 *key_store_provider_name*  
 Задает имя поставщика хранилища ключей, представляющий собой клиентский программный компонент, который инкапсулирует хранилище ключей, содержащее главный ключ столбца. Драйвер клиента с поддержкой Always Encrypted использует имя поставщика хранилища ключей для поиска поставщика в своем реестре поставщиков хранилища ключей. Драйвер использует поставщик для расшифровки ключей шифрования столбца, защищенных главным ключом столбца, который хранится в базовом хранилище ключей. Затем значение ключа шифрования столбца в виде открытого текста используется для шифрования параметров запроса, соответствующих зашифрованным столбцам базы данных, или для расшифровки результатов запроса из зашифрованных столбцов.  
  
 Библиотеки драйвера клиента с поддержкой Always Encrypted включают в себя поставщики хранилища ключей для распространенных хранилищ ключей.   
  
Набор доступных поставщиков зависит от типа и версии драйвера клиента. Сведения о конкретных драйверах см. в документации по функции Always Encrypted:

[Разработка приложений с использованием функции Always Encrypted и поставщика .NET Framework для SQL Server](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)


В приведенной ниже таблице перечислены имена системных поставщиков.  
  
|Имя поставщика хранилища ключей|Базовое хранилище ключей|  
    |-----------------------------|--------------------------|
    |'MSSQL_CERTIFICATE_STORE'|Хранилище сертификатов Windows| 
    |'MSSQL_CSP_PROVIDER'|Хранилище, например аппаратный модуль безопасности (HSM), которое поддерживает интерфейс Microsoft CryptoAPI.|
    |'MSSQL_CNG_STORE'|Хранилище, например аппаратный модуль безопасности (HSM), которое поддерживает интерфейс API криптографии следующего поколения.|  
    |'Azure_Key_Vault'|См. статью [Приступая к работе с хранилищем ключей Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/).|  
  

 Вы можете реализовать пользовательский поставщик хранилища ключей. Это позволяет хранить главные ключи столбцов в хранилище, для которого нет встроенного поставщика хранилища ключей в драйвере клиента с поддержкой Always Encrypted.  Обратите внимание на то, что имена пользовательских поставщиков хранилища ключей не могут начинаться с "MSSQL_", так как этот префикс зарезервирован для поставщиков хранилища ключей [!INCLUDE[msCoName](../../includes/msconame-md.md)]. 

  
 key_path  
 Путь к ключу в хранилище главных ключей столбцов. Путь к ключу должен быть допустимым в контексте каждого клиентского приложения, которому необходимо шифровать или расшифровывать данные, хранящиеся в столбце, защищенном (косвенно) соответствующим главным ключом столбца. У клиентского приложения должно быть разрешение на доступ к этому ключу. Формат пути к ключу зависит от поставщика хранилища ключей. Ниже представлен список форматов путей к ключам для системных поставщиков хранилища ключей Майкрософт.  
  
-   **Имя поставщика:** MSSQL_CERTIFICATE_STORE  
  
     **Формат пути к ключу:** *ИмяХранилищаСертификатов*/*РасположениеХранилищаСертификатов*/*ОтпечатокСертификата*  
  
     Где:  
  
     *РасположениеХранилищаСертификатов*  
     Расположение хранилища сертификатов: текущий пользователь или локальный компьютер. Дополнительные сведения см. в статье [Хранилища сертификатов "Локальный компьютер" и "Текущий пользователь"](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx).  
  
     *ИмяХранилищаСертификатов*  
     Имя хранилища сертификатов, например My.  
  
     *ОтпечатокСертификата*  
     Отпечаток сертификата.  
  
     **Примеры:**  
  
    ```  
    N'CurrentUser/My/BBF037EC4A133ADCA89FFAEC16CA5BFA8878FB94'  
  
    N'LocalMachine/My/CA5BFA8878FB94BBF037EC4A133ADCA89FFAEC16'  
    ```  
  
-   **Имя поставщика:** MSSQL_CSP_PROVIDER  
  
     **Формат пути к ключу:** *ИмяПоставщика*/*ИдентификаторКлюча*  
  
     Где:  
  
     *ProviderName*  
     Имя поставщика службы шифрования (CSP), реализующего интерфейс CAPI, для хранилища главных ключей столбцов. Если в качестве хранилища ключей используется модуль HSM, это должно быть имя поставщика CSP, предоставляемого изготовителем модуля HSM. Поставщик должен быть установлен на клиентском компьютере.  
  
     *ИдентификаторКлюча*  
     Идентификатор ключа, используемого в качестве главного ключа столбца, в хранилище ключей.  
  
     **Примеры:**  
  
    ```  
    N'My HSM CSP Provider/AlwaysEncryptedKey1'  
    ```  
  
-   **Имя поставщика:** MSSQL_CNG_STORE  
  
     **Формат пути к ключу:** *ИмяПоставщика*/*ИдентификаторКлюча*  
  
     Где:  
  
     *ProviderName*  
     Имя поставщика хранилища ключей (KSP), реализующего интерфейс API криптографии следующего поколения (CNG), для хранилища главных ключей столбцов. Если в качестве хранилища ключей используется модуль HSM, это должно быть имя поставщика KSP, предоставляемого изготовителем модуля HSM. Поставщик должен быть установлен на клиентском компьютере.  
  
     *ИдентификаторКлюча*  
     Идентификатор ключа, используемого в качестве главного ключа столбца, в хранилище ключей.  
  
     **Примеры:**  
  
    ```  
    N'My HSM CNG Provider/AlwaysEncryptedKey1'  
    ```  

-   **Имя поставщика:** AZURE_KEY_STORE  
  
     **Формат пути к ключу:** *KeyUrl*  
  
     Где:  
  
     *KeyUrl*  
     URL-адрес ключа в Azure Key Vault.


Пример
 
`N'https://myvault.vault.azure.net:443/keys/MyCMK/4c05f1a41b12488f9cba2ea964b6a700'`  
  
## <a name="remarks"></a>Remarks  

Элемент метаданных главного ключа столбца необходимо создать перед созданием элемента метаданных ключа шифрования столбца в базе данных и перед шифрованием столбцов в базе данных с помощью функции Always Encrypted. Обратите внимание на то, что элемент главного ключа столбца в метаданных не содержит фактический главный ключ столбца, который должен храниться во внешнем хранилище ключей столбцов (за пределами SQL Server). Имя поставщика хранилища ключей и путь к главному ключу столбца в метаданных должны быть действительными, чтобы клиентское приложение могло использовать главный ключ столбца для расшифровки ключа шифрования, зашифрованного с помощью главного ключа столбца, и для запроса зашифрованных столбцов.


  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **ALTER ANY COLUMN MASTER KEY**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-column-master-key"></a>A. Создание главного ключа столбца  
 Создание элемента метаданных для главного ключа столбца, хранящегося в хранилище сертификатов, для клиентских приложений, которые используют поставщик MSSQL_CERTIFICATE_STORE для доступа к главному ключу столбца:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
 Создание элемента метаданных для главного ключа столбца, применяемого клиентскими приложениями, которые используют поставщик MSSQL_CNG_STORE:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CNG_STORE',    
    KEY_PATH = N'My HSM CNG Provider/AlwaysEncryptedKey'  
);  
```  
  
 Создание главного ключа столбца, хранящегося в Azure Key Vault, для клиентских приложений, которые используют поставщик AZURE_KEY_VAULT для доступа к главному ключу столбца:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/  
        MyCMK/4c05f1a41b12488f9cba2ea964b6a700');  
```  
  
 Создание главного ключа столбца, хранящегося в пользовательском хранилище главных ключей столбцов:  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = 'CUSTOM_KEY_STORE',    
    KEY_PATH = 'https://contoso.vault/sales_db_tce_key'  
);  
```  
  
## <a name="see-also"></a>См. также:
 
* [DROP COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Постоянное шифрование (компонент Database Engine)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
* [Общие сведения об управлении ключами для постоянного шифрования](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
  
