---
title: Удаление строк на панели результатов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 950a47653592011cbcf3cd0a9249825c0bf70209
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170175"
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a>Удаление строк на панели «Результаты» (визуальные инструменты для баз данных)
  Удалите строки на панели «Результаты» если нужно удалить записи в базе данных. Чтобы удалить все строки, можно использовать запрос «Delete». Дополнительные сведения см. в разделе [Создание запросов на удаление (визуальные инструменты для баз данных)](visual-database-tools.md). Если необходимо только удалить строки из панели «Результаты», измените критерии для запроса. Дополнительные сведения см. в разделе [Определение критериев поиска (визуальные инструменты для баз данных)](specify-search-criteria-visual-database-tools.md).  
  
### <a name="to-delete-a-row-or-rows"></a>Удаление строки или строк  
  
1.  Установите флажки слева от строки или строк, которые необходимо удалить, на панели «Результаты».  
  
2.  Нажмите клавишу DELETE.  
  
3.  В окне сообщения с требованием подтверждения нажмите кнопку **Да**.  
  
> [!CAUTION]  
>  Строки, удаленные таким способом, окончательно удаляются из базы данных и не могут быть восстановлены в дальнейшем.  
  
> [!NOTE]  
>  Если какие-либо из выбранных строк нельзя удалить из базы данных, ни одна из них не будет удалена, при этом выводится сообщение, указывающее, какие именно строки невозможно удалить.  
  
## <a name="see-also"></a>См. также  
 [Создание запросов на удаление &#40;визуальных инструментах баз данных&#41;](visual-database-tools.md)   
 [Определение критериев поиска (визуальные инструменты для баз данных)](specify-search-criteria-visual-database-tools.md)  
  
  
