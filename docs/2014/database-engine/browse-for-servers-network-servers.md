---
title: Обзор серверов (сетевые серверы) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 27
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: af846a1348d67acbb1b1d5776a357baaf99bf07e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176501"
---
# <a name="browse-for-servers-network-servers"></a>Обзор серверов (сетевые серверы)
  Если при подключении к компоненту [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] неизвестно точное имя экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], в поле **Имя сервера** нажмите кнопку **Продолжить обзор**, чтобы открыть диалоговое окно **Выбор серверов**.  
  
 Это диалоговое окно заполняется службой « [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , браузер» на серверах. Название экземпляра может не появиться в списке по нескольким причинам, перечисленным ниже.  
  
-   Служба « [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , браузер» может не работать на компьютере с запущенным [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Возможно, порт UDP 1434 заблокирован брандмауэром.  
  
-   Возможно, установлен флаг **HideInstance** .  
  
 Чтобы подключиться к экземпляру, который не появился в списке, введите полную строку соединения для экземпляра, включая номер порта TCP/IP или имя канала именованных каналов.  
  
## <a name="options"></a>Параметры  
 **Выберите экземпляр SQL Server в сети для соединения**  
 Укажите сервер, с которым нужно соединиться, выбрав экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , показанный в дереве. Можно показывать или скрывать участки дерева, щелкнув узел, помеченный знаком **+** или **–** .  
  
  
