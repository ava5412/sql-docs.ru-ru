---
title: Активация функций интеграции Power View в SharePoint и сервера отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 45266427e7946e62a758ce994531126324dca39d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155855"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Активация функций интеграции семейства веб-сайтов с сервером отчетов и Power View в SharePoint
  Функции семейства веб-сайтов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обычно активируются по умолчанию после установки надстройки служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] для продуктов SharePoint. В некоторых ситуациях эти функции требуется активировать вручную.  
  
 При установке надстройки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint 2010 после установки продукта SharePoint функции интеграции с сервером отчетов и с Power View будут активированы только для корневых семейств веб-сайтов. Для других семейств веб-сайтов потребуется активировать эти функции вручную. Например, если имеется семейство **http://[my имя сервера] веб [узел]** необходимо будет вручную активировать [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] возможности семейства узлов.  
  
 Если нет корневого семейства веб-сайтов, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] надстройка будет регистрировать сообщение следующего вида.  
  
 «Веб-приложение SharePoint 80 не содержит корневого семейства веб-сайтов»  
  
 Сообщение будет сохранено в журнале установки надстройки с именем «RS_SP_#.log», где # ― это увеличивающийся номер. Файл журнала сохраняется в папку Temp текущего пользователя, например C:\Users\\[пользователь]\AppData\Local\Temp. Дополнительные сведения о параметрах ведения журнала надстройки см. в разделе [Установка или удаление надстройки служб Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 В этом разделе:  
  
-   [Активация функций семейства веб-сайтов для интеграции с сервером отчетов и Power View](#bkmk_features)  
  
-   [Активация и деактивация функций семейства веб-сайтов для центра администрирования служб Reporting Services](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a> Активация функций семейства веб-сайтов для интеграции с сервером отчетов и Power View  
  
1.  Откройте в браузере веб-сайт, где нужно активировать функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
2.  Щелкните **Действия сайта**.  
  
3.  Щелкните элемент **Настройки сайта**.  
  
4.  Щелкните **Функции семейства веб-сайтов** в группе администраторов семейства веб-сайтов.  
  
5.  Найдите в списке **Функцию интеграции сервера отчетов** или **Функцию интеграции средства Power View** .  
  
6.  Нажмите кнопку **Активировать**.  
  
 Деактивация компонентов выполняется схожим образом, только вместо кнопки **Активировать** нужно нажать кнопку **Деактивировать**.  
  
##  <a name="bkmk_centraladmin"></a> Активация и деактивация функций семейства веб-сайтов для центра администрирования служб Reporting Services  
  
1.  Откройте в браузере центр администрирования SharePoint.  
  
2.  Щелкните **Действия сайта**.  
  
3.  Щелкните элемент **Настройки сайта**.  
  
4.  Щелкните **Функции семейства веб-сайтов** в группе администраторов семейства веб-сайтов.  
  
5.  Найдите в списке пункт **Функция центра администрирования сервера отчетов** .  
  
6.  Нажмите кнопку **Активировать**.  
  
 Деактивация компонента выполняется схожим образом, только вместо кнопки **Активировать** нужно нажать кнопку **Деактивировать**.  
  
## <a name="next-steps"></a>Следующие шаги  
 После активации компонента можно продолжить интеграцию сервера.  
  
## <a name="see-also"></a>См. также  
 [Установка или удаление Reporting Services надстройки для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
