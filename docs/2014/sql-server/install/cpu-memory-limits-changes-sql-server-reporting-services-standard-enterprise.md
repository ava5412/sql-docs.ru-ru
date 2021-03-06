---
title: Изменения ограничений ЦП и памяти для SQL Server Reporting Services Standard и Enterprise | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
caps.latest.revision: 11
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2f2511d378113539bfe8a1a9ccab43da99334f6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325454"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a>Изменения ограничений ЦП и памяти для выпусков служб SQL Server Reporting Services Standard Edition и Enterprise Edition
  Начиная с версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], выпуски служб Reporting Services Standard и Enterprise поддерживают до 64 ГБ системной памяти.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a>Описание  
 Начиная с версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выпуски служб Reporting Services Standard и Enterprise поддерживают до 64 ГБ системной памяти. Может потребоваться повторно настроить параметры системы, чтобы поддерживать обновленные ограничения.  
  
 Дополнительные сведения об ограничениях ЦП и памяти для других выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md), и [объем памяти, поддерживаемый разными выпусками SQL Server](http://go.microsoft.com/fwlink/?LinkId=212633).  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Может потребоваться повторно настроить параметры системы, чтобы поддерживать обновленные ограничения. Дополнительные сведения см. в разделе [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql), и [параметры конфигурации сервера Server Memory](../../database-engine/configure-windows/server-memory-server-configuration-options.md).  
  
## <a name="see-also"></a>См. также  
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Обратная совместимость](../../../2014/getting-started/backward-compatibility.md)  
  
  
