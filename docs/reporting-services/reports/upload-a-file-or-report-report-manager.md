---
title: Передача файла или отчета на сервер отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 8c2adad2eef1350897bcae24bfdde434ecfeecff
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084866"
---
# <a name="upload-a-file-or-report-in-the-report-server"></a>Передача файла или отчета на сервер отчетов
На веб-портале сервера отчетов предусмотрена функция передачи, позволяющая добавлять отчеты и другие файлы на сервер отчетов без публикации этих элементов из клиентского приложения. Файлы, переданные из файловой системы, сохраняются на сервере отчетов как элементы. Способ сохранения зависит от типа передаваемого файла.  
  
-   RDL-файлы сохраняются как отчеты с разбивкой на страницы.  
  
-   Все другие файлы, включая файлы общих источников данных (RDS), передаются как ресурсы. Ресурсы не обрабатываются сервером отчетов, но могут быть просмотрены на веб-портале, если сервер отчетов поддерживает тип MIME файла.  
  
### <a name="to-upload-a-file-or-report"></a>Передача файла или отчета  
  
1.  На веб-портале щелкните **Передать**.  
  
4.  Найдите файл, который требуется передать. Можно выгружать файл определения отчета, изображение, документ и любой другой файл, который нужно сделать доступным на сервере отчетов.  
  
5.  Введите имя нового элемента. Имя элемента может включать пробелы, но не может включать зарезервированные символы: ; ? : \@ & = + , $ / * < > |.  
  
6.  Если нужно заменить существующий элемент новым, установите флажок **Перезаписывать существующие элементы**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:   
[Создание, изменение и удаление общих источников данных](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)
[Передача файлов в папку](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  
