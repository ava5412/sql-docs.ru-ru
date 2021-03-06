---
title: Добавление типов содержимого сервера отчетов в библиотеку (службы Reporting Services в режиме интеграции с SharePoint) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ac9136c8-9ef4-484c-8e9d-05008a186db5
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: da7ee6e652442bdd2773a8c669b0d134f1fadc37
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177551"
---
# <a name="add-report-server-content-types-to-a-library-reporting-services-in-sharepoint-integrated-mode"></a>добавить в библиотеку типы содержимого сервера отчетов (службы Reporting Services в режиме интеграции с SharePoint)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] обеспечивают стандартные типы содержимого SharePoint, которые используются для управления файлами общих данных источника (RSDS), моделей отчетов (SMDL) и построитель отчетов файлы определения отчетов (RDL). После добавления в библиотеку типов содержимого **Отчет построителя отчетов**, **Модель отчета**и **Источник данных отчета** становится доступной команда **Создать** , позволяющая создавать новые документы этих типов.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint  
  
 Добавить типы содержимого в библиотеку может администратор веб-сайта или пользователь с разрешениями уровня «Полный доступ».  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Содержимого, типы и управление типами содержимого будут автоматически включены во всех библиотеках документов для существующих семейств сайтов, созданных на основе следующего **центра бизнес-аналитики** шаблон узла.  
  
 Для сайтов, созданных после интеграции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , типы содержимого служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] включены не будут.  
  
> [!TIP]  
>  Если у вас есть **не** настроили типы содержимого для библиотеки, сначала включите управление типами содержимого, а затем включите [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] типы содержимого. Процедуры включения управления типами содержимого приведены в библиотеке одного документа.  
  
 **Короткий видеоролик** [(SSRS) включение типов содержимого в SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w).  
  
 **В этом разделе:**  
  
-   [Включение типов содержимого во всех библиотеках документов в существующем центре бизнес-аналитики](#bkmk_enable_all)  
  
-   [Активация управления типами содержимого для одной библиотеки документов (SharePoint 2013)](#bkmk_enable_content_management)  
  
-   [Добавление типов содержимого служб Reporting Services (SharePoint 2013)](#bkmk_add_single)  
  
-   [Активация управления типами содержимого для одной библиотеки документов (SharePoint 2010)](#bkmk_enable_content_management_2010)  
  
-   [Добавление типов содержимого сервера отчетов в библиотеку (SharePoint 2010)](#bkmk_add_single_2010)  
  
-   [Активация типов содержимого и управления содержимым для нескольких сайтов бизнес-аналитики](#bkmk_enable_multiple_sites)  
  
##  <a name="bkmk_enable_all"></a> Включение типов содержимого во всех библиотеках документов в существующем центре бизнес-аналитики  
  
1.  Чтобы включить типы содержимого и управление содержимым во всех библиотеках документов в существующем сайте **центра бизнес-аналитики** , можно переключить компонент интеграции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
2.  Перейдите в раздел **Параметры сайта**.  
  
    -   В SharePoint 2013 щелкните значок **Параметры** . ![Параметры SharePoint](../analysis-services/media/as-sharepoint2013-settings-gear.gif "Параметры SharePoint")  
  
    -   В SharePoint 2010 щелкните **Действия сайта**и выберите **Параметры сайта**.  
  
3.  Щелкните **Компоненты коллекции веб-сайтов**.  
  
4.  Найдите в списке пункт **Компонент интеграции с сервером отчетов** и щелкните **Отключить**.  
  
     ![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")  
  
5.  Обновите браузер, а затем щелкните **Активировать** для пункта **Компонент интеграции с сервером отчетов**.  
  
     ![rs_reportserver_integration_deactive](media/rs-reportserver-integration-deactive.gif "rs_reportserver_integration_deactive")  
  
##  <a name="bkmk_enable_content_management"></a> Активация управления типами содержимого для одной библиотеки документов (SharePoint 2013)  
  
1.  Откройте библиотеку, для которой нужно активировать несколько типов содержимого.  
  
2.  На ленте нажмите кнопку **Библиотека** .  
  
     ![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")  
  
3.  На ленте **Библиотека** щелкните **Параметры библиотеки**. Если вы не видите кнопки **Параметры библиотеки** или если она неактивна, значит у вас нет разрешения на настройку параметров библиотеки, включая типы содержимого.  
  
     ![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")  
  
4.  В разделе **Общие параметры** щелкните **Дополнительные параметры**.  
  
     ![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")  
  
5.  В разделе **Типы содержимого** выберите **Да** , чтобы разрешить управление типами содержимого.  
  
6.  Нажмите кнопку **ОК**.  
  
##  <a name="bkmk_add_single"></a> Добавление типов содержимого служб Reporting Services (SharePoint 2013)  
  
1.  Откройте библиотеку, для которой нужно добавить типы содержимого служб Reporting Services.  
  
2.  На ленте нажмите кнопку **Библиотека**.  
  
3.  Нажмите кнопку **Параметры библиотеки**.  
  
4.  В разделе **Типы содержимого**выберите пункт **Добавить из типов содержимого существующего веб-сайта**.  
  
5.  В разделе **Выберите типы содержимого сайта из списка**выберите элемент **Типы содержимого служб SQL Server Reporting Services**.  
  
6.  В списке **Типы содержимого веб-сайта** щелкните элемент **Построитель отчетов**, а затем нажмите кнопку **Добавить** , чтобы переместить выбранный тип содержимого в список **Добавляемые типы содержимого** .  
  
7.  Чтобы добавить типы содержимого **Модель отчета** и **Источник данных отчета** , повторите предыдущий шаг.  
  
8.  После завершения добавления типов содержимого нажмите кнопку **ОК**.  
  
9. > [!NOTE]  
    >  Если [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] группа типов содержимого **типы SQL Server Reporting Services содержимое** не отображается на **Добавление типов содержимого** страницы, одно из следующих условий верно:  
  
    -   Надстройка служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] для продуктов SharePoint еще не установлена. Дополнительные сведения см. в разделе [Установка или удаление надстройки служб Reporting Services для SharePoint &#40;SharePoint 2010 и SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Раздел включает сведения об установке надстройки и пошаговом выполнении установки файлов надстройки для обхода проблем.  
  
    -   Надстройка установлена, но компонент коллекции сайтов **Компонент интеграции сервера отчетов** неактивен. Проверьте компонент коллекции сайтов в разделе **Параметр сайта**.  
  
    -   Все [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] типы содержимого уже были добавлены в библиотеку. Если типы содержимого уже есть в библиотеке, группа удаляется со страницы **Добавление типов содержимого** . Если удалить один или несколько типов содержимого служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , группа **Типы содержимого служб SQL Server Reporting Services** снова появится на странице **Добавление типов содержимого** .  
  
##  <a name="bkmk_enable_content_management_2010"></a> Активация управления типами содержимого для одной библиотеки документов (SharePoint 2010)  
  
1.  Откройте библиотеку, для которой нужно активировать несколько типов содержимого. На панели меню библиотеки должны быть представлены следующие меню: **Создать**, **Передать**, **Действия**и **Настройки**. Если меню **Параметры**отсутствует, то пользователь не имеет разрешения на добавление типа содержимого.  
  
2.  На ленте **Средства работы с библиотекой** щелкните **Библиотека**.  
  
     ![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")  
  
3.  В группе ленты **Параметры** выберите **Параметры библиотеки**.  
  
4.  В разделе **Общие параметры**выберите **Дополнительные параметры**.  
  
5.  В разделе **Типы содержимого** выберите **Да** , чтобы разрешить управление типами содержимого.  
  
6.  Нажмите кнопку **ОК**.  
  
##  <a name="bkmk_add_single_2010"></a> Добавление типов содержимого сервера отчетов в библиотеку (SharePoint 2010)  
  
1.  Откройте библиотеку, для которой нужно добавить типы содержимого служб Reporting Services.  
  
2.  На вкладках ленты **Средства библиотеки** выберите вкладку **Библиотека**.  
  
3.  В группе ленты **Параметры** выберите **Параметры библиотеки**.  
  
4.  В разделе **Типы содержимого**выберите пункт **Добавить из типов содержимого существующего веб-сайта**.  
  
5.  В разделе **Выбор типов содержимого** в **Выбрать типы содержимого сайта из списка**нажмите кнопку со стрелкой, чтобы выбрать элемент **Типы содержимого служб SQL Server Reporting Services**.  
  
6.  В списке **Типы содержимого веб-сайта** щелкните элемент **Построитель отчетов**, а затем нажмите кнопку **Добавить** , чтобы переместить выбранный тип содержимого в список **Добавляемые типы содержимого** .  
  
7.  Чтобы добавить типы содержимого **Модель отчета** и **Источник данных отчета** , повторите предыдущий шаг.  
  
8.  После завершения добавления типов содержимого нажмите кнопку **ОК**.  
  
##  <a name="bkmk_enable_multiple_sites"></a> Активация типов содержимого и управления содержимым для нескольких сайтов бизнес-аналитики  
  
1.  Для серверов отчетов SQL Server Reporting Services 2008 и 2008 R2 можно включить типы содержимого и управление содержимым для нескольких сайтов центра бизнес-аналитики:  
  
2.  В центре администрирования SharePoint выберите **Общие параметры приложения**. В разделе **SQL Server Reporting Services (2008 и 2008 R2)** щелкните **Интеграция со службами Reporting Services**.  
  
     ![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")  
  
3.  Щелкните **Включить функции во всех имеющихся семействах веб-сайтов**.  
  
     ![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")  
  
4.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Сайт SharePoint и справочник по разрешениям списка для элементов сервера отчетов](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)   
 [Запуск построителя отчетов &#40;построитель отчетов&#41;](report-builder/start-report-builder.md)  
  
  
