---
title: Свойства заданий (Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.jobproperties.f1
ms.assetid: 807ffd0e-9363-4f8f-9c36-c5d746ad19fd
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0d2d7a24df5c74ba940dd0d9455b61b5c3aec526
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153615"
---
# <a name="job-properties-management-studio"></a>Свойства задания (среда Management Studio)
  На странице **Свойства задания** можно просматривать сведения о выполняющихся отчетах и подписках перед их отменой.  
  
 Чтобы открыть эту страницу, запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], подключитесь к серверу отчетов и откройте папку **Задания** . Щелкните выполняющееся задание правой кнопкой мыши и выберите пункт **Свойства**.  
  
> [!NOTE]  
>  Эта функция не поддерживается в [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services. Эта страница не отображается при запуске выпуска [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
## <a name="tasks"></a>Задания  
 Прежде чем сведения о задании можно будет просмотреть, обновите страницу, чтобы получить сведения о заданиях, выполняемых в данный момент на сервере отчетов.  
  
1.  Откройте папку сервера отчетов.  
  
2.  Щелкните правой кнопкой мыши **Задания**и выберите команду **Обновить**.  
  
3.  Если задание присутствует в списке, щелкните его правой кнопкой мыши и выберите пункт **Свойства**.  
  
## <a name="options"></a>Параметры  
 **Идентификатор задания**  
 Идентификатор GUID, присваиваемый заданию во время его обработки. Это значение формируется случайным образом при каждом запуске отчета или подписки.  
  
 **Состояние задания**  
 Допустимы следующие значения: **Новое** и **Выполняется**. В начале выполнения задание всегда имеет состояние **Новое** . Через 60 секунд состояние меняется на **Выполняется**. Чтобы отобразить это изменение, необходимо обновить страницу.  
  
 **Тип задания**  
 Допустимы следующие значения: **Пользовательское** и **Системное**. Пользовательским заданием является любое задание, инициированное отдельным пользователем. Сюда входит запуск отчета по требованию, формирование моментального снимка журнала отчета или создание снимка состояния выполнения отчета вручную. Выполняющаяся обычная подписка также является пользовательским заданием. Системным заданием является задание, инициируемое сервером отчетов. К системным заданиям относится и обработка отчетов, запускаемая по расписанию.  
  
 **Действие задания**  
 Для отчетов в этом столбце показываются процессы выполнения, которые в настоящее время работают. Всегда принимает значение **Подготовка отчетов**.  
  
 **Описание задания**  
 Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по умолчанию не обеспечивает описание заданий.  
  
 **Имя сервера**  
 Показывает имя сервера отчетов, на котором выполняется обработка задания. Если было настроено масштабное развертывание, это значение показывает, какой из серверов обрабатывает задание.  
  
 **Имя отчета**  
 Отображается имя отчета. Подписки идентифицируются описаниями.  
  
 **Путь отчета**  
 Показывает путь к отчету в иерархии папок на сервере отчетов.  
  
 **Start Time**  
 Указывается время запуска процесса.  
  
 **Имя пользователя**  
 Для процессов, инициируемых пользователем, в этом столбце отображается имя пользователя. Для системных заданий отображается имя сервера отчетов.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 по использованию сервера отчетов среде Management Studio](report-server-in-management-studio-f1-help.md)   
 [Подключение к серверу отчетов в среде Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Управление запущенным процессом](../subscriptions/manage-a-running-process.md)  
  
  
