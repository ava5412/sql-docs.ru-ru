---
title: Требования к системе для драйвера Microsoft PHP для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/23/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: 93
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9cfb813b857557a3a30bd89d9c96346ee261bc89
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174951"
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Системные требования драйверов Майкрософт для PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этом документе перечислены компоненты, которые должны быть установлены на компьютере для доступа к данным в SQL Server или базы данных SQL Azure с помощью [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

Официально поддерживаются версии 3.1 и более поздних версий драйверы Microsoft PHP для SQL Server. Подробные сведения о жизненном цикле поддержки и требования, включая более ранние версии драйверов PHP см. в разделе [Матрица поддержки](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Сведения о том, как скачать и установить актуальные и стабильные двоичные файлы, см. на [веб-сайте PHP](http://php.net).  Драйверы Майкрософт для PHP для SQL Server требуются следующие версии PHP:

|PHP для SQL Server версии драйвера&#8594;<br />&#8595; версия PHP|5.3 и 5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|7.2|7.2.1+ на платформе Windows<br/>7.2.0+ на других платформах | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |
|5.6|       |       |       |5.6.4+  |        |
|5.5|       |       |       |5.5.16+ |5.5.16+ |
|5.4|       |       |       |5.4.32  |5.4.32  |

-   Версия файла драйвера должна находиться в каталоге расширения PHP. См. в разделе [версии драйверов](#driver-versions) сведения о разных файлах драйвера.  Сведения о скачивании драйверов см. в статье [Драйверы Майкрософт для PHP для SQL Server](download-drivers-php-sql-server.md). Сведения о настройке драйвера для PHP см. в статье [Загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md).

-   Требуется веб-сервер. Веб-сервер должен быть настроен на выполнение PHP. Сведения о размещении приложений PHP с IIS, см. в разделе [учебник на веб-сайт на PHP](http://php.net/manual/fa/install.windows.iis.php).  

    [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] был протестирован в службе IIS 10 с помощью FastCGI.  

    > [!NOTE]  
    > Корпорация Майкрософт обеспечивает поддержку только для служб IIS.  

-   Версия 5.3 драйверы Майкрософт для PHP для SQL Server будет последней для поддержки PHP 7.0.

## <a name="odbc-driver"></a>Драйвер ODBC

Требуется правильная версия Microsoft ODBC Driver for SQL Server на компьютере, на котором выполняется PHP. Вы можете скачать все поддерживаемые версии драйвера для поддерживаемых платформ на [эту страницу](https://docs.microsoft.com/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-2017).

При загрузке Windows версию драйвера на 64-разрядной версии Windows ODBC 64-разрядный установщик устанавливает 32-разрядных и 64-разрядные драйверы ODBC. Если вы используете в 32-разрядной версии Windows, использующие ODBC x86 установщика. На платформах, отличных от Windows доступны только в 64-разрядные версии драйвера.

|PHP для SQL Server версии драйвера&#8594;<br />&#8595;Версия драйвера ODBC|5.3<br />&nbsp;|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|---|
|Драйвер ODBC 17+ |Да|Да| | | | |
|Драйвер ODBC 13.1|Да|Да|Да|Да| | |
|Драйвер ODBC 13  | | | |Да| | |
|Драйвер ODBC 11  |Да|Да|Да|Да|Да|Да|

Если вы используете драйвер SQLSRV, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) возвращает сведения о том, какая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Microsoft ODBC Driver for SQL Server, используемого [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Если вы используете драйвер PDO_SQLSRV, можно применить [PDO::getAttribute](../../connect/php/pdo-getattribute.md) для определения версии.  

## <a name="sql-server"></a>SQL Server

Поддерживаются базы данных SQL Azure. Дополнительные сведения см. в статье [Подключение к базе данных Microsoft Azure SQL](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|PHP для SQL Server версии драйвера&#8594;<br />&#8595; версия SQL Server|5.3<br />&nbsp;|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|---|
|База данных SQL Azure        |Да|Да|Да| | | |
|Управляемый экземпляр SQL Azure|Да|Да|Да| | | |
|Хранилище данных SQL Azure  |Да|Да|Да| | | |
|SQL Server 2017           |Да|Да|Да| | | |
|SQL Server 2016           |Да|Да|Да|Да| | |
|SQL Server 2014           |Да|Да|Да|Да|Да|Да|
|SQL Server 2012           |Да|Да|Да|Да|Да|Да|
|SQL Server 2008 R2        |Да|Да|Да|Да|Да|Да|
|SQL Server 2008           | | | |Да|Да|Да|

## <a name="operating-systems"></a>Операционные системы
Ниже приведены поддерживаемые операционные системы для версии драйвера.

|PHP для SQL Server версии драйвера&#8594;<br />&#8595; операционная система|5.3<br />&nbsp;|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|---|
|Windows Server 2016                      |Да|Да|Да| | | |
|Windows Server 2012 R2                   |Да|Да|Да|Да|Да|Да|
|Windows Server 2012                      |Да|Да|Да|Да|Да|Да|
|Windows Server 2008 R2 с пакетом обновления 1 (SP1)               | | | |Да|Да|Да|
|Windows Server 2008 с пакетом обновления 2 (SP2)                  | | | |Да|Да|Да|
|Windows 10                               |Да|Да|Да|Да| | |
|Windows 8.1                              |Да|Да|Да|Да|Да|Да|
|Windows 8                                | | |Да|Да|Да|Да|
|Windows 7 с пакетом обновления 1 (SP1)                            | | | |Да|Да|Да|
|Windows Vista с пакетом обновления 2 (SP2)                        | | | |Да|Да|Да|
|Ubuntu 18.04 (64-разрядная версия)                    |Да| | | | | |
|Ubuntu 17.10 (64-разрядная версия)                    |Да|Да| | | | |
|Ubuntu 16.04 (64-разрядная версия)                    |Да|Да|Да|Да| | |
|Ubuntu 15.10 (64-разрядная версия)                    | | |Да| | | |
|Ubuntu 15.04 (64-разрядная версия)                    | | | |Да| | |
|Debian 9 (64-разрядная версия)                        |Да|Да| | | | |
|Debian 8 (64-разрядная версия)                        |Да|Да|Да| | | |
|Red Hat Enterprise Linux 7 (64-разрядная версия)      |Да|Да|Да|Да| | |
|SuSE Enterprise Linux 12 (64-разрядная версия)        |Да|Да| | | | |
|macOS High Sierra (64-разрядная версия)               |Да| | | | | |
|macOS Sierra (64-разрядная версия)                    |Да|Да|Да| | | |
|macOS El Capitan (64-разрядная версия)                |Да|Да|Да| | | |

## <a name="driver-versions"></a>Версии драйвера  
В этом разделе перечислены файлы драйверов, которые входят в состав каждой версии [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Каждый пакет установки содержит файлы драйвера SQLSRV и PDO_SQLSRV потоками и однопоточных варианта. В Windows они также доступны в 32-разрядных и 64-разрядных вариантов. Чтобы настроить драйвер для использования в среде выполнения PHP, следуйте инструкциям по установке в [загрузка драйверов Майкрософт для PHP для SQL Server](../../connect/php/loading-the-php-sql-driver.md).

В поддерживаемых версиях Linux и macOS, соответствующие драйверы можно установить с помощью PHP PECL пакета системы, следуя [инструкции по установке Linux и macOS](../../connect/php/installation-tutorial-linux-mac.md). Кроме того, можно загрузить предварительно созданные двоичные файлы для вашей платформы из [драйверы Майкрософт для PHP для SQL Server](https://github.com/Microsoft/msphpsql/releases) странице проекта Github--в таблицах ниже перечислены файлы, обнаруженные в предварительно созданные двоичные пакеты.

**Драйверы Майкрософт версии 5.3 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|32-разрядных php_sqlsrv_7_nts.dll <br />32-разрядных php_pdo_sqlsrv_7_nts.dll |7.0|нет |32-разрядных php7.dll|
|32-разрядных php_sqlsrv_7_ts.dll  <br />32-разрядных php_pdo_sqlsrv_7_ts.dll  |7.0|да|32-разрядных php7ts.dll|
|64-разрядных php_sqlsrv_7_nts.dll <br />64-разрядных php_pdo_sqlsrv_7_nts.dll |7.0|нет |64-разрядных php7.dll|  
|64-разрядных php_sqlsrv_7_ts.dll  <br />64-разрядных php_pdo_sqlsrv_7_ts.dll  |7.0|да|64-разрядных php7ts.dll|
|32-разрядных php_sqlsrv_71_nts.dll<br />32-разрядных php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядных php7.dll|  
|32-разрядных php_sqlsrv_71_ts.dll <br />32-разрядных php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядных php7ts.dll|  
|64-разрядных php_sqlsrv_71_nts.dll<br />64-разрядных php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядных php7.dll|  
|64-разрядных php_sqlsrv_71_ts.dll <br />64-разрядных php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядных php7ts.dll|   
|32-разрядных php_sqlsrv_72_nts.dll<br />32-разрядных php_pdo_sqlsrv_72_nts.dll|7.2|нет |32-разрядных php7.dll|  
|32-разрядных php_sqlsrv_72_ts.dll <br />32-разрядных php_pdo_sqlsrv_72_ts.dll |7.2|да|32-разрядных php7ts.dll|  
|64-разрядных php_sqlsrv_72_nts.dll<br />64-разрядных php_pdo_sqlsrv_72_nts.dll|7.2|нет |64-разрядных php7.dll|  
|64-разрядных php_sqlsrv_72_ts.dll <br />64-разрядных php_pdo_sqlsrv_72_ts.dll |7.2|да|64-разрядных php7ts.dll|  

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.SO <br />php_pdo_sqlsrv_7_nts.SO |7.0|нет |
|php_sqlsrv_7_ts.SO  <br />php_pdo_sqlsrv_7_ts.SO  |7.0|да|
|php_sqlsrv_71_nts.SO<br />php_pdo_sqlsrv_71_nts.SO|7.1|нет |
|php_sqlsrv_71_ts.SO <br />php_pdo_sqlsrv_71_ts.SO |7.1|да|  
|php_sqlsrv_72_nts.SO<br />php_pdo_sqlsrv_72_nts.SO|7.2|нет |
|php_sqlsrv_72_ts.SO <br />php_pdo_sqlsrv_72_ts.SO |7.2|да|

**Драйверы Майкрософт версии 5.2 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|32-разрядных php_sqlsrv_7_nts.dll <br />32-разрядных php_pdo_sqlsrv_7_nts.dll |7.0|нет |32-разрядных php7.dll|
|32-разрядных php_sqlsrv_7_ts.dll  <br />32-разрядных php_pdo_sqlsrv_7_ts.dll  |7.0|да|32-разрядных php7ts.dll|
|64-разрядных php_sqlsrv_7_nts.dll <br />64-разрядных php_pdo_sqlsrv_7_nts.dll |7.0|нет |64-разрядных php7.dll|  
|64-разрядных php_sqlsrv_7_ts.dll  <br />64-разрядных php_pdo_sqlsrv_7_ts.dll  |7.0|да|64-разрядных php7ts.dll|
|32-разрядных php_sqlsrv_71_nts.dll<br />32-разрядных php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядных php7.dll|  
|32-разрядных php_sqlsrv_71_ts.dll <br />32-разрядных php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядных php7ts.dll|  
|64-разрядных php_sqlsrv_71_nts.dll<br />64-разрядных php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядных php7.dll|  
|64-разрядных php_sqlsrv_71_ts.dll <br />64-разрядных php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядных php7ts.dll|   
|32-разрядных php_sqlsrv_72_nts.dll<br />32-разрядных php_pdo_sqlsrv_72_nts.dll|7.2|нет |32-разрядных php7.dll|  
|32-разрядных php_sqlsrv_72_ts.dll <br />32-разрядных php_pdo_sqlsrv_72_ts.dll |7.2|да|32-разрядных php7ts.dll|  
|64-разрядных php_sqlsrv_72_nts.dll<br />64-разрядных php_pdo_sqlsrv_72_nts.dll|7.2|нет |64-разрядных php7.dll|  
|64-разрядных php_sqlsrv_72_ts.dll <br />64-разрядных php_pdo_sqlsrv_72_ts.dll |7.2|да|64-разрядных php7ts.dll|  

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.SO <br />php_pdo_sqlsrv_7_nts.SO |7.0|нет |
|php_sqlsrv_7_ts.SO  <br />php_pdo_sqlsrv_7_ts.SO  |7.0|да|
|php_sqlsrv_71_nts.SO<br />php_pdo_sqlsrv_71_nts.SO|7.1|нет |
|php_sqlsrv_71_ts.SO <br />php_pdo_sqlsrv_71_ts.SO |7.1|да|  
|php_sqlsrv_72_nts.SO<br />php_pdo_sqlsrv_72_nts.SO|7.2|нет |
|php_sqlsrv_72_ts.SO <br />php_pdo_sqlsrv_72_ts.SO |7.2|да|

**Драйверы Майкрософт версии 4.3 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|32-разрядных php_sqlsrv_7_nts.dll <br />32-разрядных php_pdo_sqlsrv_7_nts.dll |7.0|нет |32-разрядных php7.dll|
|32-разрядных php_sqlsrv_7_ts.dll  <br />32-разрядных php_pdo_sqlsrv_7_ts.dll  |7.0|да|32-разрядных php7ts.dll|
|64-разрядных php_sqlsrv_7_nts.dll <br />64-разрядных php_pdo_sqlsrv_7_nts.dll |7.0|нет |64-разрядных php7.dll|  
|64-разрядных php_sqlsrv_7_ts.dll  <br />64-разрядных php_pdo_sqlsrv_7_ts.dll  |7.0|да|64-разрядных php7ts.dll|
|32-разрядных php_sqlsrv_71_nts.dll<br />32-разрядных php_pdo_sqlsrv_71_nts.dll|7.1|нет |32-разрядных php7.dll|  
|32-разрядных php_sqlsrv_71_ts.dll <br />32-разрядных php_pdo_sqlsrv_71_ts.dll |7.1|да|32-разрядных php7ts.dll|  
|64-разрядных php_sqlsrv_71_nts.dll<br />64-разрядных php_pdo_sqlsrv_71_nts.dll|7.1|нет |64-разрядных php7.dll|  
|64-разрядных php_sqlsrv_71_ts.dll <br />64-разрядных php_pdo_sqlsrv_71_ts.dll |7.1|да|64-разрядных php7ts.dll|   

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.SO <br />php_pdo_sqlsrv_7_nts.SO |7.0|нет |
|php_sqlsrv_7_ts.SO  <br />php_pdo_sqlsrv_7_ts.SO  |7.0|да|
|php_sqlsrv_71_nts.SO<br />php_pdo_sqlsrv_71_nts.SO|7.1|нет |
|php_sqlsrv_71_ts.SO <br />php_pdo_sqlsrv_71_ts.SO |7.1|да|  

**Драйверы Майкрософт версии 4.0 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|нет|32-разрядных php7.dll|  
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|да|32-разрядных php7ts.dll|  
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|нет|64-разрядных php7.dll|  
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|да|64-разрядных php7ts.dll|   

В Linux включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.SO <br />php_pdo_sqlsrv_7_nts.SO |7.0|нет |
|php_sqlsrv_7_ts.SO  <br />php_pdo_sqlsrv_7_ts.SO  |7.0|да|

**Драйверы Майкрософт версии 3.2 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|нет|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|да|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|нет|php5.dll|  
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|да|php5ts.dll|  

**Драйверы Майкрософт версии 3.1 для PHP для SQL Server:**  

В Windows включены следующие версии драйвера:

|Файл драйвера|Версия PHP|Является потокобезопасным?|Использование с DLL PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|нет|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|да|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|нет|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|да|php5ts.dll|  

## <a name="see-also"></a>См. также:  
[Приступая к работе с драйверами Майкрософт для PHP для SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Справочник по API драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
