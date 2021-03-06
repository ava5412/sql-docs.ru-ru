---
title: Указание типа хранилища файлов с помощью программы bcp (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fff9084513f21333125eaee8995eebfd3e22e1a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251996"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a>Указание типа файлового хранилища с помощью программы bcp (SQL Server)
  *Тип файла хранилища* описывает, каким образом данные хранятся в файле данных. Данные можно экспортировать в файл данных формате таблиц баз данных (собственный формат), в символьном представлении (символьный формат) или в виде любого типа данных, где поддерживается неявное преобразование; Например, копирование `smallint` как `int`. Пользовательские типы данных экспортируются так же, как их базовые типы.  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a>Приглашение bcp указать тип файлового хранилища  
 Если интерактивная команда **bcp** содержит параметр **in** или **out** без параметра файла форматирования (**-f**) или параметра формата данных (**-n**, **-c**, **-w**или **-N**), команда запрашивает тип файлового хранилища для каждого поля данных следующим образом:  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 Ответ на такое приглашение зависит от выполняемой задачи.  
  
-   Для массового экспорта данных из экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в файл данных в наиболее компактном хранилище (собственный формат данных) примите типы файловых хранилищ по умолчанию, которые предлагает программа **bcp**. Список собственных типов файловых хранилищ см. в разделе «Собственные типы файловых хранилищ» далее в этом подразделе.  
  
-   Для массового экспорта данных из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в файл данных в символьном формате укажите `char` в качестве типа файлового хранилища для всех столбцов в таблице.  
  
-   Для массового импорта данных в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из файла данных, указание типа файлового хранилища, как `char` для типов, хранящихся в символьном формате, а для данных, хранящихся в формате собственного типа данных, укажите один из типов файлового хранилища, соответствующим образом:  
  
    |Тип файла хранилища|Введите в командной строке|  
    |-----------------------|-----------------------------|  
    |`char` <sup>1</sup>|`c`[`har`]|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |`text` <sup>2</sup>|`T`[`ext`]|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |`image` <sup>2</sup>|`I`[`mage`]|  
    |`datetime`|**d[ate]**|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|**f[loat]**|  
    |`real`|`r`|  
    |`Int`|**i[nt]**|  
    |`bigint`|`B[igint]`|  
    |`smallint`|**s[mallint]**|  
    |`tinyint`|**t[inyint]**|  
    |`money`|**m[oney]**|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |`UDT` (пользовательский тип данных)|`U`|  
    |`XML`|`X`|  
  
     <sup>1</sup> взаимосвязь длины поля, длины префикса и признаков конца определяет объем хранилища, выделяемый в файле данных для несимвольных данных, экспортируемых в качестве `char` типа файлового хранилища.  
  
     <sup>2</sup> `ntext`, `text`, и `image` типы данных будут удалены в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует избегать использования этих типов данных при новой разработке и запланировать изменение приложений, использующих их в настоящий момент. Используйте `nvarchar(max)`, `varchar(max)`, и `varbinary(max)` вместо этого.  
  
## <a name="native-file-storage-types"></a>Собственные типы файловых хранилищ  
 Все собственные типы файловых хранилищ записаны в файле форматирования как соответствующие типы данных основных файлов.  
  
|Тип файла хранилища|Тип данных файла|  
|-----------------------|-------------------------|  
|`char` <sup>1</sup>|SQLCHAR|  
|`varchar`|SQLCHAR|  
|`nchar`|SQLNCHAR|  
|`nvarchar`|SQLNCHAR|  
|`text` <sup>2</sup>|SQLCHAR|  
|`ntext` <sup>2</sup>|SQLNCHAR|  
|`binary`|SQLBINARY|  
|`varbinary`|SQLBINARY|  
|`image` <sup>2</sup>|SQLBINARY|  
|`datetime`|SQLDATETIME|  
|`smalldatetime`|SQLDATETIM4|  
|`decimal`|SQLDECIMAL|  
|`numeric`|SQLNUMERIC|  
|`float`|SQLFLT8|  
|`real`|SQLFLT4|  
|`int`|SQLINT|  
|`bigint`|SQLBIGINT|  
|`smallint`|SQLSMALLINT|  
|`tinyint`|SQLTINYINT|  
|`money`|SQLMONEY|  
|`smallmoney`|SQLMONEY4|  
|`bit`|SQLBIT|  
|`uniqueidentifier`|SQLUNIQUEID|  
|`sql_variant`|SQLVARIANT|  
|`timestamp`|SQLBINARY|  
|UDT (определяемый пользователем тип данных)|SQLUDT|  
  
 <sup>1</sup> файлов данных, хранящихся в символьном формате используйте `char` в качестве типа файлового хранилища. Таким образом, для символьных файлов данных SQLCHAR — это единственный тип данных, допустимый в файле форматирования.  
  
 <sup>2</sup> невозможно массово импортировать данные в `text`, `ntext`, и `image` столбцы, которые имеют значения по умолчанию.  
  
## <a name="additional-considerations-for-file-storage-types"></a>Дополнительные замечания относительно типов файловых хранилищ  
 При массовом экспорте данных из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в файл данных:  
  
-   можно указать в качестве типа файлового хранилища `char`;  
  
-   При вводе указан тип файлового хранилища, представляющий недопустимое неявное преобразование, **bcp** сбое; например, хотя можно указать `int` для `smallint` данных, если указать `smallint` для `int` данных, Ошибка переполнения.  
  
-   Когда несимвольные типы данных, такие как `float`, `money`, `datetime`, или `int` хранятся с использованием соответствующих типов баз данных, данные записываются в файл данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный формат.  
  
    > [!NOTE]  
    >  После интерактивного заполнения всех полей в команде **bcp** появится запрос на сохранение введенных ответов для каждого поля в файле форматирования в формате, отличном от XML. Дополнительные сведения о файлах форматирования в формате, отличном от XML, см. в разделе [Файлы формата, отличные от XML (SQL Server)](xml-format-files-sql-server.md).  
  
## <a name="see-also"></a>См. также  
 [Программа bcp](../../tools/bcp-utility.md)   
 [Типы данных (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)   
 [Указание длины поля с помощью программы bcp (SQL Server)](specify-field-length-by-using-bcp-sql-server.md)   
 [Определение признаков конца поля и строки (SQL Server)](specify-field-and-row-terminators-sql-server.md)   
 [Определение длины префикса в файлах данных с помощью программы bcp (SQL Server)](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
