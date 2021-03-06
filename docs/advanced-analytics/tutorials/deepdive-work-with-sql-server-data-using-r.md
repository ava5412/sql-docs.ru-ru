---
title: Работа с данными SQL Server, с помощью языка R (SQL и R глубокое погружение в обработку) | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ea8fee364cd69580b8b7d0b6438349dbf2b1298c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084186"
---
# <a name="lesson-1-create-a-database-and-permissions"></a>Занятие 1: Создание базы данных и разрешения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии настроить среду и добавить данные, необходимые для обучения моделей и кратких сводок данных. Как часть процесса необходимо выполнить следующие задачи:
  
- создадите базу данных, в которой будут храниться данные для обучения и оценки двух моделей R;
  
- создадите учетную запись (пользователя Windows или имя входа SQL), которая будет использоваться для обмена данными между рабочей станцией и сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;
  
- создадите источники данных в R для работы с данными и объектами базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;
  
- используете источник данных R для загрузки данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];
  
- используете язык R для получения списка переменных и изменения метаданных таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;
  
- создадите контекст вычисления для удаленного выполнения кода на языке R;
  
- (Необязательно) Включите трассировку в удаленном контексте вычисления.
  
## <a name="create-the-database-and-user"></a>Создание базы данных и пользователя

В этом пошаговом руководстве, создайте новую базу данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]и добавьте имя входа SQL с разрешениями на запись и чтение данных и для выполнения скриптов R.

> [!NOTE]
> Если используется только для чтения данных, учетная запись, запускает скрипты R, требуются разрешения SELECT (**db_datareader** роли) в указанной базе данных. Тем не менее в этом руководстве, необходимо иметь права администратора DDL Подготовка базы данных и создания таблицы для сохранения результатов оценки.
> 
> Кроме того Если вы не являетесь владельцем базы данных, необходимо разрешение EXECUTE ANY EXTERNAL SCRIPT для выполнения R-скриптов.

1. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]выберите экземпляр, в котором включены службы [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , щелкните правой кнопкой мыши элемент **базы данных**и выберите пункт **Создать базу данных**.
  
2. Введите имя новой базы данных. Вы можете использовать любое имя, но не забудьте внести соответствующие изменения во все скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] и R в этом пошаговом руководстве.
  
    > [!TIP]
    > Чтобы увидеть новое имя базы данных, щелкните правой кнопкой мыши элемент **Базы данных** и выберите пункт **Обновить** .
  
3. Щелкните **Создать запрос**и измените контекст базы данных на master.
  
4. В новом окне **Запрос** выполните приведенные ниже команды, чтобы создать учетные записи пользователей и назначить их базе данных, используемой в этом учебнике. При необходимости измените имя базы данных.
  
**Пользователь Windows**
  
```SQL
 -- Create server user based on Windows account
USE master
GO
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[DeepDive]

 --Add the new user to tutorial database
USE [DeepDive]
GO
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]
```

**Имя входа SQL**

```SQL
-- Create new SQL login
USE master
GO
CREATE LOGIN DDUser01 WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

-- Add the new SQL login to tutorial database
USE [DeepDive]
GO
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]
```

5. Чтобы проверить, был ли создан пользователь, выберите новую базу данных, а затем разверните узлы **Безопасность**и **Пользователи**.

## <a name="troubleshooting"></a>Устранение неполадок

В этом разделе перечислены некоторые распространенные проблемы, которые могут возникнуть в процессе настройки базы данных.

- **Как проверить подключение к базе данных и запросы SQL?**
  
    Перед выполнением кода на языке R с помощью сервера может потребоваться проверить, доступна ли база данных из среды разработки R. [Обозреватель сервера Visual Studio](https://msdn.microsoft.com/library/x603htbk.aspx) и [среда SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) являются бесплатными средствами с эффективными возможностями подключения к базам данных и функциями управления.
  
    Если вы не хотите устанавливать дополнительные средства управления базами данных, то можете создать тестовое подключение к экземпляру SQL Server с помощью компонента [Администратор источников данных ODBC](https://msdn.microsoft.com/library/ms714024.aspx) на панели управления. Если база данных настроена правильно и вы ввели верные имя пользователя и пароль, то вы увидите созданную базу данных и сможете выбрать ее в качестве базы данных по умолчанию.
  
    Если вы не можете подключиться к базе данных, проверьте, включены ли удаленные подключения для сервера и включен ли протокол именованных каналов. В этой статье предоставляются дополнительные советы по устранению неполадок: [Устранение неполадок подключения к SQL Server Database Engine](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Почему имя таблицы имеет префикс datareader?**
  
    При указании схемы по умолчанию для этого пользователя как **db_datareader**, все таблицы и другие объекты, созданные этим пользователем начинаются с префикса *схемы* имя. Схема напоминает папку, которую можно добавить к базе данных для упорядочения объектов. Схема также определяет права пользователя в базе данных.
  
    Если схема связана с одного имени определенного пользователя, он _владелец схемы_. Когда вы создаете объект, он всегда создается в вашей собственной схеме, если вы специально не укажете, что он должен быть создан в другой схеме.
  
    Например, если создать таблицу с именем `*`TestData`, and your default schema is **db\_datareader**, the table is created with the name `.db_datareader < имя_базы_данных >. TestData ".
  
    По этой причине база данных может содержать несколько таблиц с одинаковыми именами, если они относятся к разным схемам.
   
    Если вы ищете таблицу и не указали схему, сервер базы данных выполняет поиск вашей собственной схеме. Поэтому нет необходимости указывать имя схемы при доступе к таблицам в схеме, связанной в вашим именем входа.
  
- **У меня нет прав DDL. Могу ли я работать с учебником?**
  
    Да. Однако вам нужно будет предварительно попросить кого-нибудь загрузить данные в таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а затем пропустить разделы, в которых требуется создать таблицы. Функции, требующие прав DDL, называются в этом руководстве, везде, где это возможно.

    Кроме того попросите администратора предоставить вам разрешения EXECUTE ANY EXTERNAL SCRIPT. Он необходим для выполнения сценариев R, ли удаленный или с помощью `sp_execute_external_script`.

## <a name="next-step"></a>Следующий шаг

[Создание объектов данных SQL Server с помощью функции RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)

## <a name="overview"></a>Обзор

[Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)



