---
title: Занятие 7. Добавление операции детализации к родительскому отчету | Документы Майкрософт
ms.custom: ''
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: aad2da1a-d7b1-4afa-a66a-1ff102e8306f
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: afb72e601ef9715cf0951cbff46c1033aa1c1854
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33015291"
---
# <a name="lesson-7-add-drillthrough-action-on-parent-report"></a>Занятие 7. Добавление операции детализации к родительскому отчету
После добавления элемента управления ReportViewer в приложение веб-сайта далее необходимо добавить действие детализации в родительский отчет.  
  
### <a name="to-add-drillthrough-action-on-the-parent-report"></a>Добавление действия детализации в родительский отчет  
  
1.  Перейдите к родительскому отчету.  
  
2.  Выберите текстовое поле, в котором содержится значение **Имя**.  
  
3.  Щелкните это текстовое поле правой кнопкой мыши и выберите пункт **Свойства текстового поля**.  
  
4.  Перейдите на вкладку **Действие** и выберите параметр **Переход к отчету** .  
  
5.  В разделе **Указать отчет** введите имя дочернего отчета.  
  
    > [!NOTE]
    > Не включайте в имя отчета расширение файла.  
  
6.  В разделе **Использовать эти параметры при выполнении отчета** нажмите кнопку **Добавить** .  
  
7.  Введите **productid** в поле **Имя** , а затем выберите пункт **ProductID** в раскрывающемся списке **Значение** .  
  
8.  Нажмите кнопку **ОК** для завершения.  
  
## <a name="next-task"></a>Следующая задача  
Тем самым в родительский отчет была успешно добавлена операция детализации. Затем необходимо создать фильтр данных для таблицы данных, которая определена в дочернем отчете. См. раздел [Занятие 8. Создание фильтра данных](../reporting-services/lesson-8-create-a-data-filter.md).  
  
  
  

