---
title: Установка SQL Server 2016 R Server (изолированная версия) | Документация Майкрософт
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e5457698120536247ad1823b842bb1b8e52b484d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979286"
---
# <a name="install-sql-server-2016-r-server-standalone"></a>Установка SQL Server 2016 R Server (изолированный)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается использование программы установки SQL Server 2016 для установки автономной версии **SQL Server 2016 R Server**.

## <a name="bkmk_prereqs"> </a> Контрольный список перед установкой

SQL Server 2016 является обязательным. Если у вас есть SQL Server 2017, установите [сервера SQL Server 2017 машинного обучения (изолированного)](sql-machine-learning-standalone-windows-install.md) вместо этого.

Если вы установили любой предыдущей версии средств Revolution Analytics или пакетов, сначала их необходимо удалить. 

## <a name="get-the-installation-media"></a>Получение установочного носителя

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Требование для установки исправления 

Корпорация Майкрософт выявила проблему с определенной версией двоичных файлов среды выполнения Microsoft VC++ 2013, которые SQL Server устанавливает в качестве необходимого компонента. Если это обновление двоичных файлов среды выполнения VC не установлено, в SQL Server могут возникать проблемы с надежностью в определенных сценариях. Перед установкой SQL Server выполните инструкции, приведенные в [заметках о выпуске SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch), чтобы узнать, требуется ли на вашем компьютере исправление для двоичных файлов среды выполнения VC.  

## <a name="run-setup"></a>Запуск программы установки

Для локальных установок необходимо запускать программу установки с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.

1. Запустите мастер установки для SQL Server 2016. Мы рекомендуем установить пакет обновления 1 или более поздней версии.

2. На **установки** щелкните **Установка нового R Server (изолированный)**.
    
     ![Запустите программу установки изолированного сервера R](media/2016-setup-installation-rsvr.png "запустите программу установки изолированного сервера R")
    
3.  На странице **Выбор компонентов** уже должен быть выбран следующий параметр:
    
    **R Server (изолированный)**  
    
    ![Выбор изолированного сервера R компонентов](media/2016setup-rserver-features.png "Выбор изолированного сервера R компонентов")
    
    Все прочие параметры можно игнорировать. 
    
    > [!NOTE]
    > Не устанавливать **общие компоненты** при запуске программы установки на компьютере, где R уже установлены службы для анализа в базе данных SQL Server. Это создает повторяющиеся библиотеки.
    > 
    > При этом R-скриптов, выполняемых в SQL Server под управлением SQL Server, так как не будет конфликтовать с память, занятая другими службами компонента database engine, изолированного сервера R Server имеет такие ограничения нет и может конфликтовать с другими операциями базы данных.
    > 
    > Обычно рекомендуется установить R Server (изолированный) на отдельном компьютере с SQL Server R Services (в базе данных).

4.  Примите условия лицензии, чтобы скачать и установить Microsoft R Open. Когда кнопка **Принять** станет недоступна, можно нажать кнопку **Далее**.
    
    Установка этих компонентов, и все необходимые компоненты, которые могут понадобиться, может занять некоторое время.
    
5.  На странице **Все готово для установки** проверьте выбранные параметры и нажмите кнопку **Установить**.

## <a name="default-installation-folders"></a>По умолчанию установочные папки

При установке сервера R с помощью программы установки SQL Server, библиотеки R устанавливаются в папку, связанную с версией SQL Server, который использовался для установки. В этой папке вы также найдете образцы данных, документация по базовым пакетам и документацию, инструменты R и среды выполнения.

Тем не менее если вы установили Microsoft R Server с помощью отдельного установщика Windows (не программа установки SQL) или при обновлении с помощью отдельного установщика Windows, библиотеки R устанавливаются в другую папку.

Несмотря на то, что мы не рекомендуем его, если вы установили экземпляр SQL Server со службами R (в базе данных) на одном компьютере, второй копии библиотеки и средства R устанавливаются в другую папку.

В следующей таблице перечислены пути для каждой установки.

|Версия| Метод установки | Папка по умолчанию|
|----|----|----|
|R Server (Standalone) |Мастер установки SQL Server 2016|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (Standalone) |Автономный установщик Windows|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Сервер машинного обучения (автономный) |  Мастер установки SQL Server 2017, с помощью языка R-параметр |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Сервер машинного обучения (автономный) |  Мастер установки SQL Server 2017, с параметром языка Python |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Сервер машинного обучения (автономный) |  Автономный установщик Windows |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Службы R (в базе данных) |Мастер установки SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Службы машинного обучения (в базе данных) |Мастер установки SQL Server 2017, с помощью языка R-параметр|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Службы машинного обучения (в базе данных) |Мастер установки SQL Server 2017, с параметром языка Python| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |

## <a name="development-tools"></a>Средства разработки

Интегрированная СРЕДА разработки не устанавливается в процессе установки. Дополнительные средства не требуются, так как все стандартные средства включены, будет предоставлен дистрибутив R или Python.

Мы рекомендуем вам опробовать новый выпуск [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] или [Python для Visual Studio](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio). Visual Studio поддерживает как R и Python, а также инструменты для разработки баз данных, возможность подключения к SQL Server и средств бизнес-Аналитики. Тем не менее можно использовать любой предпочитаемой среде разработки, включая RStudio.
  
## <a name="get-help"></a>Получить справку

Нужна помощь с установку или обновление? Ответы на часто задаваемые вопросы и известные проблемы обратитесь к следующей статье:

* [Обновление и установка часто задаваемые вопросы – службы машинного обучения](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Чтобы проверить состояние установки экземпляра и исправлять распространенные проблемы, используйте эти пользовательские отчеты.

* [Пользовательские отчеты для служб R SQL Server](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Следующие шаги

Разработчики R можно приступить к работе с простыми примерами и ознакомиться с основами как R работает с SQL Server. Следующий шаг см. следующие ссылки:

+ [Руководство: Запуск R в T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).
+ [Учебник: Анализ в базе данных для разработчиков R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Чтобы просмотреть примеры машинного обучения, которые основаны на реальных сценариев, см. в разделе [машинного обучения учебники](../tutorials/machine-learning-services-tutorials.md).

