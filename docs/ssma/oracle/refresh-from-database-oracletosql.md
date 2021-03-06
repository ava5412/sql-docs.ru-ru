---
title: Обновление из базы данных (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 84492f44-c368-4c75-954d-7307a2d2bbc0
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 213fe8ba8569c043ca19c6737be8992da79a17de
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34777890"
---
# <a name="refresh-from-database-oracletosql"></a>Обновление из базы данных (OracleToSQL)
**Обновление из базы данных** диалоговое окно позволяет выбрать объекты для обновления из базы данных Oracle. Строки в диалоговом окне отображаются цветовые обозначения, исходя из состояния метаданных:  
  
-   Если метаданные объекта был изменен локально и в базе данных Oracle, строки — синим.  
  
-   Если метаданные объекта был изменен в базе данных Oracle, но не в SSMA, желтый строки.  
  
-   Если метаданные объекта изменилось локально, но не в базе данных Oracle, строка имеет зеленый цвет.  
  
-   Если объект является новым в базе данных Oracle, строки розовым цветом.  
  
Можно указать параметры обновления объекта по умолчанию в **параметры проекта** диалоговое окно. Дополнительные сведения см. в разделе [параметры проекта&#40;синхронизации&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
Чтобы получить доступ к **обновление из базы данных** диалоговое окно, щелкните правой кнопкой мыши объект в обозревателе метаданных Oracle и нажмите кнопку **обновление из базы данных**.  
  
## <a name="options"></a>Параметры  
**Свернуть (-)**  
Свернуть все группы объектов, чтобы скрыть отдельные объекты.  
  
**Развертывания (+)**  
Разверните все группы объектов для отображения отдельных объектов.  
  
**Скрыть или Показать равно объектов**  
Скрывает объекты из списка, если такой же в базе данных Oracle и SSMA метаданные объекта.  
  
**Обновление из базы данных (кнопка со стрелкой)**  
Используйте кнопку со стрелкой, чтобы указать, что метаданные для выбранных объектов должны быть обновлены в SSMA.  
  
**Выполните обновляется из базы данных (кнопку X)**  
Используйте кнопку «X», чтобы указать, что метаданные для выбранных объектов не должны обновляться в SSMA.  
  
**Условные обозначения**  
Отображает **условных обозначений** диалоговое окно. Легенда содержит сопоставление между цвета строк и состояния метаданных.  
  
Чтобы сохранить **условных обозначений** диалоговое окно на основе **обновление из базы данных** выберите **Показывать в верхней части** флажок.  
  
