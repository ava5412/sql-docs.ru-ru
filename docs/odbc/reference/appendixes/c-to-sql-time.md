---
title: 'C в SQL: время | Документы Microsoft'
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
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 381a0ee578b17c37c5646e495025a17538956085
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906119"
---
# <a name="c-to-sql-time"></a>C в SQL: время
Идентификатор для типа данных ODBC C времени является:  
  
 SQL_C_TYPE_TIME  
  
 Следующая таблица показывает ODBC SQL типы данных, к которым может быть преобразован данных C времени. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца в байтах > = 8<br /><br /> Столбец с длиной < 8 байт<br /><br /> Значение данных не является допустимым времени|н/д<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина столбца символ > = 8<br /><br /> Длина < 8 символов столбца<br /><br /> Значение данных не является допустимым времени|н/д<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Значение данных является действительным значением времени<br /><br /> Значение данных не является допустимым времени|н/д<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Значение данных является действительным значением времени []<br /><br /> Значение данных не является допустимым времени|н/д<br /><br /> 22007|  
  
 [a] дату часть отметка времени имеет значение текущей даты и долей секунды, часть отметка времени, установленным равным нулю.  
  
 Сведения о какие значения являются допустимыми в структуре SQL_C_TYPE_TIME см. в разделе [типы данных C](../../../odbc/reference/appendixes/c-data-types.md)ранее в этом приложении.  
  
 При преобразовании данных C времени в символьные данные SQL, результирующий символьных данных находится в «*hh*:*мм*:*ss*» формата.  
  
 Драйвер не учитывает значение длины и индикатора, при преобразовании данных из времени, тип данных C и предполагается, что размер буфера данных размер типа данных C времени. Переданное значение длины/индикатора *StrLen_or_Ind* аргумент в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумент в **SQLBindParameter**. Буфер данных задается с помощью *DataPtr* аргумент в **SQLPutData** и *ParameterValuePtr* аргумент в **SQLBindParameter**.
