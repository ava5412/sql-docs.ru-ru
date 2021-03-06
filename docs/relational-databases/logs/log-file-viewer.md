---
title: Средство просмотра журналов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
caps.latest.revision: 26
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 44f5ed33bef9ff57e6bc0c4262a950069ec5b480
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32942149"
---
# <a name="log-file-viewer"></a>Средство просмотра файлов журнала
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Средство просмотра журнала в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] служит для доступа к сведениям об ошибках и событиях, регистрируемых в файлах журналов.  
  
## <a name="benefits-of-using-log-file-viewer"></a>Преимущества использования средства просмотра журналов  
 Можно просматривать файлы журнала [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на локальных и удаленных экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые находятся вне сети или не могут запуститься. Получить доступ к файлам журналов вне сети можно в списке «Зарегистрированные серверы» или программным способом с помощью запросов WMI и WQL. Дополнительные сведения см. в разделе [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md). Ниже приведены типы файлов журналов, которые можно открыть с помощью средства просмотра журналов.  
  
-   Коллекция аудита  
  
-   Сбор данных  
  
-   Database Mail  
  
-   Журнал заданий  
  
-   Планы обслуживания  
  
-   Удаленные планы обслуживания  
  
-   SQL Server  
  
-   SQL Server, агент  
  
-   Windows NT (это события Windows, также доступные из программы просмотра событий Windows)  
  
## <a name="log-file-viewer-tasks"></a>Задачи средства просмотра журналов  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает процедуру открытия средства просмотра журналов в зависимости от того, какие сведения нужно просмотреть.|[открыть средство просмотра журнала](../../relational-databases/logs/open-log-file-viewer.md)|  
|Описывает процедуру просмотра файлов журналов, находящихся в режиме вне сети, с помощью зарегистрированных серверов, а также процедуру проверки разрешений WMI.|[Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md)|  
|Предоставляет справку F1 для средства просмотра журналов.|[Справка средства просмотра журнала F1](../../relational-databases/logs/log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a>См. также:  
 [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [Журнал ошибок агента SQL Server](http://msdn.microsoft.com/library/0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41)  
  
  
