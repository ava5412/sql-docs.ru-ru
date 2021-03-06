---
title: Проверка подлинности Active Directory для SQL Server в Linux | Документация Майкрософт
description: Статья содержит общие сведения о проверке подлинности Active Directory для SQL Server в Linux.
author: rothja
ms.date: 02/23/2018
ms.author: jroth
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 9d55275269ee09daf933521330b093a8d98411fd
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087116"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Проверка подлинности Active Directory для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье представлен обзор проверки подлинности Active Directory (AD) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux. Проверка подлинности AD называется также встроенная проверка подлинности в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

## <a name="ad-authentication-overview"></a>Обзор проверки подлинности AD

Проверка подлинности AD позволяет клиентов, присоединенных к домену, в ОС Windows или Linux, чтобы проходить проверку подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью своих учетных данных домена и протокола Kerberos.

Проверка подлинности AD имеет следующие преимущества над [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] проверки подлинности:

- Пользователи проходят проверку подлинности с помощью единого входа, не вводя пароль.   
- Создание имен входа для группы AD, можно управлять доступом и разрешениями в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью членства в группах AD.  
- Каждый пользователь имеет единую идентификацию в вашей организации, поэтому не нужно для отслеживания которого [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] круг пользователей, которым соответствуют имена входа.   
- AD позволяет принудительно применять политику централизованная паролей в организации.   

## <a name="configuration-steps"></a>Шаги настройки

Чтобы использовать проверку подлинности Active Directory, необходимо иметь контроллера домена AD (Windows) в сети.

В этом руководстве предоставляются подробные сведения о настройке проверки подлинности AD [руководство: проверка подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md). В следующем списке приведены Сводка со ссылкой на каждый раздел в этом руководстве:

1. [Присоединение узла SQL Server к домену Active Directory](sql-server-linux-active-directory-authentication.md#join).
1. [Создание пользователя AD для SQL Server и задайте ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser).
1. [Настройка keytab службы SQL Server](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Создать имена входа SQL Server на основе AD в Transact-SQL](sql-server-linux-active-directory-authentication.md#createsqllogins).
1. [Подключение к SQL Server с использованием проверки подлинности AD](sql-server-linux-active-directory-authentication.md#connect).

## <a name="known-issues"></a>Известные проблемы

- В настоящее время единственного способа проверки подлинности поддерживается для конечной точки зеркального отображения базы данных является СЕРТИФИКАТ. Метод проверки подлинности WINDOWS будет добавлена в будущем выпуске.
- Сторонние средства AD, такие как Centrify, Powerbroker, и Vintela не поддерживаются.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о том, как реализовать проверку подлинности Active Directory для SQL Server в Linux см. в разделе [руководство: проверка подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).