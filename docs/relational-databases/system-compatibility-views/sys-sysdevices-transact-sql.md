---
title: sys.sysdevices (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
caps.latest.revision: 24
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bf1a22fae1c4c8f69edf843c1a126844abdd1190
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="syssysdevices-transact-sql"></a>sys.sysdevices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого файла резервной копии на диске или магнитной ленте, а также для файла базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Логическое имя файла резервной копии или базы данных.|  
|**size**|**int**|Размер файла в страницах по 2 КБ. |  
|**Низкий**|**int**|Поддерживается только для обратной совместимости.|  
|**Высокий уровень**|**int**|Поддерживается только для обратной совместимости.|  
|**status**|**smallint**|Битовая карта, показывающая тип устройства:<br /><br /> 1 = диск по умолчанию;<br /><br /> 2 = физический диск;<br /><br /> 4 = логический диск;<br /><br /> 8 = пропустить заголовок;<br /><br /> 16 = файл резервной копии;<br /><br /> 32 = устройство последовательной записи;<br /><br /> 4096 = только для чтения.|  
|**cntrltype**|**smallint**|Тип контроллера:<br /><br /> 0 = файл базы данных не на компакт-диске;<br /><br /> 2 = дисковый файл резервной копии;<br /><br /> 3 — 4 = файл резервной копии на дискете;<br /><br /> 5 = файл резервной копии на ленточном накопителе;<br /><br /> 6 = файл с доступом через именованные каналы.|  
|**phyname**|**nvarchar(260)**|Имя физического файла.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
