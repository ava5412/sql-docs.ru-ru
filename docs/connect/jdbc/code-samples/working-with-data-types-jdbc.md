---
title: Работа с типами данных (JDBC) | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 857f05430f963e085d47fad633d0039e2bbd7fb2
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39453098"
---
# <a name="working-with-data-types-jdbc"></a>Работа с типами данных (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Основная функция [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] — предоставить разработчикам на Java доступ к данным в базах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. С этой целью драйвер JDBC контролирует преобразование между типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] и типами и объектами языка Java.  
  
> [!NOTE]  
> Подробные сведения о типах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] и драйвера JDBC, в том числе об их отличиях и о преобразовании в типы данных языка Java, см. в статье [Основные сведения о типах данных драйвера JDBC](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
Для совместимости с типами данных SQL Server драйвер JDBC предоставляет методы get\<Type> и set\<Type> для классов [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md), а также методы get\<Type> и update\<Type> для класса [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md). Применяемый метод зависит от типа обрабатываемых данных, а также от использования либо результирующих наборов, либо запросов.  
  
В этом разделе описано использование типов данных драйвера JDBC для доступа к данным [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в приложениях Java.  
  
## <a name="in-this-section"></a>в этом разделе  
  
| Раздел                                                                         | Описание                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Пример базовых типов данных](../../../connect/jdbc/code-samples/basic-data-types-sample.md)   | Описывает использование методов получения результирующих наборов для извлечения значений с базовыми типами данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], а также применение методов обновления результирующего набора для изменения этих значений.                                             |
| [Пример типа данных SQLXML](../../../connect/jdbc/code-samples/sqlxml-data-type-sample.md)   | Описывает сохранение данных XML в реляционной базе данных, их извлечение из базы и выполнение их анализа с помощью типа данных Java **SQLXML**.                                                                                   |
| [Пример пространственных типов данных](../../../connect/jdbc/code-samples/spatial-data-types-sample.md) | Описывает, как хранить Пространственные типы данных в SQL Server и как получить эти типы из SQL Server. Также описывается, как использовать новые определенные классы **Geometry** и **Geography** от драйвера, для управления Справочник по Java из этих типов данных. |
  
## <a name="see-also"></a>См. также:

[Пример приложений драйвера JDBC](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
