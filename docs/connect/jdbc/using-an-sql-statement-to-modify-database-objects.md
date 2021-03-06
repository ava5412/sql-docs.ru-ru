---
title: Использование инструкции SQL для изменения объектов баз данных | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3386121432f918ef447f5d3ad1f4ff79a64c681
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662446"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Использование инструкции SQL для изменения объектов баз данных 

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Для изменения объектов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с использованием инструкции SQL можно использовать метод [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Метод executeUpdate передаст инструкцию SQL базе данных для обработки, а затем возвратит значение 0, так как не было затронуто ни одной строки.

Для этого сначала нужно создать объект SQLServerStatement с помощью метода [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

> [!NOTE]  
> Инструкции SQL, изменяющие объекты в базе данных, называются инструкциями языка описания данных DDL. К ним относятся инструкции, такие как `CREATE TABLE`, `DROP TABLE`, `CREATE INDEX`, и `DROP INDEX`. Дополнительные сведения о типах инструкций DDL, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], см. в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].

В приведенном ниже примере функции передается открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], составляется инструкция SQL, которая создаст простую таблицу TestTable в базе данных, а затем инструкция выполняется, и выводится возвращаемое значение.

[!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]

## <a name="see-also"></a>См. также:

[Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)
