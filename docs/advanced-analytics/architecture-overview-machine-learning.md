---
title: Общие сведения об архитектуре служб SQL Server Machine Learning | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4abe5e508f1e183e1e6cb5012b9541fe3723b77a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31202987"
---
# <a name="architecture-overview-for-sql-server-machine-learning-services"></a>Общие сведения об архитектуре служб SQL Server машины обучения 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описываются цели extensibility Framework, которая поддерживает выполнение сценария Python и R в SQL Server.

Он также предоставляет обзор проектирования архитектуры для достижения этих целей процесс поддерживается и выполнения и преимущества интеграции SQL Server R и Python.

В целом инфраструктура расширяемости R и Python, почти совпадает с незначительными различиями в подробные сведения о средства запуска, которые вызываются, параметры конфигурации и т. д. Сведения о реализации для конкретного языка см. статьи:

- [Обзор архитектуры для SQL Server R Services](r/architecture-overview-sql-server-r.md)
- [Общие сведения об архитектуре для Python в SQL Server](python/architecture-overview-sql-server-python.md)


## <a name="background"></a>Историческая справка

В SQL Server 2016 многочисленные изменения появились с компонентом database engine для поддержки выполнения скриптов R, с помощью SQL Server. В SQL Server 2017 г этой базовой инфраструктурой была улучшена добавить поддержку языка Python.

Инфраструктура расширяемости заключалась в создании более интерфейс между SQL Server и языках обработки и анализа данных, например R и Python, и является повышение эффективности, возникающее при перемещении в эксплуатацию решений для обработки и анализа данных, а для защиты данных, которые могут быть предоставляются во время разработки обработки и анализа данных.

Выполняя доверенных язык сценариев безопасной платформы, под управлением SQL Server, разработчик базы данных может поддерживать безопасности, позволяет специалистам по анализу данных для использования данных предприятия.

  ![Цели интеграция с SQL Server](media/ml-service-value-add.png "машины обучения служб эффект")

- Текущие пользователи из R или Python можно перенести свой код или выполнить ее в SQL Server с относительно небольшими изменениями.
- Модель безопасности данных в SQL Server будет расширено и данные, используемые внешней языки сценариев. Другими словами кто-то выполнение скрипта R или Python необходимо будет использовать любые данные, которые недоступны этого пользователя в SQL-запросе.
- Администратор базы данных должен иметь возможность управлять ресурсы, используемые внешних скриптов, управление пользователями и управлять и отслеживать внешнего кода библиотеки.
- Система должна поддерживать решения, основываясь целиком на дистрибутивов открытым исходным кодом R и Python, но использование собственных компонентов, разработанных корпорацией Майкрософт для обеспечения большей безопасности и производительности.

## <a name="architecture-core-concepts"></a>Основные понятия архитектуры

Для достижения этих целей, архитектуры служб R SQL Server 2016 и службы SQL Server 2017 г машины обучения для R и Python зависит от следующих базовых понятиях:

+ **Архитектура процессов**

  R и Python — это открытая языки с поддержкой сообществу полнофункциональную и энтузиастов. Таким образом важно поддерживать полное взаимодействие с открытым исходным кодом R и Python.

  Распределения с открытым исходным кодом R и Python устанавливаются вместе с SQL Server в рамках лицензии и могут функционировать независимо от SQL Server при необходимости.

   Кроме того Корпорация Майкрософт предоставляет набор собственных библиотек, которые обеспечивают интеграцию с SQL Server, включая преобразования данных, сжатие и оптимизации, предназначенные для каждого поддерживаемого языка.

+ **Безопасность**

   Более высокий уровень безопасности означает поддерживает встроенную проверку подлинности Windows и имена входа SQL на основе пароля, в качестве также как безопасные обработку учетных данных, следует рассчитывать на SQL Server для защиты данных и использование доверенного панели запуска SQL Server для управления внешних скриптов выполнение и защиты данных, используемых в скриптах.

+ **Производительность и масштабируемость**

  Интеграция с SQL Server является ключом к улучшению полезность Python и R на предприятии. Любой сценарий R или Python можно выполнить путем вызова хранимой процедуры, а результаты возвращаются в виде табличных результатов непосредственно в SQL Server, что позволяет легко создавать или использовать машинное обучение из любого приложения, которое может отправлять SQL-запроса и обработки результатов.

  Оптимизация производительности зависит от два аспекта столь же мощных платформы: управление ресурсами и параллельной обработки с помощью SQL Server и распределенных вычислений, предоставляемых алгоритмами в **RevoScaleR** и **revoscalepy**.

## <a name="solution-development-and-deployment"></a>Разработка и развертывание решений

Помимо этих основных целей для расширяемости платформы призваны обеспечить тесную интеграцию с ядром СУБД и стека бизнес-Аналитики, эти преимущества службы обучения машины в SQL Server:

+ Управление производительности и ресурсов с помощью традиционных средств мониторинга
+ Простые в использовании Python и R данных, наборы бизнес-Аналитики или любого приложения, которые можно использовать результаты SQL-запроса
+ Гораздо ниже барьера для разработки корпоративных решений обучения машины

Давайте посмотрим, как это работает на практике.

  ![Процесс разработки решения ML](media/ml-solution-development-process.png "разработка и развертывание с помощью службы обучения машины")

1. Данные хранятся в пределах границ соответствия и использования данных можно управлять и отслеживаемый с помощью SQL Server. В свою очередь администратор базы данных имеет полный контроль над, можно установить пакеты или запускать скрипты на сервере. При желании администратор базы данных можно также делегировать разрешения на уровне базы данных для специалистов по анализу данных или менеджеров.
2. Специалисты по анализу данных можно построить и тестирования решения в их предпочтительный R или Python средах отключен от сервера.
3. Разработчик SQL можно использовать знакомые средства, например среды Management Studio или Visual Studio на интеграцию кода R или Python с SQL Server. Тесная интеграция означает, что грамотный разработчик может выбрать наиболее подходящим средством для оптимизации каждой задачи. Например можно использовать SQL для некоторых компонентов технических задач и R для других пользователей. Сценарий Python могут внедрять в задаче «службы Integration Services» для выполнения анализа сложных текста.
4. Протестированные и все готово для развертывания решений можно оптимизировать с помощью технологий SQL Server, таких как индексы columnstore для повышения производительности. Новые функции позволяют пакета обучение множество небольших моделей параллельно на секционированные данные набора или оценки миллионы строк с помощью машинного кода SQL, оптимизированный для задач машинного обучения.
5. Все готово для точности прогнозов? Можно легко предоставлять решениях прогнозирования в стеке бизнес-Аналитики или внешними приложениями с помощью хранимых процедур.

## <a name="related-products"></a>Связанные продукты

Не знаете, какие решения машинного обучения соответствует требованиям? Помимо внедренные аналитика в SQL Server 2016 и на SQL Server 2017 г. Корпорация Майкрософт предоставляет следующие машинного обучения платформы и служб:

+ [Microsoft R Server и сервера Machine обучения](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)

  Среде несколькими платформами разработки, распределение и управление заданиями обучения машины
+ [Виртуальная машина обработки и анализа данных](https://docs.microsoft.com/azure/machine-learning/machine-learning-data-science-virtual-machine-overview)

  Все средства, необходимые для компьютера, обучения и предварительно. Используйте записные книжки Jupyter, Python или R.
  
  Воспользуйтесь новым [ознакомительного выпуска Windows 2016](http://aka.ms/dsvm/win2016), включая версии GPU популярных углубленного обучения платформ, например CNTK mxNet, а также поддержку контейнеров Windows!

+ [Когнитивных служб Azure](https://azure.microsoft.com/services/cognitive-services/)

  Широкий набор облачных служб для добавления в приложения, включая индексирование естественного языка распознавания видео, лиц, AI и ML эмоций обнаружения, анализа текста компьютера более значения преобразования и очень много операций,
+ [Машинное обучение Azure](https://azure.microsoft.com/services/machine-learning/)

  Интерфейс и перетащите облачной разработки обучения конечных автоматов, вместе с возможностью для автоматизации и интеграция с приложениями через веб-службы и PowerShell

## <a name="see-also"></a>См. также

[Сравнение продуктов машины обучения Server и Microsoft R](https://docs.microsoft.com/machine-learning-server/what-is-r-server-interoperability)
