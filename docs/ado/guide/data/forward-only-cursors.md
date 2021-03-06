---
title: Однопроходные курсоры | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], forward-only
- forward-only cursors [ADO]
ms.assetid: 2b1e062f-3294-4a6f-8241-a17045c4df18
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a309a34d8b5a897c62de6bdceb1db2eef4d46c2
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271483"
---
# <a name="forward-only-cursors"></a>Однопроходные курсоры
Обычно по умолчанию используется тип курсора, вызывается курсора однонаправленные (или без прокрутки), можно переместить только вперед по результирующему набору. Однонаправленный курсор не поддерживает прокрутку (возможность перемещаться вперед и назад в результирующем наборе); он поддерживает только выборки строк от начала до конца результирующего набора. С помощью некоторых однонаправленные курсоры (таких как библиотеки курсоров SQL Server), что все insert, update и delete инструкции внесенные текущим пользователем (или зафиксированные другими пользователями), влияющих на строки результирующего набора, отображаются как строки, выбранные. Так как курсор не может быть прокручен назад, однако изменений, сделанных в строках в базе данных после получения строки, не видны через курсор.  
  
 После обработки данных для текущей строки курсора однонаправленные освобождает ресурсы, используемые для хранения этих данных. Однопроходные курсоры являются динамическими по умолчанию, это означает, что все изменения обнаруживаются в процессе обработки текущей строки. Это обеспечивает более быстрое открытия курсора и позволяет результирующий набор, чтобы отобразить обновления в базовых таблицах.  
  
 Хотя однонаправленные курсоры не поддерживают прокрутку назад, приложение может возвращать результирующий набор, закрытие и повторное открытие курсора в начало. Это эффективный способ работы с небольшими объемами данных. В качестве альтернативы приложение может считывать результирующего набора, один раз, кэшировать данные локально и перейдите локального кэша данных.  
  
 Если приложение требует прокрутке результирующего набора, однонаправленный курсор не лучший способ получить данные быстро при минимальных издержек. Используйте **adOpenForwardOnly CursorTypeEnum** для указания необходимости использовать однопроходный курсор в ADO.  
  
## <a name="see-also"></a>См. также  
 [Статические курсоры](../../../ado/guide/data/static-cursors.md)   
 [Управляемые набором ключей курсоры](../../../ado/guide/data/keyset-cursors.md)   
 [Динамические курсоры](../../../ado/guide/data/dynamic-cursors.md)
