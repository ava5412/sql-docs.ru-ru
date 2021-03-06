---
title: Учетные данные (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 579b9d6f9847652ab2088eeb5111372fc4377c02
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198784"
---
# <a name="credentials-database-engine"></a>Учетные данные (компонент Database Engine)
  Учетные данные представляют собой запись, которая содержит сведения для проверки подлинности (учетные данные), которые необходимы для подключения к ресурсу вне [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Эти сведения используются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Большинство учетных данных содержат имя пользователя Windows и пароль.  
  
 Хранимые в учетных данных сведения позволяют пользователю, подключившемуся к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с применением проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , обращаться к ресурсам, размещенным вне данного экземпляра сервера. Когда внешним ресурсом является ОС Windows, проверяется соответствие данных пользователя сведениям, указанным в учетной записи Windows. Одни учетные данные могут соответствовать нескольким зарегистрированным именам входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Но имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может соответствовать только одним учетным данным.  
  
 Системные учетные данные создаются автоматически и связываются с определенными конечными точками. Имена для системных учетных данных начинаются с двух символов решетки (##).  
  
 Дополнительные сведения об учетных данных см. в разделе [sys.credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) представления каталога.  
  
## <a name="related-content"></a>См. также  
 [Создание учетных данных](../authentication-access/create-a-credential.md) [создать учетные данные &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
 [Обеспечение безопасности SQL Server](../securing-sql-server.md)  
  
  
