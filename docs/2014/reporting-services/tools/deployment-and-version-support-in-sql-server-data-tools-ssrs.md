---
title: Развертывание и поддержка версий в SQL Server Data Tools (SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 36f5686d-7e40-4f31-be81-bd197ca33a02
caps.latest.revision: 17
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 856834aa8c29ebaba0661012383d52ad30e3ad59
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37313236"
---
# <a name="deployment-and-version-support-in-sql-server-data-tools-ssrs"></a>Развертывание и поддержка версий в SQL Server Data Tools (SSRS)
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] поддерживает следующие сценарии:  
  
-   Открытые определения отчетов (*RDL) и проекты сервера отчетов (\*RPTPROJ).  
  
-   Создайте определения отчетов.  
  
-   Просмотрите отчеты в конструкторе отчетов.  
  
-   Разверните отчеты на серверах отчетов.  
  
##  <a name="bkmk_ConfigurationandDeploymentProperties"></a> Свойства настройки и развертывания  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] поддерживает конфигурации проекта. Конфигурация проекта состоит из набора свойств, определяющего местоположения и поведения в том случае, когда проект создан в качестве шага просмотра или развертывания отчетов. Дополнительные сведения о конфигурациях проекта см. в документации по Visual Studio.  
  
 Используйте конфигурации проектов, чтобы управлять обновлением определений отчетов до версий схем, совместимых с целевыми серверами отчетов. Конфигурация проекта включает такие свойства, как целевой сервер отчетов, папка, где процесс построения временно сохраняет определения отчетов для предварительного просмотра и развертывания, и уровни ошибок.  
  
 Построение отчетов производится перед подготовкой к просмотру в конструкторе отчетов или развертыванием на сервере отчетов.  
  
 Задать свойства конфигурации можно в диалоговом окне среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] **Свойства проекта** .  
  
 Свойства построения и развертывания включают:  
  
-   OutputPath — свойство сборки, показывающее путь к папке для хранения определения отчета, используемого при проверке сборки, развертывании и просмотре отчетов.  
  
-   ErrorLevel — свойство сборки, отображающее серьезность проблем сборки, помечаемых как ошибки. Проблемы, степень серьезности которых меньше значения ErrorLevel или равна ему, выводятся как ошибки. В противном случае они помечаются как предупреждения. Дополнительные сведения см. в подразделе "Проверка отчета и уровни ошибок" раздела [Разработка отчетов с использованием конструктора отчетов (SSRS)](design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
-   TargetServerVersion — это свойство развертывания, задающее ожидаемую версию служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которая установлена на целевом сервере отчетов, указанном в свойстве TargetServerURL.  
  
 Если указывается более ранняя версия служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в диалоговом окне **Свойства проекта** , отчеты не преобразуются автоматически в предыдущую версию. По сути дела, проект сервера отчетов может содержать отчеты из двух разных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда развертывается проект сервера отчетов, все отчеты в проекте преобразуются в версию, указанную в TargetServerVersion.  
  
 К проекту может быть добавлено более одной конфигурации проекта. Разные конфигурации используются для разных сценариев, например для развертывания в разных версиях серверов отчетов. Дополнительные сведения см. в разделах [Задание свойства развертывания (службы Reporting Services)](set-deployment-properties-reporting-services.md) и [Диалоговое окно страниц свойств проекта](project-property-pages-dialog-box.md).  
  
##  <a name="bkmk_SupportedVersions"></a> Поддерживаемые версии  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], которая является 32-разрядной версией среды разработки для проектов сервера отчетов, не предназначена для работы на компьютерах архитектуры [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] и не устанавливается на серверах с архитектурой [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]. Однако имеется поддержка среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] для компьютеров с архитектурой x64.  
  
 В приведенной ниже таблице описаны поддерживаемые версии для создания и публикации отчетов в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Схема не изменялась после [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
|Тип проекта или файла|Версия|Разработка отчетов|Публикация отчетов|Примечания|  
|--------------------------|-------------|--------------------|---------------------|-----------|  
|Проект сервера отчетов<br /><br /> или диспетчер конфигурации служб<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Схема языка определения отчетов версии 2014|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Проект сервера отчетов<br /><br /> или диспетчер конфигурации служб<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|Схема языка определения отчетов версии 2012|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Проект сервера отчетов<br /><br /> или диспетчер конфигурации служб<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|Схема языка определения отчетов версии 2008 R2|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]||  
|Проект сервера отчетов<br /><br /> или диспетчер конфигурации служб<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|Схема языка определения отчетов версии 2008|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Только сервер отчетов служб|Производит локальное обновление схем языка определения отчетов с версий 2003 и 2005 до версии 2008.|  
|Проект сервера отчетов<br /><br /> или диспетчер конфигурации служб<br /><br /> Проект мастера сервера отчетов|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Схема языка определения отчетов версии 2005|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сервера отчетов||  
|Проект сервера отчетов|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|Схема языка определения отчетов версии 2003|Не поддерживается||  
|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Конструктор отчетов RDLC|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 2005<br /><br /> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 2008|Схема языка определения отчетов версии 2005|Не поддерживается|Схема языка определения отчетов версии 2008 не поддерживается.|  
|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Элементы управления средства просмотра|[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 2005<br /><br /> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 2008|Язык определения отчетов версии 2008 не поддерживается в локальном режиме|Недоступно|Можно просматривать отчеты языка определения Отчетов 2008 на [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] сервера отчетов в режиме сервера.|  
  
 Дополнительные сведения об открытии отчетов в предыдущей версии схемы определения отчета см. в разделе [обновление отчетов](../install-windows/upgrade-reports.md). Дополнительные сведения о конкретных схемах определений отчетов см. в разделе [Спецификация по языку определения отчетов](http://go.microsoft.com/fwlink/?linkid=116865).  
  
## <a name="see-also"></a>См. также  
 [Публикация источников данных и отчетов](../reports/publishing-data-sources-and-reports.md)  
  
  
