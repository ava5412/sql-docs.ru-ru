---
title: Предварительный просмотр отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], previewing reports
- previewing reports [Reporting Services]
- printing previews
- test servers [Reporting Services]
ms.assetid: 85117f6c-828e-45c9-810f-e700d9bfba67
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: afcfb2cf31526f4e8898fafbe72f9492a1848886
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202534"
---
# <a name="previewing-reports"></a>Предварительный просмотр отчетов
  При проектировании отчета может понадобиться просмотреть его до публикации в рабочей среде. Это можно сделать несколькими способами: воспользовавшись вкладкой «Предварительный просмотр» конструктора отчетов, при помощи окна предварительного просмотра в конструкторе отчетов, а также опубликовав отчет на сервере отчетов в тестовом режиме.  
  
> [!NOTE]  
>  При осуществлении предварительного просмотра отчета данные для отчета кэшируются в файл на локальном компьютере. При повторном просмотре того же отчета (с использованием того же запроса, параметров и учетных данных) конструктор отчетов получает кэшированную копию вместо того, чтобы заново выполнять запрос. Файл данных сохраняется под именем *\<имя_отчета>*.rdl.data в том же каталоге, что и файл определения отчета. Этот файл не удаляется, когда конструктор отчетов закрывается.  
  
## <a name="preview-mode"></a>Режим предварительного просмотра  
 Предварительного просмотра отчета в конструкторе отчетов откройте вкладку **предварительной версии**. Тем самым отчет выполнится локально, используя те же возможности обработки отчета и подготовки его к предварительному просмотру, которые обеспечиваются на сервере отчетов. Отчет отображается как интерактивное изображение; можно выбирать параметры, щелкать ссылки, просматривать схему документа, разворачивать и сворачивать скрытые области отчета. Также можно экспортировать отчет в любой из установленных форматов подготовки к просмотру.  
  
## <a name="standalone-preview"></a>Автономный предварительный просмотр  
 Другой способ предварительного просмотра отчета — выполнение проекта отчета в конфигурации отладки; например, это можно сделать для отладки пользовательских сборок. Существуют три способа выполнения проекта:  
  
-   Щелкнув **запустить** на **Отладка** меню.  
  
-   Щелкнув **запустить** кнопку [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] стандартной панели инструментов.  
  
-   Нажатием клавиши F5.  
  
 Если используется конфигурация проекта, которая строит отчет, но не развертывает его, отчет, который указан в `StartItem` свойство текущей конфигурации открывается в отдельном окне предварительного просмотра. Окно предварительного просмотра отображает отчет в том же виде и с теми же возможностями, что и вкладка «Предварительный просмотр».  
  
> [!NOTE]  
>  Прежде чем приступить к отладке отчета, необходимо указать стартовый элемент. Чтобы задать стартовый элемент, в обозревателе решений щелкните правой кнопкой мыши проект отчета, выберите **свойства**, а затем в `StartItem`, выберите имя отчета для отображения.  
  
 Для предварительного просмотра конкретного отчета, не являющегося стартовым элементом проекта, выберите конфигурацию, которая строит отчет, но не развертывает его, например DebugLocal, щелкните правой кнопкой мыши отчет и выберите команду **Выполнить**. Необходимо выбрать конфигурацию, которая не развертывает отчет; в противном случае отчет будет опубликован на сервере отчетов вместо того, чтобы отобразиться локально в окне предварительного просмотра.  
  
## <a name="print-preview"></a>Предварительный просмотр  
 Когда отчет просматривается на вкладке «Предварительный просмотр» или в окне предварительного просмотра, он выглядит так, как если бы он был создан модулем подготовки отчетов в формате HTML. Отчет не является HTML-страницей, но его макет и разбиение на страницы подобны выходному формату HTML.  
  
 Вместо этого отчет можно просмотреть в таком виде, как если бы он был напечатан, путем переключения в режим просмотра печати. Щелкните значок **Предварительный просмотр** на панели инструментов предварительного просмотра. Отчет отобразится в таком виде, как если бы он был напечатан на бумаге. Этот режим просмотра похож на результат работы модуля подготовки отчетов в формате PDF и формате изображения. Предварительный просмотр не является изображением или PDF-файлом, но макет отчета и его разбиение на страницы подобны выходному результату в этих форматах.  
  
## <a name="publishing-to-a-test-server"></a>Публикация на тестовом сервере  
 Отчеты также можно протестировать путем публикации их на тестовом сервере. Публикация отчета на тестовом сервере происходит точно так же, как публикация на производственном сервере. Сведения о публикации отчета см. в разделе [Публикация отчетов на сервере отчетов](publishing-reports-to-a-report-server.md).  
  
## <a name="see-also"></a>См. также  
 [Печать отчетов (построитель отчетов и службы SSRS)](../report-builder/print-reports-report-builder-and-ssrs.md)   
 [Печать отчета (построитель отчетов и службы SSRS)](../report-builder/print-a-report-report-builder-and-ssrs.md)   
 [Публикация отчетов](../publish-reports.md)   
 [Использование пользовательских сборок с отчетами](../custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
