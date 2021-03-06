---
title: sys.external_libraries (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: jeannt
ms.author: jeannt
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3f6d833488982da777d0f146d55f0a67fa945de5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553264"
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Поддерживает управление библиотеками пакетов, связанных с внешних сред выполнения, например R или Python.

## <a name="sysexternallibraries"></a>sys.external_libraries

Sys.external_libraries представление каталога содержит по строке для каждой внешней библиотеке, который был загружен в базу данных.

|Имя столбца |Тип данных | Описание|
|------|------|------|
|external_library_id |ssNoversion | Идентификатор объекта внешней библиотеки. |
|name |sysname |Имя внешней библиотеки. Уникален в пределах базы данных на одного владельца.|
|principal_id |ssNoversion |Идентификатор участника, которому принадлежит этот внешняя библиотека. |
|language | sysname | Имя используемого языка или среды выполнения, которая поддерживает внешнюю библиотеку. Допустимые значения: «R». Дополнительные среды выполнения могут быть добавлены в будущем.|
|область |ssNoversion |0 для открытой области; 1 — закрытая область |  
|scope_desc |varchar(7) |Указывает, является ли пакет общедоступный или частный|


## <a name="see-also"></a>См. также  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)  
[Пакет управления для SQL Server R Services](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
