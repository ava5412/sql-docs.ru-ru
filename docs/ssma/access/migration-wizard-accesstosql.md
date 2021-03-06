---
title: Мастер миграции (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Migration Wizard dialog box
- Migration Wizard, adding Access databases
- Migration Wizard, Connect to SQL Azure
- Migration Wizard, Connect to SQL Server
- Migration Wizard, Link Tables
- Migration Wizard, Migration status
- Migration Wizard, New Project
- Migration Wizard, Selecting objects to migrate
ms.assetid: 5bab5914-b2ae-4795-8cf5-83e42d64bef2
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 52e29fb03a3bcc0436f69447caa4e96fc146c3a7
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985496"
---
# <a name="migration-wizard-accesstosql"></a>Мастер миграции (AccessToSQL)
Мастер миграции поможет выполнить перенос один или несколько баз данных с доступом к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. С помощью мастера, будет создание проекта, добавьте в проект базы данных, выберите объекты для переноса и подключитесь к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Также будет преобразовать, загрузить и перенести схем доступа и данные. При необходимости вы можете связать доступа к таблицам для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] таблиц или SQL Azure.  
  
Большинство страниц мастера миграции содержит существующие диалоговые окна SSMA с теми же параметрами. Таким образом здесь описываются страницы мастера, и затем приводятся ссылки, чтобы узнать подробнее об отдельных параметрах. Если страница содержит уникальные параметры, эти сведения приведены здесь.  
  
## <a name="starting-the-migration-wizard"></a>Запуск мастера миграции  
По умолчанию мастер миграции отображается при запуске SSMA. Кроме того, мастер можно запустить на **файл** меню, выбрав **мастер миграции**.  
  
## <a name="welcome-page"></a>Страница приветствия  
Страница приветствия вводит мастер миграции и предоставляет следующий параметр для запуска мастера.  
  
**Запустите этот мастер при запуске.**  
По умолчанию SSMA будет запущен мастер миграции при запуске SSMA. Чтобы предотвратить автоматический запуск мастера, снимите этот флажок.  
  
## <a name="create-new-project-page"></a>Создать новую страницу проекта  
На странице Создание нового проекта вводится проекта имя, расположение и миграции проекта тип файла (версия целевого SQL Server, используемый для миграции). Дополнительные сведения см. в разделе [новый проект (SSMA)](http://msdn.microsoft.com/ca294f6d-eeb5-42ca-9306-156281a3f0f3)  
  
## <a name="add-access-databases-page"></a>Добавить страницу базы данных Access  
На странице добавления базы данных Access является, который можно добавить один или несколько баз данных Access в проект. Отдельные базы данных можно добавить, щелкнув **баз данных, добавить**и затем выбрав базы данных из **откройте** окна. Или можно найти базы данных с помощью **найти баз данных** кнопки. Дополнительные сведения см. в следующих разделах:  
  
-   [Добавление и удаление файлов баз данных Access](http://msdn.microsoft.com/e944c740-4c8a-4bc1-b0ed-be57bc06dced)  
  
-   [Мастер поиска баз данных (выбор расположений)](http://msdn.microsoft.com/00b2d32a-998b-47a7-b25c-589b5bd6777a)  
  
-   [Мастер поиска баз данных (Выбор файлов)](http://msdn.microsoft.com/2f574a34-4bab-40a4-89a8-ad4907ffc3fd)  
  
-   [Мастер поиска баз данных (проверка выбора)](http://msdn.microsoft.com/62e20e03-50cc-4ac8-8072-524d194d2ec3)  
  
## <a name="select-objects-to-migrate-page"></a>Выберите объекты для страниц  
На выбор объектов для миграции страницу выберите объекты для преобразования. Можно выбрать все объекты, группы объектов или отдельных объектов.  
  
**Для выбора объектов**  
  
1.  Разверните **доступа к метабазе**, а затем разверните **баз данных**.  
  
2.  Выполните одно или несколько из следующих:  
  
    -   Чтобы преобразовать все базы данных, установите флажок рядом с полем **баз данных**.  
  
    -   Чтобы преобразовать или пропустить отдельные базы данных, установите или снимите флажок рядом с именем базы данных.  
  
    -   Чтобы преобразовать или пропускать запросы, разверните базу данных и затем установите или снимите **запросы** "флажок".  
  
    -   Чтобы преобразовать или пропустите отдельных таблиц, разверните базу данных, разверните узел **таблиц**, а затем установите или снимите флажок рядом с таблицей.  
  
Если у вас есть много объектов, может потребоваться использовать **Расширенный выбор объектов** параметры в области справа для фильтрации доступа к объектам базы данных. Например, если вы выберите **таблиц** в области слева, затем можно отфильтровать список таблиц, введя строки в **фильтра** поле. Затем можно выбрать или очистить фильтруемых таблиц для миграции с помощью кнопок в верхней части области.  
  
Дополнительные сведения о фильтрации см. в раздел Options [Расширенный выбор объектов (SSMA распространено)](http://msdn.microsoft.com/f53b0c79-5473-410a-a0dc-d8f544f7a63c).  
  
## <a name="connect-to-sql-server-page"></a>Подключение к странице SQL Server  
На странице подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] странице Укажите свойства соединения, а затем подключитесь к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Дополнительные сведения см. в разделе [подключение к SQL Server](http://msdn.microsoft.com/00e0432e-ec26-4ab4-af64-c9ca760e3541)  
  
> [!IMPORTANT]  
> Возникает сразу после успешного подключения **связь с таблицами** страницы, где предусмотрена возможность связывания в таблицах. Нажмите кнопку **Далее** и запускает миграции.  
  
## <a name="connect-to-sql-azure-page"></a>Подключение к SQL Azure страницы  
На странице подключение к SQL Azure укажите свойства соединения и подключитесь к SQL Azure. Чтобы создать новую базу данных azure, это можно сделать с помощью **Создание базы данных Azure** вариант, который отображается при щелчке **Обзор** кнопки. Дополнительные сведения см. в разделе [подключение к SQL Azure](http://msdn.microsoft.com/bf44b236-d9be-41ae-a5fd-bd73038e505f)  
  
> [!IMPORTANT]  
> Возникает сразу после успешного подключения **связь с таблицами** страницы, где предусмотрена возможность связывания в таблицах. Нажмите кнопку **Далее** кнопку на странице "ссылки", чтобы начать миграцию.  
  
## <a name="link-tables-page"></a>Страница связи таблиц  
На странице таблицы ссылок можно связать исходные таблицы Access с перенесенными [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблиц SQL Azure. Связывание таблиц изменяет базу данных Access, таким образом, чтобы ваши запросы, формы, отчеты и данные доступа к страницам использовать данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure вместо данных в базе данных.  
  
**Связь с таблицами**  
Выберите **связывание таблиц** флажок, чтобы связать таблицы Access с перенесенными [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблиц SQL Azure. Чтобы начать миграцию, следует нажать кнопку **Далее** кнопки.  
  
## <a name="migration-status-page"></a>Страница состояния миграции  
На странице состояния миграции отображается ход выполнения преобразования схем доступа [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схем SQL Azure, загрузке преобразованный схем в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, и затем перенос данных.  
  
Дополнительные сведения об этой странице см. в разделе [преобразование, загрузка и миграция](http://msdn.microsoft.com/4ec83e96-88a5-4b7b-8d5a-f3429d9a936b)  
  
## <a name="see-also"></a>См. также  
[Приступая к работе с SQL Server Migration Assistant для Access &#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Reference(Access) интерфейса пользователя](http://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
