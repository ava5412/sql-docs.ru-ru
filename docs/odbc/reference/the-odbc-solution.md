---
title: Решение ODBC | Документы Microsoft
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], using ODBC
ms.assetid: 34b80790-e010-4b90-8eaa-03189f5d8986
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a071ce8c5fc767b3cb7dc998562328e4a6b94d53
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32918929"
---
# <a name="the-odbc-solution"></a>Решение ODBC
Ответ на запрос, такое как ODBC стандартизировать системные базы данных access Существует два архитектурные требования:  
  
-   Приложения должны иметь доступ к несколько СУБД, с помощью того же исходного кода без повторной компиляции или повторного связывания.  
  
-   Приложения должны иметь возможность доступа к СУБД несколько одновременно.  
  
 И имеется один дополнительные вопрос, из-за реальности marketplace:  
  
-   Какие возможности СУБД для предоставления ODBC Только функции, которые являются общими для всех СУБД или любые функции, доступные в любой СУБД?  
  
 ODBC позволяет решить эти проблемы следующим образом:  
  
-   **ODBC — это интерфейс уровня вызова.** Чтобы решить проблему, как приложения получают доступ к нескольким СУБД, с помощью того же исходного кода, ODBC определяет стандартные CLI. Это содержит все функции в спецификациях CLI из Open Group и ISO/IEC и обеспечивает дополнительные функции, часто необходимые приложения.  
  
     Другой библиотеки или драйвера, является обязательным для каждой СУБД, поддерживающий ODBC. Драйвер реализует функции API-интерфейса ODBC. Чтобы использовать другой драйвер, приложение требует повторной компиляции или повторно связать. Вместо этого приложение просто загружает новый драйвер и вызывает функции. Для доступа к нескольким СУБД одновременно, приложение загружает несколько драйверов. Объясняется, как драйверы поддерживаются операционной системой. Например в операционной системе Microsoft® Windows®, драйверов, библиотек динамической компоновки (DLL).  
  
-   **ODBC определяет стандартный синтаксис SQL.** Помимо стандартных интерфейс уровня вызова ODBC определяет стандартный синтаксис SQL. Этой грамматике основана на спецификации Open CAE SQL группы. Различия между двумя грамматик минимальны и в основном из-за различия между грамматику SQL, необходимые для встроенного SQL (Open Group) и CLI (ODBC). Существуют также некоторые расширения к предоставлять обычно доступен языковые функции, не связанная с грамматики Open Group грамматике.  
  
     Приложения могут отправлять инструкции с использованием Грамматика ODBC или СУБД. Инструкция использует грамматику ODBC, которая отличается от СУБД синтаксису, драйвер преобразует перед его отправкой в источнике данных. Однако подобные преобразования встречаются редко, так как большинство СУБД уже используется стандартный синтаксис SQL.  
  
-   **ODBC предоставляет диспетчера драйверов для управления одновременный доступ к нескольким СУБД.** Несмотря на то, что использовать драйверы устранены одновременно доступ к нескольким СУБД, код для этого могут быть сложными. Приложения, предназначенные для работы с все драйверы не может быть статически связан какие-либо драйверы. Вместо этого необходимо загрузить драйверы устройства во время выполнения и вызывать функции в их через таблицу указателей на функции. Ситуация усложняется, если приложение использует несколько драйверов одновременно.  
  
     Каждое приложение, чтобы сделать это, ODBC предоставляя диспетчера драйверов. Диспетчер драйверов реализует все функции ODBC, главным образом для сквозной вызовов функций ODBC в драйверы — и статически связана с приложением или загружена приложением во время выполнения. Таким образом приложение вызывает функции ODBC, по имени диспетчера драйверов, а не указатель в каждого драйвера.  
  
     Если приложению требуется конкретный драйвер, сначала он запрашивает маркер подключения для идентификации драйвера и запросов, что диспетчер драйверов загрузить драйвер. Диспетчер драйверов будет загружен драйвер и сохраняет адрес каждой функции в драйвере. Попытка вызова функции ODBC в драйвере, приложение вызывает эту функцию в диспетчер драйверов и передает дескриптор соединения для драйвера. Затем диспетчер драйверов вызывает функцию с помощью адреса, сохраненную ранее.  
  
-   **ODBC предоставляет значительное количество компонентов СУБД, но не требует драйверы для поддержки всех из них.** Если ODBC только те компоненты, которые являются общими для всех СУБД, было бы использовать; в конце концов причина так, существует множество различных DBMS заключается в том, что они имеют разные функции. Если все возможности, доступные в любой СУБД ODBC, невозможно драйверов для реализации.  
  
     Вместо этого ODBC предоставляет значительное число функций — более не поддерживается в большинстве СУБД, но требуются драйверы устройств, реализуют только подмножество этих функций. Драйверы реализовать оставшиеся компоненты только в том случае, если они поддерживаются базовой СУБД или при желании для эмуляции их. Таким образом приложения могут быть написаны для использования возможности единого СУБД, как представлено драйвер для этого СУБД использовать только те функции, используемые все СУБД, а также проверки для поддержки конкретных возможностей и реагировать соответствующим образом.  
  
     Приложение может определить, какие возможности драйвера и СУБД, ODBC предоставляет две функции (**SQLGetInfo** и **SQLGetFunctions**), которые возвращают Общие сведения о драйвера и СУБД драйвер поддерживает возможности и список функций. ODBC также определяет API и SQL уровни соответствия грамматики, определяющие широкий диапазон возможностей, поддерживаемых драйвером. Дополнительные сведения см. в разделе [уровни соответствия](../../odbc/reference/develop-app/conformance-levels.md).  
  
     Важно помнить, что ODBC определяет общий интерфейс для всех функций, которые она предоставляет. По этой причине приложения содержат определенные функции код, не зависящие от СУБД и могут использовать драйверы, которые предоставляют эти возможности. Является одним из преимуществ этого приложения не обязательно будут обновляться при улучшены возможности, поддерживаемые СУБД; Вместо этого при установке обновленного драйвера, приложение автоматически использует возможности потому что его код определенные функции, не относящиеся к драйверу или СУБД.
