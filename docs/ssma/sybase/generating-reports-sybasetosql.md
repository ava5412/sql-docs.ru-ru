---
title: Создание отчетов (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,generating reports
- Sybase Console,refresh-from-database report
- Sybase Console,synchronize-target report
ms.assetid: 19278f6a-6d58-4867-9d71-c6228040466e
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5f5f64d418bd99b3403534db19c770f475d089ee
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34778640"
---
# <a name="generating-reports-sybasetosql"></a>Создание отчетов (SybaseToSQL)
Отчеты определенные действия, выполняемые с помощью команды создаются в консоли SSMA на уровне дерева объектов.  
  
Используйте следующую процедуру для создания отчетов:  
  
1.  Укажите **записи — Сводка отчет в** параметра. Связанный отчет хранится в качестве имени файла (Если указан), или задать в папке. Имя файла системы предопределенные как упоминалось в таблице ниже where, **&lt;n&gt;** файлу уникальное число, которое увеличивает цифрой при каждом выполнении той же команде.  
  
    Команды vis à по диагонали отчеты представляют собой.  
  
    ||||  
    |-|-|-|  
    |**SL. Нет.**|**Command**|**Заголовок отчета**|  
    |1|Создание оценки отчета|AssessmentReport&lt;n&gt;. XML|  
    |2|преобразовать схему|SchemaConversionReport&lt;n&gt;. XML|  
    |3|Перенос данных|DataMigrationReport&lt;n&gt;. XML|  
    |4|оператор CONVERT-sql|ConvertSQLReport&lt;n&gt;. XML|  
    |5|синхронизировать целевой|TargetSynchronizationReport&lt;n&gt;. XML|  
    |6|обновление из базы данных|SourceDBRefreshReport&lt;n&gt;. XML|  
  
    > [!IMPORTANT]  
    > В выходной отчет отличается от отчета оценки. В первом — отчета о производительности во время выполнения команды, во втором случае выполняется отчет в формате XML для программный потребления.  
  
    Для параметров вывода отчетов за (Sl. Нет. 2-4 выше), см. [выполнение консоли SSMA &#40;SybaseToSQL&#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) раздела.  
  
2.  Укажите степень детализации при работе на данные в отчете с помощью параметров детализации отчета:  
  
    ||||  
    |-|-|-|  
    |**SL. Нет.**|**Команд и параметров**|**Описание выходных данных**|  
    |1|verbose = «false»|Формирует сводный отчет по действия.|  
    |2|verbose = «true»|Создает отчет о состоянии сводные и подробные для каждого действия.|  
  
    > [!NOTE]  
    > Создание оценки отчета, преобразовать схемы, перенос данных, команды sql инструкцию convert применяются параметры детализации отчета, указанных выше.  
  
3.  Укажите степень детализации при работе с отчетами об ошибках, с помощью параметров отчетов об ошибках:  
  
    ||||  
    |-|-|-|  
    |**SL. Нет.**|**Команд и параметров**|**Описание выходных данных**|  
    |1|ошибки отчета = «false»|Нет сведений об ошибке / предупреждение / сведения о сообщениях.|  
    |2|ошибки отчета = «true»|Подробные сведения об ошибке / предупреждение / сведения о сообщениях.|  
  
    > [!NOTE]  
    > Параметры отчета об ошибках указанных выше применимы для создание оценки отчета, convert схемы, перенос данных, команды sql инструкцию convert.  
  
```xml  
<generate-assessment-report  
  
    object-name="<object-name>"  
  
    object-type="<object-type>"  
  
    verbose="<true/false>"  
  
    report-erors="<true/false>"  
  
    write-summary-report-to="<file-name/folder-name>"  
  
    assessment-report-folder="<folder-name>"  
  
    assessment-report-overwrite="<true/false>"  
  
/>  
```  
  
### <a name="synchronize-target"></a>синхронизировать целевой:  
Команда **синхронизировать целевой** имеет **отчета ошибки в** параметр, который указывает расположение отчет об ошибках для операции синхронизации. Затем файл с именем **TargetSynchronizationReport&lt;n&gt;. XML** создается в указанном месте, где **&lt;n&gt;** файлу уникальное число, которое увеличивает цифрой при каждом выполнении той же команде.  
  
**Примечание:** Если задан путь к папке, то параметр «отчета ошибки в» становится необязательным атрибутом для команды «синхронизировать-целевой объект».  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
    object-name="<object-name>"  
  
    on-error="<object-type>"  
  
    report-errors-to="<file-name/folder-name>"  
  
/>  
```  
**Имя объекта:** указывает один или несколько объектов, для синхронизации (он также может иметь имена пометку отдельных объектов или имя объекта группы).  
  
**в случае ошибки:** указывает, следует ли указать ошибок синхронизации в качестве предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
-   всего отчета как предупреждения  
  
-   отчет each как предупреждение  
  
-   Сбой скрипта  
  
### <a name="refresh-from-database"></a>обновление с-база данных:  
Команда **обновление из базы данных** имеет **отчета ошибки в** параметр, который указывает расположение отчет об ошибках для операции обновления. Затем файл с именем **SourceDBRefreshReport&lt;n&gt;. XML** создается в указанном месте, где **&lt;n&gt;** файлу уникальное число, которое увеличивает цифрой при каждом выполнении той же команде.  
  
**Примечание:** Если задан путь к папке, то параметр «отчета ошибки в» становится необязательным атрибутом для команды «синхронизировать-целевой объект».  
  
```xml  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
    object-name="<object-name>"  
  
    object-type ="<object-type>"  
  
    on-error="report-total-as-warning/report-each-as-warning/fail-script"  
  
    report-errors-to="<file-name/folder-name> "  
  
/>  
```  
**Имя объекта:** указывает один или несколько объектов, для обновления (он также может иметь имена пометку отдельных объектов или имя объекта группы).  
  
**в случае ошибки:** указывает, следует ли указать ошибки обновления в качестве предупреждения или ошибки. Доступные варианты в случае ошибки:  
  
-   всего отчета как предупреждения  
  
-   отчет each как предупреждение  
  
-   Сбой скрипта  
  
## <a name="see-also"></a>См. также  
[Выполнение консоли SSMA (Sybase)](http://msdn.microsoft.com/en-us/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
