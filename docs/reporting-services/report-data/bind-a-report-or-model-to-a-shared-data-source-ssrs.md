---
title: Привязка отчета к общему источнику данных (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-data
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: ded45a9be18b2e00c4b5fc497159ccb80e26bed0
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34550835"
---
# <a name="bind-a-report-to-a-shared-data-source-ssrs"></a>Привязка отчета к общему источнику данных (службы SSRS)
  В некоторых ситуациях, например при переносе отчета с тестового сервера на рабочий, бывает необходимо сохранить файл на локальном компьютере, а затем передать его на другой сервер отчетов. При передаче отчета на новый сервер необходимо повторно привязать его к общему источнику данных, находящемуся на новом сервере отчетов. Если повторную привязку отчета не выполнить, он не будет работать корректно при обращении к нему с нового сервера отчетов.  
  
> [!IMPORTANT]  
>  Перед повторной привязкой отчета к общему источнику данных этот источник должен уже существовать на сервере отчетов или в библиотеке SharePoint. Дополнительные сведения об источниках данных см. в статье [Создание, изменение и удаление общих источников данных (службы SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="to-bind-a-report-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>Привязка отчета к общему источнику данных на сервере отчетов, работающем в собственном режиме  
  
1.  На веб-портале в правом верхнем углу плитки отчета нажмите кнопку с многоточием (...), а затем выберите **Управление**.  

2.  Щелкните **Источники данных**.  
  
3.  Щелкните **Общий источник данных**и перейдите к источнику данных, с которым необходимо связать отчет.  
  
4.  Выберите источник данных и нажмите кнопку **Сохранить**.  
  
5.  Нажмите кнопку **Применить**.  
  
     Теперь отчет привязан к выбранному источнику данных.  
  
## <a name="to-bind-a-report-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>Привязка отчета к общему источнику данных на сервере отчетов, работающем в режиме интеграции с SharePoint  
  
1.  Если библиотека еще не открыта, щелкните ее имя на панели «Быстрый запуск». Если имя библиотеки не отображается, щелкните **Просмотреть содержимое всего сайта**и выберите имя библиотеки.  
  
2.  Укажите отчет и щелкните стрелку вниз.  
  
3.  Щелкните **Управление источниками данных**.  
  
4.  Щелкните **источник_данных_1**.  
  
5.  Убедитесь, что в области **Тип соединения** выбран вариант **Общий источник данных** .  
  
6.  В области **Связь с источником данных** нажмите кнопку с многоточием (...).  
  
7.  Найдите источник данных, который необходимо использовать.  
  
8.  Выберите источник данных и нажмите кнопку **ОК**.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Щелкните **Закрыть**.  
  
## <a name="see-also"></a>См. также:  
 [Отправка документов в библиотеку SharePoint (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [Создание общих источников данных и управление ими (службы Reporting Services в режиме интеграции с SharePoint)](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)   
 [Подключения к данным, источники данных и строки подключения &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
  
  
