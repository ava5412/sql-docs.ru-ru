---
title: "Настройка рабочей нагрузки | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- workloads [SQL Server], tuning
ms.assetid: 6229bf3f-1182-4bc6-8451-cedc37f4b62e
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f64ca747368ed22ea4d9f19027b446a98e19e87c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="lesson-1-1---tuning-a-workload"></a>Занятие 1-1 — Настройка рабочей нагрузки
Помощник по настройке ядра СУБД можно использовать для определения физической структуры базы данных и выбранных таблиц, оптимальной с точки зрения производительности запросов.  
  
В данной задаче используется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются. Дополнительные сведения об установке образцов баз данных см. в статье [Установка образцов SQL Server и образцов баз данных](http://sqlserversamples.codeplex.com).  
  
### <a name="tune-a-workload-transact-sql-script-file"></a>Настройка файла скрипта рабочей нагрузки Transact-SQL  
  
1.  Скопируйте образец инструкции или инструкций SELECT из примера «А. Использование инструкции SELECT для получения строк и столбцов" в разделе [Примеры использования инструкции SELECT (Transact-SQL)](../../t-sql/queries/select-examples-transact-sql.md) и вставьте их в редактор запросов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Сохраните файл с именем **MyScript.sql** в каталог, где его будет легко найти.  
  
2.  Запустите помощник по настройке ядра СУБД. См. раздел [Запуск помощника по настройке ядра СУБД](../../tools/dta/lesson-1-1-launching-database-engine-tuning-advisor.md).  
  
3.  На правой панели графического пользовательского интерфейса помощника по настройке ядра СУБД в поле **Имя сеанса** введите **MySession**.  
  
4.  В поле **Рабочая нагрузка** выберите значение **Файл**, нажмите кнопку **Выберите файл рабочей нагрузки** и выберите файл **MyScript.sql** , сохраненный в шаге 1.  
  
5.  Выберите в списке [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] База данных для анализа нагрузки **значение** , выберите [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] в сетке **Выберите базы данных и таблицы для настройки** и оставьте установленным флажок **Сохранить журнал настройки** . В поле**База данных для анализа рабочей нагрузки** указывается первая база данных, к которой будет подключаться помощник по настройке ядра СУБД при настройке рабочей нагрузки. После начала настройки помощник по настройке ядра СУБД подключается к базам данных, определенным в инструкциях `USE DATABASE` , которые содержатся в рабочей нагрузке.  
  
6.  Перейдите на вкладку **Параметры настройки** . В этом задании не рассматривается настройка параметров, однако рекомендуется ознакомиться со значениями параметров по умолчанию. Нажмите клавишу F1, чтобы вызвать справку для этой страницы с вкладками. Нажмите кнопку **Дополнительные параметры** , чтобы просмотреть дополнительные параметры настройки. Нажмите кнопку **Справка** в диалоговом окне **Расширенные параметры настройки** , чтобы просмотреть дополнительные сведения о параметрах настройки. Нажмите кнопку **Отмена** , чтобы закрыть диалоговое окно **Расширенные параметры настройки** и оставить заданные по умолчанию параметры.  
  
7.  На панели инструментов нажмите кнопку **Начать анализ** . Пока помощник по настройке ядра СУБД ведет анализ рабочей нагрузки, ход выполнения анализа отображается на вкладке **Ход выполнения** . После завершения настройки отображается вкладка **Рекомендации** .  
  
    При возникновении ошибки даты и времени остановки настройки проверьте значение времени **Остановиться** на вкладке **Параметры настройки** . Убедитесь в том, что дата и время в поле **Остановиться** превышают текущие дату и время, и при необходимости измените значения.  
  
8.  После завершения анализа сохраните рекомендации в виде скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] , выбрав пункт **Сохранить рекомендации** в меню **Действия** . В диалоговом окне **Сохранить как** перейдите в каталог, где требуется сохранить скрипт рекомендаций, и введите имя файла **MyRecommendations**.  
  
## <a name="summary"></a>Сводка  
Настройка простой рабочей нагрузки инструкции SELECT для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] завершена. Помощник по настройке ядра СУБД в качестве рабочих нагрузок может также принимать файлы трассировки приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] или таблицы. В следующей задаче рассматривается, как просмотреть рекомендации настройки, полученные в результате учебной настройки, и что они означают.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Просмотр рекомендаций по настройке](../../tools/dta/lesson-1-2-viewing-tuning-recommendations.md)  
  
  
  
