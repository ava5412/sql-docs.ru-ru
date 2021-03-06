---
title: Получение данных сведения о типе с SQLGetTypeInfo | Документы Microsoft
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
- SQL data types [ODBC], identifiers
- SQLGetTypeInfo function [ODBC], retrieving data type information
- retrieving data type information [ODBC]
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d764d8470343d67bd37c1ef7ce5dcf15962079e9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912559"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Получение типа данных при помощи SQLGetTypeInfo
Поскольку приблизительны сопоставления из базовых типов данных SQL для идентификаторов типа ODBC, ODBC представляет собой функцию (**SQLGetTypeInfo**), через который полностью можно драйвер описания каждого типа данных SQL в источнике данных. Эта функция возвращает результирующий набор, каждая строка описывает характеристики одного типа, такие как имя, идентификатор типа, точность, масштаб и допустимость значений NULL.  
  
 Эти сведения обычно используется универсальные приложения, которые пользователи могут создавать и изменять таблицы. Такие приложения вызывают **SQLGetTypeInfo** извлечь сведения о типе данных и затем представить некоторые или все его пользователю. Такие приложения должны иметь в виду следующее:  
  
-   Более чем один тип данных SQL можно сопоставить с одним типом идентификатора, который может сделать его трудно определить, какой тип данных для использования. Чтобы устранить эту проблему, результирующий набор, упорядочены сначала по идентификатору типа, во втором по близости для определения идентификатора типа. Кроме того типы данных — определить источник данных имеют приоритет над определяемым пользователем типам данных. Например предположим, что источник данных определяет типы данных INTEGER и СЧЕТЧИК должны совпадать, за исключением того, что СЧЕТЧИК является автоматическим приращением. Также предположим, что определяемый пользователем тип WHOLENUM является синонимом целого числа со знаком. SQL_INTEGER сопоставляет каждый из этих типов. В **SQLGetTypeInfo** результирующего набора, целое число отображается во-первых, следуют WHOLENUM и затем СЧЕТЧИКА. WHOLENUM отображается после целое число со знаком, так как он определяется пользователем, но перед СЧЕТЧИКА так как он более точно соответствует определению SQL_INTEGER идентификатор типа.  
  
-   ODBC не определяет имена типов данных для использования в **CREATE TABLE** и **ALTER TABLE** инструкции. Вместо этого приложение должно использовать имя, возвращаемое в столбце TYPE_NAME результирующего набора, возвращаемого **SQLGetTypeInfo**. Это обусловлено тем, что несмотря на то, что большинство SQL не меняется большая между СУБД, имена типов данных очень различаются. Вместо того, драйверы для синтаксического анализа инструкций SQL и замените имена типов данных стандартные имена типов данных СУБД, ODBC требует, чтобы в первую очередь используются имена СУБД конкретного приложения.  
  
 Обратите внимание, что **SQLGetTypeInfo** не описываются все типы данных, приложение может возникнуть обязательно. В частности результирующие наборы могут содержать типы данных, не поддерживаемого непосредственно компонентом источника данных. Например типы данных столбцов в результирующие наборы, возвращаемые функциями каталога определяются ODBC и возможно, эти типы данных не поддерживается источником данных. Чтобы определить характеристики типов данных в результирующем наборе, приложение вызывает **SQLColAttribute**.
