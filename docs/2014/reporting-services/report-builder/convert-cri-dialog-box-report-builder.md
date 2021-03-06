---
title: Диалоговое окно "Преобразование пользовательских элементов отчета" (построитель отчетов) | Документы Майкрософт
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
- "10008"
helpviewer_keywords:
- CRI
- custom report items
ms.assetid: 2a3f2ac6-667e-4498-8b73-9c40beb993f5
caps.latest.revision: 17
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8fcaa229bfc685e8e9315086f963d5bc9f74a613
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247854"
---
# <a name="convert-cri-dialog-box-report-builder"></a>Диалоговое окно «Преобразование пользовательских элементов отчета» (построитель отчетов)
  Этот отчет содержит пользовательские элементы отчетов с неподдерживаемыми функциями. Пользовательские элементы отчетов представляют собой расширения языка определения отчетов, которые поддерживают пользовательские объекты, отображающие данные в отчете. Пользовательские элементы отчета включают компоненты времени разработки и времени выполнения, поставляемые сторонними поставщиками программного обеспечения.  
  
> [!NOTE]  
>  Решение о поддержке пользовательских элементов отчетов на сервере отчетов принимает системный администратор. Чтобы можно было просматривать пользовательские элементы в отчете, компоненты CRI должны быть установлены на системе клиента, создающего отчеты, для предварительного просмотра отчета и на сервере отчетов для просмотра опубликованного или переданного отчета. Дополнительные сведения см. в [Custom Report Items](../custom-report-items/custom-report-items.md)и в документации стороннего поставщика программного обеспечения.  
  
 Некоторые пользовательские элементы в отчете могут быть преобразованы в элементы отчета в новом формате определения отчета. При открытии отчета появляется запрос на обновление. Используйте следующие сведения, чтобы решить, какие пользовательские элементы отчета нужно преобразовать.  
  
-   **Да** Выберите **Да** , чтобы преобразовать все пользовательские элементы в отчете, где возможно. Неподдерживаемые функции в пользовательских элементах отчета нельзя обновить и удалить из файла определения отчета. Список неподдерживаемых функций, см. в разделе [обновление отчетов](../install-windows/upgrade-reports.md). При просмотре отчета можно увидеть различия в способах отображения пользовательских элементов в отчете.  
  
-   **Нет** Выберите **Нет** , если не нужно преобразовать пользовательские элементы в отчете. Эти пользовательские элементы отчета в их текущей версии невозможно отобразить с помощью обработчика отчета. Если системный администратор планирует установить новую версию пользовательского элемента отчета от стороннего поставщика программного обеспечения, которая совместима с новым форматом определения отчета, то следует выбрать **Нет**. До тех пор, пока не появятся новые версии, пользовательские элементы отчета отображаются в отчете как пустые текстовые поля с красным символом «X».  
  
 В обоих случаях отчет обновляется до нового формата определения отчета, и резервная копия исходного отчета сохраняется как *\<Имя отчета>* `-` Backup.rdl. При сохранении отчета в средстве создания отчетов выполняется сохранение обновленного отчета в новом формате определения отчета. Если отчет публикуется, то отчет сначала сохраняется в компьютере пользователя, а затем публикуется на сервере отчетов. Обновленная версия отчета публикуется на сервере отчетов.  
  
 Если отчет не сохраняется, то исходный отчет остается неизмененным. Однако этот отчет нельзя изменить в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] более поздней версии или в среде создания отчетов, которая использует данный формат определения отчета. Можно продолжить выполнять исходную версию отчета, загрузив ее на сервер отчетов для работы с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней версией служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с помощью диспетчера отчетов. Дополнительные сведения см. в разделе [Передача файла или отчета (диспетчер отчетов)](../reports/upload-a-file-or-report-report-manager.md).  
  
 Для отчетов, которые передаются вместо публикации на сервере отчетов, обработчик отчета отчета определяет, можно ли обновить отчет при первом использовании. Отчеты, которые нельзя обновить, обрабатываются в режиме обратной совместимости и продолжают отображаться, как в предыдущей версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения см. в разделе [Upgrade Reports](../install-windows/upgrade-reports.md).  
  
 Инструкции по определению текущей версии формата определения отчета для сервера отчетов или средства разработки отчетов см. в разделе [Определение версии схемы определения отчета (SSRS)](../reports/find-the-report-definition-schema-version-ssrs.md).  
  
## <a name="see-also"></a>См. также  
 [Справка построителя отчетов для диалоговых окон, панелей и мастеров](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
