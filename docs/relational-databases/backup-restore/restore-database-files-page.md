---
title: Восстановление базы данных (страница "Файлы") | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.restoredb.files.f1
- sql13.swb.restoredb.files.f1 in the code
ms.assetid: 714c36ea-a9f9-43a4-99f9-a6f73d1baf8e
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 14411c1f06a25ace27823f2b0890c89fa5009cf8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32918809"
---
# <a name="restore-database-files-page"></a>Восстановление базы данных (страница «Файлы»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Используйте страницу **Файлы** диалогового окна **Восстановление базы данных** для выбора конкретных файлов, из которых будет восстановлена база данных.  
  
## <a name="options"></a>Параметры  
  
### <a name="restore-database-files-as"></a>Восстановить файлы базы данных как  
 Используйте, чтобы назначить новый путь к восстановленным файлам и управлять им.  
  
 **Переместить все файлы в папку**  
 Перемещение восстановленных файлов.  
  
|Параметр|Description|  
|------------|-----------------|  
|**Папка файла данных**|Введите или выполните поиск имени папки файла данных, в которую нужно переместить восстановленный файл или файлы данных.|  
|**Папка файлов журнала**|Введите или выполните поиск файла журнала или папки файлов, в которую нужно переместить восстановленный файл журнала.|  
  
 **Логическое имя файла**  
 Отображает одну строку для каждого восстанавливаемого файла базы данных.  
  
 **Тип файла**  
 Отображает тип файла.  
  
 **Имя исходного файла**  
 Отображает исходный путь к файлу для каждого восстанавливаемого файла базы данных.  
  
 **Восстановить как**  
 Перечисляет имена файлов, в которых будут сохранены восстанавливаемые файлы. Введите или найдите соответствующее имя файла.  
  
## <a name="see-also"></a>См. также:  
 [Восстановление базы данных (страница "Общие")](../../relational-databases/backup-restore/restore-database-general-page.md)   
 [Восстановление базы данных (страница "Параметры")](../../relational-databases/backup-restore/restore-database-options-page.md)   
 [Аргументы инструкции RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-arguments-transact-sql.md)   
 [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
