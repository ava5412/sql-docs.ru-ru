---
title: "О драйверах и источники данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 79ae9e95ce31df371366e9073cb36f88c5bd9ece
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="about-drivers-and-data-sources"></a>О драйверах и источников данных
*Драйверы* являются компонентами, которые обрабатывают запросы ODBC и возврата данных в приложение. При необходимости драйверы измените запрос приложения в форму, которая воспринимает источник данных. Необходимо использовать программу установки драйвера для добавления или удаления драйверов с вашего компьютера.  
  
 *Источники данных* баз данных или файлов, используемых драйвером и идентифицируются по имени источника данных (DSN). Используйте администратор источника данных ODBC для добавления, настройки и удаления источников данных из системы. В следующей таблице описаны типы источников данных, которые могут использоваться.  
  
|Источник данных|Description|  
|-----------------|-----------------|  
|Пользователь|Пользовательских источников данных на локальном компьютере и может использоваться только текущим пользователем. Они зарегистрированы в дереве реестра HKEY_CURRENT_USER.|  
|System|Системный DSN являются локальными для компьютера, а не для конкретного пользователя. Система или любой пользователь с правами можно использовать для установки системный DSN источника данных. Системный DSN регистрируются в реестра HKEY_LOCAL_MACHINE.|  
|Файл|Файловые источники данных являются файловых источников, которые могут совместно использоваться все пользователи, имеющие необходимые драйверы и поэтому имеют доступ к базе данных. Эти источники данных не должны быть предоставлены для пользователя, а также находиться на локальном компьютере. Имена источников данных файла не идентифицировано выделенный реестра; Вместо этого они идентифицируются по имени файла с расширением DSN с.|  
  
 Пользовательских и системных источников данных которые в совокупности называются *машины* источники данных, поскольку они являются локальными для компьютера.  
  
 Каждый из этих источников данных имеет вкладку в **администратор источников данных ODBC** диалоговое окно. Дополнительные сведения о доступных источниках данных см. в разделе [Источники данных](../../odbc/reference/data-sources.md).