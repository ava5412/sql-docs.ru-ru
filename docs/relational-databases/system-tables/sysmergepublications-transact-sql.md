---
title: "sysmergepublications (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sysmergepublications
- sysmergepublications_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmergepublications system table
ms.assetid: 7f82c6c3-22d1-47c0-a92b-4d64b98cc455
caps.latest.revision: "42"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95059187ddd567212027d73dbd361e1ee9d2e7a7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysmergepublications-transact-sql"></a>sysmergepublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой публикации слиянием, определенной в базе данных. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя сервера по умолчанию.|  
|**publisher_db**|**sysname**|Имя базы данных издателя по умолчанию.|  
|**name**|**sysname**|Имя публикации.|  
|**Описание**|**nvarchar(255)**|Краткое описание публикации.|  
|**хранения**|**int**|Срок хранения для всего набора публикаций, где модуль идентифицируется по значению **retention_period_unit** столбца.|  
|**publication_type**|**tinyint**|Состояние публикации относительно фильтрации:<br /><br /> **0** = не отфильтрована.<br /><br /> **1** = отфильтрованы.|  
|**pubid**|**uniqueidentifier**|Уникальный идентификационный номер этой публикации. Формируется при добавлении публикации.|  
|**designmasterid**|**uniqueidentifier**|Зарезервировано для последующего использования.|  
|**parentid**|**uniqueidentifier**|Указывает на родительскую публикацию, из которой была создана текущая равноправная публикация или публикация подмножества (используется для иерархических топологий публикаций).|  
|**sync_mode**|**tinyint**|Режим синхронизации публикации:<br /><br /> **0** = машинный код.<br /><br /> **1** = символ.|  
|**allow_push**|**int**|Допустимость принудительных подписок:<br /><br /> **0** = принудительные подписки не разрешены.<br /><br /> **1** = принудительные подписки разрешены.|  
|**allow_pull**|**int**|Допустимость подписок по запросу:<br /><br /> **0** = подписки по запросу не разрешено.<br /><br /> **1** = по запросу подписки разрешены.|  
|**allow_anonymous**|**int**|Допустимость анонимных подписок в публикации:<br /><br /> **0** = анонимные подписки не разрешены.<br /><br /> **1** = анонимные подписки разрешены.|  
|**centralized_conflicts**|**int**|Хранение конфликтных записей на издателе:<br /><br /> **0** = конфликтные записи не хранятся на издателе.<br /><br /> **1** = конфликтные записи хранятся на издателе.|  
|**status**|**tinyint**|Зарезервировано для последующего использования.|  
|**snapshot_ready**|**tinyint**|Состояние моментального снимка публикации:<br /><br /> **0** = моментальный снимок не готов к использованию.<br /><br /> **1** = моментальный снимок будет готов к использованию.<br /><br /> **2** = новый моментальный снимок для этой публикации необходимо создать.|  
|**enabled_for_internet**|**bit**|Доступность файлов синхронизации для публикации через Интернет, по протоколу FTP, а также их доступность для других служб:<br /><br /> **0** = синхронизации файлов, доступных из Интернета.<br /><br /> **1** = синхронизации файлов не доступен из Интернета.|  
|**dynamic_filters**|**bit**|Указывает, была ли публикация отфильтрована с помощью параметризованного фильтра строк:<br /><br /> **0** = публикация отфильтрована не строки.<br /><br /> **1** = публикация отфильтрована строка.|  
|**snapshot_in_defaultfolder**|**bit**|Хранение файлов моментальных снимков в папке по умолчанию:<br /><br /> **0** = файлы моментальных снимков хранятся в папке по умолчанию.<br /><br /> **1** = файлы моментальных снимков хранятся в расположении, заданном **alt_snapshot_folder**.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Задает расположение альтернативной папки для моментального снимка.|  
|**pre_snapshot_script**|**nvarchar(255)**|Указатель. **sql** файл, который агент слияния выполняется до любого объекта репликации скрипты при применении моментального снимка на подписчике.|  
|**post_snapshot_script**|**nvarchar(255)**|Указатель. **sql** файл, который агент слияния выполняет после всех других репликации скриптов объектов и данных были применены во время начальной синхронизации.|  
|**compress_snapshot**|**bit**|Указывает ли моментальный снимок, записываемый **alt_snapshot_folder** расположение сжимается в [!INCLUDE[msCoName](../../includes/msconame-md.md)] формате CAB. **0** указывает, что файл не сжимается.|  
|**ftp_address**|**sysname**|Сетевой адрес службы FTP для распространителя. Указывает расположение файлов моментальных снимков публикаций, необходимых агенту слияния, если служба FTP включена.|  
|**ftp_port**|**int**|Номер порта службы FTP для распространителя.|  
|**ftp_subdirectory**|**nvarchar(255)**|Подкаталог, где находятся файлы моментальных снимков для агента слияния.|  
|**ftp_login**|**sysname**|Пароль пользователя для подключения к службе FTP.|  
|**ftp_password**|**nvarchar(524)**|Пароль пользователя для подключения к службе FTP.|  
|**conflict_retention**|**int**|Указывает срок хранения конфликтных записей (в сутках). По истечении срока хранения конфликтные строки удаляются из конфликтной таблицы.|  
|**keep_before_values**|**int**|Оптимизация синхронизации для данной публикации:<br /><br /> **0** = синхронизация не оптимизирована и отправленные всем подписчикам секции проверяются при изменении данных в секции.<br /><br /> **1** = синхронизация оптимизирована и влияет только на подписчики, чьи строки есть в измененной секции.|  
|**allow_subscription_copy**|**bit**|Возможность копирования базы данных подписки. **0** означает копирование запрещено.|  
|**allow_synctoalternate**|**bit**|Показывает, допустимо ли для данного издателя наличие альтернативного участника синхронизации. **0** означает, что участник синхронизации не разрешено.|  
|**validate_subscriber_info**|**nvarchar(500)**|Выводит список функций, с помощью которых возвращаются сведения о подписчике, и проверяет правильность критериев параметризованной фильтрации строк на подписчике.|  
|**ad_guidname**|**sysname**|Указывает, опубликована ли публикация в каталоге [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory. Допустимый идентификатор GUID указывает, что публикация опубликована в Active Directory и идентификатор GUID — соответствующий объект публикации Active Directory **objectGUID**. Если значение равно NULL, то публикация не опубликована в Active Directory.|  
|**backward_comp_level**|**int**|Уровень совместимости базы данных. Может использоваться одно из следующих значений:<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].|  
|**max_concurrent_merge**|**int**|Максимальное число выполняемых одновременно процессов слияния. Значение **0** для этого свойства означает отсутствие ограничений на число параллельных процессов слияния в любой момент времени. Это свойство устанавливает ограничение на число параллельных процессов слияния, которые могут быть одновременно запущены для публикации слиянием. Если на одно и то же время назначено больше процессов моментальных снимков, чем позволяет указанное значение, лишние задачи будут помещены в очередь до завершения текущего процесса слияния.|  
|**max_concurrent_dynamic_snapshots**|**int**|Максимальное допустимое число параллельных сеансов моментальных снимков отфильтрованных данных, которые могут быть запущены для публикации слиянием. Если **0**, не ограничено максимальное количество сеансов моментальных снимков отфильтрованных данных, одновременно выполняемых для публикации в любой момент времени. Это свойство устанавливает ограничение на число параллельных процессов создания моментальных снимков, которые могут быть одновременно запущены для публикации слиянием. Если на одно и то же время назначено больше процессов моментальных снимков, чем позволяет указанное значение, лишние задачи будут помещены в очередь до завершения текущего процесса слияния.|  
|**use_partition_groups**|**smallint**|Указывает, используются ли в публикации предварительно вычисляемые секции.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Список функций (через точку с запятой), применяемых в параметризованных фильтрах строк публикации.|  
|**partition_id_eval_proc**|**sysname**|Указывает имя процедуры, с помощью которой агент слияния на подписчике определяет назначенный ему идентификатор секции.|  
|**publication_number**|**smallint**|Указывает столбец идентификаторов, который предоставляет двухбайтовое сопоставление для **pubid**. **pubid** является глобальный уникальный идентификатор для публикации, в то время как номер публикации является уникальным только в пределах определенной базы данных.|  
|**replicate_ddl**|**int**|Показывает, поддерживается ли в публикации репликация схемы.<br /><br /> **0** = DDL не реплицируются инструкции.<br /><br /> **1** = DDL реплицируются инструкции, выполняемые на издателе.<br /><br /> Дополнительные сведения см. в статье [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).|  
|**allow_subscriber_initiated_snapshot**|**bit**|Указывает на то, что подписчики могут начать процесс, формирующий моментальный снимок для публикации с помощью параметризованных фильтров: **1** указывает, что подписчики могут инициировать процесс создания моментального снимка.|  
|**dynamic_snapshot_queue_timeout**|**int**|При использовании параметризованных фильтров указывает выраженное в минутах время, которое подписчик должен ожидать в очереди до начала процесса формирования моментального снимка.|  
|**dynamic_snapshot_ready_timeout**|**int**|При использовании параметризованных фильтров указывает время в минутах, в течение которого подписчик ожидает завершения процесса формирования моментального снимка.|  
|**распространитель**|**sysname**|Название распространителя для публикации.|  
|**snapshot_jobid**|**binary(16)**|Определяет задание агента, формирующее моментальный снимок, когда подписчик начинает процесс формирования моментального снимка.|  
|**allow_web_synchronization**|**bit**|Указывает, включена ли публикация для веб-синхронизация, где **1** означает, что веб-синхронизация разрешена для публикации.|  
|**web_synchronization_url**|**nvarchar(500)**|Значение URL-адреса по умолчанию, применяемое для веб-синхронизации.|  
|**allow_partition_realignment**|**bit**|Указывает на отправление удалений подписчику, если изменения строки на издателе приводят к изменению секции:<br /><br /> **0** = данные из старой секции остаются на подписчике, когда изменения, внесенные в эти данные на издателе не будут реплицированы на подписчик, но изменения, внесенные на подписчике будут реплицироваться на издатель.<br /><br /> **1** = удаления посылаются на подписчик для отражения результатов изменений секции путем удаления данных, не являются частью секции подписчика.<br /><br /> Дополнительные сведения см. в разделе [sp_addmergepublication &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).<br /><br /> Примечание: Данные, сохраняющиеся на подписчике, если это значение равно **0** должны рассматриваться, как если бы они были доступны только для чтения; Однако это не требование строго системы репликации.|  
|**retention_period_unit**|**tinyint**|Определяет единицу измерения, используемых при определении *хранения*, который может принимать одно из следующих значений:<br /><br /> **0** = день.<br /><br /> **1** = неделя.<br /><br /> **2** = месяц.<br /><br /> **3** = год.|  
|**decentralized_conflicts**|**int**|Указывает, хранятся ли на подписчике записи, вызвавшие конфликт:<br /><br /> **0** = конфликтные записи не хранятся на подписчике.<br /><br /> **1** = конфликтные записи хранятся на подписчике.|  
|**generation_leveling_threshold**|**int**|Задает число изменений в формировании. Поколение — это набор изменений, переданных издателю или подписчику.|  
|**automatic_reinitialization_policy**|**bit**|Указывает, передаются ли изменения с подписчика перед автоматической повторной инициализацией.<br /><br /> **1** = изменения передаются с подписчика перед автоматической повторной инициализацией.<br /><br /> **0** = изменения не передаются перед автоматической повторной инициализацией.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergepublication &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)  
  
  