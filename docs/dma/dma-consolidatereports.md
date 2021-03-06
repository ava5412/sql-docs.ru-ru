---
title: Импорт и объединение отчетов с оценкой помощник по миграции данных (SQL Server) | Документация Майкрософт
description: Узнайте, как для импорта отчетов с оценкой из помощника по миграции данных в базу данных SQL Server, а также объединять несколько отчетов
ms.custom: ''
ms.date: 04/16/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: be9fc224093f0d5ae14372d4674a52589a2d4801
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781775"
---
# <a name="import-and-consolidate-data-migration-assistant-assessment-reports"></a>Импорт и объединение помощник по миграции данных отчетов с оценкой

Можно использовать командную строку для выполнения оценки миграции в автоматическом режиме, начиная с версии 2.1 Data Migration Assistant. Эта функция позволяет для выполнения оценок в нужном масштабе. Результаты оценки в виде файла JSON или CSV.

Можно оценить несколько баз данных в отдельный экземпляр Data Migration Assistant программы командной строки и экспортировать все результаты оценки в JSON-файл. Или можно оценить во время одной базы данных и позже объединить результаты из этих несколько JSON-файлов в базу данных SQL.

Сведения о том, как запустить помощник по миграции данных из командной строки см. в разделе [запустите помощник по миграции данных из командной строки](../dma/dma-commandline.md). 

## <a name="import-assessment-results-into-a-sql-server-database"></a>Импорт результатов оценки в базу данных SQL Server

Используйте сценарий PowerShell, см. в этом [репозиторий Github](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant) для импорта результатов оценки из JSON-файлов в базу данных SQL Server.

> [!NOTE]
> PowerShell версии 5 или выше необходим.

При выполнении сценарий, вам потребуется предоставить следующие сведения: 

- **serverName**: имя экземпляра SQL Server, что вы хотите импортировать оценки результатов из JSON-файлов.

- **Имя базы данных**: имя базы данных, получить импортировать результаты.

- **jsonDirectory**: папка, сохранения результатов оценки, в один или несколько файлов JSON.

- **processTo**: SQLServer

Добавьте приведенные выше значения в разделе «Выполнение функции» следующим образом.

```
dmaProcessor -serverName localhost \`\
-databaseName DMAReporting \`\
-jsonDirectory "C:\\temp\\DMACmd\\output\\" \`\
-processTo SQLServer
```

Сценарий PowerShell создает следующие объекты в экземпляре SQL Server, которые вы указали, если не существует нужных объектов:

- **База данных** — имя, указанное в параметрах PowerShell

  - Основной репозиторий

- **Таблица** – ReportData

  - Данные для отчетов

- **Таблица** -BreakingChangeWeighting

  - Ссылочная таблица для всех критических изменений. Здесь можно определить собственные значения веса на более точные ранжирования обновление выполнено успешно процент (%).

- **Представление** — UpgradeSuccessRanking\_OnPrem

  - Представления, отображающее фактор успеха для каждой базы данных для перенесенных локально.

- **Представление** — UpgradeSuccessRanking\_Azure

  - Представления, отображающее фактор успеха для каждой базы данных для перенесенных локально.

- **Хранимая процедура** — JSONResults\_вставки

  - Используется для импорта данных из файла JSON в SQL Server.

- **Хранимая процедура** — AzureFeatureParityResults\_вставки

  - Используется для импорта результатов четности компонентов Azure из JSON-файла в SQL Server.

- **Тип таблицы** – JSONResults

  - Используется для хранения результатов JSON для оценки в локальной и передавать JSONResults\_хранимая процедура Insert

- **Тип таблицы** – AzureFeatureParityResults

  - Используется для хранения компонентов Azure четности результатов оценки azure и передавать AzureFeatureParityResults\_хранимая процедура Insert

Сценарий PowerShell создает **обрабатываемые** каталог в указанный каталог, содержащий JSON-файлы, которые должны обрабатываться.

По завершении выполнения скрипта результаты импортируются в таблице ReportData.

### <a name="viewing-the-results-in-sql-server"></a>Просмотр результатов в SQL Server

После загрузки данных, подключитесь к экземпляру SQL Server. Экран должен выглядеть, как показано на следующем рисунке:

![Консолидированные отчеты в базе данных SQL Server](../dma/media/DMAReportingDatabase.png)

Dbo. Таблица ReportData содержит содержимое файла JSON в необработанном виде.

## <a name="on-premises-upgrade-success-ranking"></a>В локальной обновление ранжирования успех

Чтобы просмотреть список баз данных и рангу успех процент (%), выберите dbo. Представление UpgradeSuccessRanking_OnPrem:

![Данные в представлении UpgradeSuccessRaning_OnPrem](../dma/media/UpgradeSuccessRankingView.png)

Здесь вы увидите для заданной базы данных: Какова вероятность успеха обновления для разных уровнях совместимости. Таким образом например, базу данных HR был оценили для уровней совместимости, 100, 110, 120 и 130. Эта оценка помогает визуально см. в разделе усилия, потраченные включается в миграцию до более поздней версии SQL Server из базы данных находится в текущей версии.

Обычно метрики, которые вас интересуют — сколько изменений критические предназначены для конкретной базы данных. В приведенном выше примере можно увидеть, что база данных HR имеет коэффициент обновление выполнено успешно 50% для уровней совместимости, 100, 110, 120 и 130.

Эта метрика может зависеть путем изменения значений веса в dbo. Таблица BreakingChangeWeighting.

В следующем примере усилия, уходящие на устранение синтаксическая ошибка в базе данных HR считается высокой, назначается значение 3 **усилия**. Так как это не займет много времени, чтобы решить проблему, синтаксис, значение 1 будет назначено **FixTime**. Так как некоторые стоимость будет заниматься внесения изменений, значение 2 назначается **стоимость**. Это значение меняется Changerank переходом на 2.

> [!NOTE]
> Оценки — по шкале от 1 до 5.  1 самый низкий, а 5 — самый высокий уровень. Кроме того ChangeRank является вычисляемым столбцом.

![Усилия, стоимость и FixTime значений в параметре синтаксическая ошибка](../dma/media/SyntaxIssueEffort.png)

Теперь в этом примере, при запросе dbo. Представление UpgradeSuccessRanking_OnPrem коэффициент для базы данных HR критически важных изменениях обновление выполнено успешно удалены.

![Обновление фактор успеха для базы данных HR](../dma/media/UpgradeSuccessFactor_HR.png)

## <a name="azure-upgrade-success-ranking"></a>Ранжирование Azure обновление выполнено успешно

Чтобы просмотреть список баз данных для миграции базы данных SQL Azure и рангу успех в процентах, выберите dbo. Представление UpgradeSuccessRanking_Azure.

![Данные в представлении UpgradeSuccessRanking_Azure](../dma/media/UpgradeSuccessRankingView_Azure.png)

Здесь вы заинтересованы в значении MigrationBlocker. 100,00 означает, что ранг успех 100% для перемещения базы данных до версии 12 базы данных SQL Azure.

Разница с этим представлением — это в настоящее время нет переопределения для изменения взвешенное значение для блокирования установки правила переноса.

Сведения о об этих данных с использованием Power BI, см. в разделе [отчетов о вашей консолидированных оценок с помощью PowerBI](../dma/dma-powerbiassesreport.md).
