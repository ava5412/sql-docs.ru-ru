---
title: Сохранение результатов трассировки в файл | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 74f80667-62f3-4e14-bb1a-f0c2b6ef3402
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b9b465fda2e3deb6b0e98c6f649ce5bc226458f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232974"
---
# <a name="save-trace-results-to-a-file"></a>Сохранение результатов трассировки в файл
  Результаты трассировки можно сохранить в файле. Файл трассировки — это файл, в который записаны результаты трассировки. Файл трассировки может находиться в локальном каталоге (например, C:\\*имя_папки*\\*имя_файла.trc*) или в сетевом (например, \\\имя_компьютера\сетевое_имя\имя_файла.trc).  
  
 Файлы трассировки можно применять для:  
  
-   воспроизведения трассировок;  
  
-   Аудит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   выполнения анализа производительности;  
  
-   сравнения событий трассировки со счетчиками производительности для улучшения распознавания неполадок;  
  
-   выполнения анализа при помощи помощника по настройке ядра СУБД;  
  
-   оптимизации запросов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет результаты трассировки в файле, путь и имя которого указываются в качестве аргумента **@tracefile** хранимой процедуры **sp_trace_create**.  
  
> [!NOTE]  
>  Если для сохранения файла трассировки хранимой процедуре **sp_trace_create** передается путь к файлу, то этот каталог должен быть доступен серверу. Также помните, что если процедуре **sp_trace_create**передается путь к локальному каталогу, то это локальный каталог на данном сервере.  
  
 Если используется [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , результаты трассировки можно сохранить в файле или в таблице. Сохранение результатов трассировки в таблице обеспечивает такой же доступ, как и при сохранении трассировки в файле; помимо этого, для поиска определенных событий можно выполнять запросы к этой таблице.  
  
 Дополнительные сведения о сохранении результатов трассировки см. в разделах [Сохранить результаты трассировки в таблицу (приложение SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) и [Сохранить результаты трассировки в файл (приложение SQL Server Profiler)](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md).  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_create (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)   
 [Создание трассировки (Transact-SQL)](../sql-trace/create-a-trace-transact-sql.md)   
 [Создание трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
