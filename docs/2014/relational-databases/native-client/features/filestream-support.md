---
title: Поддержка FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b499fee530484c14297d04cc6ffe8db38983e214
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424333"
---
# <a name="filestream-support"></a>Поддержка FILESTREAM
  Компонент FILESTREAM предоставляет способ хранения и доступа к большим двоичным значениям либо с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], либо путем непосредственного доступа к файловой системе Windows. Большим двоичным значением считается значение с размером больше 2 гигабайт (ГБ). Дополнительные сведения о поддержке усовершенствованного компонента FILESTREAM, см. в разделе [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md).  
  
 После открытия подключения к базе данных параметр `@@TEXTSIZE` устанавливается в значение -1 («неограниченный») по умолчанию.  
  
 Предусмотрена также возможность получения доступа и обновления столбцов FILESTREAM с помощью API файловой системы Windows.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Поддержка FILESTREAM &#40;OLE DB&#41;](../ole-db/filestream-support-ole-db.md)  
  
-   [Поддержка FILESTREAM &#40;ODBC&#41;](../odbc/filestream-support-odbc.md)  
  
-   [Доступ к данным FILESTREAM с OpenSqlFilestream](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Запрос столбцов FILESTREAM  
 Наборы строк схемы в OLE DB не сообщают, является ли столбец столбцом FILESTREAM. ITableDefinition в OLE DB не может использоваться для создания столбца FILESTREAM.  
  
 Функций каталога, например SQLColumns в ODBC не сообщает, является ли столбец столбцом FILESTREAM.  
  
 Чтобы создать столбцы FILESTREAM или обнаружить, какие существующие столбцы являются столбцами FILESTREAM, можно использовать `is_filestream` столбец [sys.columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) представления каталога.  
  
 Ниже представлен пример такого кода:  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Совместимость на низком уровне  
 Если клиент был скомпилирован с помощью версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, которая поставляется с сервером [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)], `varbinary(max)` поведение будут совместимы с [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Это означает, что максимальный размер возвращаемых данных будет ограничен 2 ГБ. Для результирующих значений больше 2 ГБ произойдет усечение и будет возвращено сообщение «усечение строковых данных справа».  
  
 Если уровень совместимости типов данных установлен равным «80», то поведение клиента будет согласовано с поведением клиента низкого уровня.  
  
 Для клиентов, которые используют SQLOLEDB или другие поставщики, выпущенные до [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] Native Client, `varbinary(max)` будут сопоставлены к образу.  
  
## <a name="see-also"></a>См. также  
 [Компоненты SQL Server Native Client](sql-server-native-client-features.md)  
  
  
