---
title: Устранение неполадок с модульными тестами базы данных SQL Server | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cf4c9cd1-7e73-4c3b-922a-68b9247e7b33
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0fa8e6a9e4d23c74a6908d645d422b37db1f7f36
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088456"
---
# <a name="troubleshooting-sql-server-database-unit-testing-issues"></a>Устранение неполадок модульных тестов базы данных SQL Server
При работе с тестированиями модулей SQL Server для базы данных у вас могут возникнуть проблемы, описанные в этом разделе:  
  
-   [Изменения тестирования модулей и файла App.Config не учитываются при выполнении тестирований модулей](#UnitTestingAndAppConfigChanges)  
  
-   [При выполнении тестирований модулей база данных развертывается в непредвиденном расположении](#DatabaseDeploymentInUnitTests)  
  
-   [Истечение времени ожидания при выполнении тестов единиц базы данных](#TimeoutsDuringUnitTests)  
  
## <a name="UnitTestingAndAppConfigChanges"></a>Изменения тестирования модулей и файла App.Config не учитываются при выполнении тестирований модулей  
Если в тестовом проекте в файл App.Config вносятся изменения, для вступления этих изменений в силу проект необходимо построить повторно. Сюда также входят изменения, которые вносятся в файл App.Config с помощью диалогового окна **Конфигурация теста SQL Server**. Если не выполнить повторное построение проекта тестов, изменения не будут приведены при запуске модульных тестов.  
  
## <a name="DatabaseDeploymentInUnitTests"></a>При выполнении тестирований модулей база данных развертывается в непредвиденном расположении  
При развертывании базы данных из проекта базы данных, когда выполняются модульные тесты, база данных развертывается с помощью данных строки подключения, заданной в конфигурации тестирования модулей. Данные подключения, указанные в свойствах "Отладка" проекта базы данных, для этой задачи не используются, что позволяет выполнять тестирования модулей SQL Server разных экземпляров одной и той же базы данных.  
  
## <a name="TimeoutsDuringUnitTests"></a>Истечение времени ожидания при выполнении тестов единиц базы данных  
Если выполнить тесты единиц базы данных не удается из-за истечения времени ожидания, можно увеличить период времени ожидания, внеся изменение в файл app.config тестового проекта. Время ожидания подключения, заданное в строке подключения, указывает, сколько можно ждать, когда тестирование модулей устанавливает соединение с сервером. Время ожидания команды, которое должно задаваться непосредственно в файле app.config, указывает, сколько можно ждать в то время, когда тестирование модулей выполняет скрипт Transact\-SQL. Если вы испытываете проблемы с тестированиями модулей, на выполнение которых требуется длительное время, попробуйте увеличить значение времени ожидания команды в контексте соответствующего элемента. Например, чтобы задать время ожидания команды в 120 секунд для элемента **PrivilegedContext**, внесите в файл app.config следующие изменения:  
  
```  
<SqlUnitTesting_VS2010>  
    <DatabaseDeployment DatabaseProjectFileName="..\..\..\..\..\..\Visual Studio 2010\Projects\Database10\Database10\AdventureWorks.sqlproj"  
        Configuration="Debug" />  
    <DataGeneration ClearDatabase="true" />  
    <ExecutionContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(LocalDB)\Projects;Initial Catalog=AdventureWorks_Test;Integrated Security=True;Pooling=False"  
        CommandTimeout="30" />  
    <PrivilegedContext Provider="System.Data.SqlClient" ConnectionString="Data Source=(LocalDB)\Projects;Initial Catalog=AdventureWorks_Test;Integrated Security=True;Pooling=False"  
        CommandTimeout="120" />  
</SqlUnitTesting_VS2010>  
```  
  
## <a name="see-also"></a>См. также:  
[Практическое руководство. Создание модульных тестов SQL Server для функций, триггеров и хранимых процедур](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md)  
[Практическое руководство. Настройка запуска модульного теста SQL Server](../ssdt/how-to-configure-sql-server-unit-test-execution.md)  
  
