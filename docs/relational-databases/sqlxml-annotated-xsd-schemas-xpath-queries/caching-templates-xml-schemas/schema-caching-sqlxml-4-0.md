---
title: Кэширование схем (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: f6b9e9a8a6d9406def9e2adc90e1ef7e9b8545a1
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559644"
---
# <a name="schema-caching-sqlxml-40"></a>Кэширование схем (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  При установке side-by-side XML для Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0 и SQLXML 3.0 можно явно управлять схемы, кэширование во всех версиях ОС, используя следующие разделы реестра:  
  
 Web Release 1.  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 SQLXML 2.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 SQLXML 3.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Дополнительные сведения об установке side-by-side см. в разделе [новые возможности в SQLXML 4.0 с пакетом обновления 1](../../../relational-databases/sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).  
  
 Кэширование схем значительно повышает производительность запроса XPath. При выполнении запроса XPath к схеме сопоставления эта схема хранится в памяти, и необходимые структуры данных строятся в памяти. Если задано кэширование схем, то схема остается в памяти, тем самым повышая производительность последующих запросов XPath.  
  
 Размер кэша для схем можно задать, добавив в реестр указанный выше раздел.  
  
 Размер схемы устанавливается в зависимости от доступной памяти и количества используемых схем. Значение по умолчанию **SchemaCacheSize** равно 31. Если задать **SchemaCacheSize** более поздней версии, используется больше памяти. Поэтому можно увеличить размер кэша, если доступ к схеме происходит медленно, и уменьшить его при нехватке памяти.  
  
 Из соображений производительности рекомендуется установить **SchemaCacheSize** выше, чем количество обычно используемых схем сопоставления. Как увеличить количество схем, если **SchemaCacheSize** меньше, чем количество схем, у вас есть, то производительность снижается.  
  
> [!NOTE]  
>  Не рекомендуется кэшировать схемы во время разработки программ, поскольку изменения, вносимые в схемы, отражаются в кэше примерно через две минуты.  
  
## <a name="see-also"></a>См. также  
 [Кэширование шаблонов &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)   
 [Кэширование XSL &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
