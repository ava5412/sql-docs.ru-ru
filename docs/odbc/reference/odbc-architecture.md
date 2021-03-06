---
title: Архитектура ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5e9311bc990dddcac5addd5953125cd0ba435a06
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916134"
---
# <a name="odbc-architecture"></a>Архитектура ODBC
Архитектура ODBC состоит из четырех компонентов:  
  
-   **Приложение** выполняет обработку и вызовы функций ODBC для отправки инструкций SQL и получения результатов.  
  
-   **Диспетчер драйверов** загружает и выгружает драйверы от имени приложения. Функция ODBC процессы вызывает или передает их драйверу.  
  
-   **Драйвер** вызывает функции ODBC процессы, отправляет запросы SQL к определенному источнику данных и возвращает результаты в приложение. При необходимости драйвер изменяет запрос приложения так, чтобы запрос соответствует синтаксису, поддерживаемых связанного СУБД.  
  
-   **Источник данных** Consists данных пользователю получить доступ и операционной системы, СУБД и платформы сети (если таковые имеются) используется для доступа к СУБД.  
  
 Обратите внимание на следующие аспекты архитектуры ODBC. Может существовать первым, несколько драйверов и источников данных, который позволяет приложениям одновременно обращаться к данным из нескольких источников данных. Во-вторых, API-Интерфейс ODBC используется в двух местах: между приложением и диспетчера драйверов, а также между диспетчера драйверов и каждого драйвера. Интерфейс между диспетчера драйверов и драйверов, иногда называют *интерфейс поставщика службы,* или *SPI*. Для ODBC программный интерфейс приложения (API) и интерфейс поставщика службы (SPI) одинаковы; то есть диспетчера драйверов и каждого из драйверов имеют один и тот же интерфейс в одной функции.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Приложения](../../odbc/reference/applications.md)  
  
-   [Диспетчер драйверов](../../odbc/reference/the-driver-manager.md)  
  
-   [Драйверы](../../odbc/reference/drivers.md)  
  
-   [Источники данных](../../odbc/reference/data-sources.md)
