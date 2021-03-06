---
title: Редактор источника ODBC (страница "столбцы") | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.columns.f1
ms.assetid: 565984eb-8318-4be7-bebc-262209cf5065
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b16be16730643cc063b39594c8e01f1321b6a983
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209434"
---
# <a name="odbc-source-editor-columns-page"></a>Редактор источника «ODBC» (страница «Столбцы»)
  Страница **Столбцы** диалогового окна **Редактор источника ODBC** используется для сопоставления выходного столбца с каждым внешним (исходным) столбцом.  
  
 Дополнительные сведения об источнике ODBC см. в разделе [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="task-list"></a>Список задач  
 **Открытие страницы «Столбцы» редактора источника ODBC**  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]откройте пакет служб [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] , содержащий источник ODBC.  
  
2.  На вкладке **Поток данных** дважды щелкните источник ODBC.  
  
3.  В окне **Редактор источника ODBC**нажмите кнопку **Столбцы**.  
  
## <a name="options"></a>Параметры  
  
### <a name="available-external-columns"></a>Доступные внешние столбцы  
 Список доступных внешних столбцов источника данных. В этой таблице нельзя добавлять или удалять столбцы. Выберите используемые столбцы источника. Выбранные столбцы добавляются в список **Внешний столбец** в порядке выбора.  
  
 Чтобы выбрать все столбцы, установите флажок **Выделить все** .  
  
### <a name="external-column"></a>Внешний столбец  
 Представление внешних (исходных) столбцов в порядке, заданном при настройке компонентов, которые обрабатывают данные из источника ODBC.  
  
### <a name="output-column"></a>Выходной столбец  
 Введите уникальное имя для каждого выходного столбца. По умолчанию используется имя выбранного внешнего (исходного) столбца, однако можно выбрать любое уникальное описательное имя. Введенное имя отображается в конструкторе служб SSIS.  
  
## <a name="see-also"></a>См. также  
 [Редактор источника ODBC &#40;страницы диспетчера соединений&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md)   
 [Редактор источника ODBC &#40;странице вывода ошибок&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
