---
title: Диалоговое окно "Сохранить скрипт изменений" (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 531a7b9a4ae7405ef58cba9c5605c3f41c60df79
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274220"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>Диалоговое окно "Сохранить скрипт изменений" (визуальные инструменты для баз данных)
  Это диалоговое окно показывает скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] изменений, сделанных со времени последнего сохранения таблицы. Оно также позволяет сохранить скрипт в текстовом файле в выбранном местоположении.  
  
 Открыть это диалоговое окно также можно после совершения несохраненных изменений таблицы в конструкторе таблиц. В меню **Конструктор таблиц** выберите пункт **Создать скрипт изменения**.  
  
> [!NOTE]  
>  Скрипты изменений, содержащиеся в визуальных инструментах для баз данных, не содержат средств обработки ошибок. Они предполагают, что объекты базы данных не изменились с момента открытия инструментального средства; поэтому возникновение проблем, связанных с изменением объектов, невозможно. Перед выполнением скрипта изменений следует включить соответствующие инструкции обработки ошибок.  
  
## <a name="options"></a>Параметры  
 **Автоматически создавать скрипт изменений при каждом сохранении**  
 Если флажок установлен, то диалоговое окно **Сохранить скрипт изменений** будет выводиться каждый раз при сохранении изменений таблицы.  
  
 **Да**  
 Разверните диалоговое окно **Сохранить** , где можно выбрать местоположение текстового файла.  
  
 **Нет**  
 Отменить создание скрипта изменения.  
  
  
