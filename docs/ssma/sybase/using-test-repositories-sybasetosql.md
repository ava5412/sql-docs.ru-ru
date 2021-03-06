---
title: С помощью репозиториев теста (SybaseToSQL) | Документы Microsoft
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
- Tester Component,Test Repositories
ms.assetid: c359c25c-db2a-4a20-afa9-62d87a62df72
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 880262cf0342c66a91a1f88e50477e0685e1d1e0
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779540"
---
# <a name="using-test-repositories-sybasetosql"></a>С помощью репозиториев теста (SybaseToSQL)
Хранилище тестов SSMA хранилищ инженер-испытатель SSMA тестовые случаи и результаты теста для последующего использования. Репозиторий данных сохраняются в таблицах SQL Server **TestCaseRepository** и **RunTestCaseResultRepository** в схеме **ssma_sybase_utilities** из **ssmatesterdb_syb** базы данных.  
  
В диалоговом окне репозитория тестовых случаев доступны следующие кнопки:  
  
-   Нажмите кнопку **обновление** кнопку, чтобы обновить список тестовых случаев или результатов тестов.  
  
-   Нажмите кнопку **закрыть** кнопку, чтобы закрыть диалоговое окно репозитория тестовых случаев.  
  
## <a name="test-cases-repository"></a>Репозиторий тестовых случаев  
Репозиторий тестовые случаи можно просмотреть, щелкнув **тестовые случаи...** из **тест-инженер** меню. Затем отображает SSMA **репозитория тестовых случаев** диалоговое окно со списком сохраненные тестовые случаи в **тестовых случаев** страницы.  
  
В сетке показаны следующие сведения о каждого тестового случая:  
  
-   Имя: Имя тестового случая.  
  
-   Создан: Тестовый случай Дата создания.  
  
-   Изменен: Тестовый случай Дата последнего изменения.  
  
-   Описание: Тестовый случай описания.  
  
На странице тестовых случаев доступны следующие кнопки:  
  
-   Нажмите кнопку **добавить** кнопку, чтобы запустить мастер тестовый случай и создать новый тест.  
  
-   Нажмите кнопку **удалить** кнопку, чтобы удалить выбранный тест из репозитория. При удалении тестового случая, также удаляются все связанные результаты тестов.  
  
-   Нажмите кнопку **изменить** кнопку, чтобы запустить мастер тестовый случай и изменить выбранного теста.  
  
-   Нажмите кнопку **запуска** кнопку, чтобы открыть [выполнение тестовых случаев &#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md) диалоговое окно и выполнение выбранного теста.  
  
## <a name="test-results-repository"></a>Репозиторий результатов теста  
Репозиторий результатов теста можно просмотреть на **результаты теста** страница **репозитория тестовых случаев** окна. Открыть, щелкнув **результаты теста...** из **тест-инженер** меню.  
  
Можно использовать два фильтра на **результаты теста** страницы:  
  
-   Фильтр имя тестового случая: позволяет выбирать результаты тестов по имени тестового случая. Этот фильтр **всех тестовых случаев** значение позволяет отображение результатов теста для всех тестовых случаев.  
  
-   Фильтр даты выполнения тестового случая: фильтры результаты тестов по дате сохранения. Этот фильтр **все период** значение дает возможность отображения для любой даты для сохранения результатов теста.  
  
Следующие сведения о результатах теста отображается в сетке.  
  
-   Имя: имя тестового случая.  
  
-   Запущено: Тестовая вариантов Дата выполнения.  
  
-   Результат: Краткое описание выполнения теста (эта ячейка всплывающая подсказка Сводка полного выполнения теста).  
  
На странице результатов тестирования доступны следующие кнопки:  
  
-   Нажмите кнопку **представление** кнопку, чтобы открыть [просмотра отчетов тестовый случай &#40;SybaseToSQL&#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md) текущего результата тестового случая.  
  
-   Нажмите кнопку **удалить** кнопку, чтобы удалить выбранный результат теста  
  
## <a name="see-also"></a>См. также  
[Выполнение тестовых случаев &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Тестирование перенесенные объекты базы данных &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
