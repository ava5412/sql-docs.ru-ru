---
title: 'Задача 10: Добавление преобразования «Нечеткое группирование» для обнаружения повторений | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 90b2b323-babd-464a-8914-9dc5e66aca74
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 843d79da1d5e9aba58a80ea93ee36a68cd689916
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312754"
---
# <a name="task-10-adding-fuzzy-group-transform-to-identify-duplicates"></a>Задача 10. Добавление преобразования «Нечеткое группирование» для обнаружения повторений
  В этой задаче вы добавляете в поток данных преобразование «Нечеткое группирование». Преобразование «Нечеткое группирование» помогает выявить повторения в исходных данных. См. в разделе [преобразованию "Нечеткое группирование"](http://msdn.microsoft.com/library/ms141764.aspx) для получения дополнительных сведений.  
  
1.  Перетащите **Нечеткое группирование** преобразования в **другие преобразования** на **область элементов служб SSIS** для **потока данных** открыть, выбрав вкладку  **Объединение верных и исправленных записей**.  
  
2.  Щелкните правой кнопкой мыши **Нечеткое группирование** преобразования в **потока данных** , а щелкните **Переименовать**. Тип **поставщики группы с совпадающими идентификаторами** и нажмите клавишу **ввод**.  
  
3.  Подключение **объединение верных и исправленных записей** для **поставщики группы с совпадающими идентификаторами** используя голубой соединитель.  
  
     ![Соединение с поставщиками группы с совпадающими идентификаторами](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-01.jpg "соединение с поставщиками группы с совпадающими идентификаторами")  
  
4.  Дважды щелкните **поставщики группы с совпадающими идентификаторами**.  
  
5.  В **редакторе преобразования Нечеткий группу**, нажмите кнопку **New** рядом с полем **с раскрывающимся списком диспетчера соединений OLE DB** для запуска **настроить соединение OLE DB Диспетчер** диалоговое окно.  
  
6.  В диалоговом окне щелкните **New** для запуска **диспетчер соединений** диалоговое окно.  
  
7.  Тип **(local)** или **период** (.) для имени сервера.  
  
8.  Выберите **MDS** для **выберите или введите имя базы данных** поля. Базу данных MDS будет использоваться в качестве временного хранилища для **преобразование Нечеткое группирование**. **"Нечеткое группирование"** преобразования требуется подключение к экземпляру SQL Server для создания временных таблиц SQL Server, необходимые алгоритму преобразования для выполнения своей работы. Для этой цели вы можете создать базу данных или использовать существующую базу данных.  
  
9. Нажмите кнопку **проверить подключение** для проверки соединения и нажмите кнопку **ОК** в окне сообщения.  
  
10. В **диспетчер соединений** диалоговом окне щелкните **ОК**.  
  
11. Выберите **(local). MDS** (или **localhost. MDS**) из **список подключений к данным** и нажмите кнопку **ОК**.  
  
12. В **редактор преобразования Нечеткое группирование**, убедитесь, что **(local). MDS** или **localhost. MDS** выбран для **диспетчера соединений OLE DB**.  
  
13. Переключиться в режим **столбцы** вкладки.  
  
14. Выберите (флажок) **SupplierID_Output** из списка **доступные входные столбцы**. Чтобы настроить преобразование, выберите входные столбцы, которые будут использоваться для поиска повторений. Для простоты на этом шаге используется только столбец SupplierID.  
  
     ![Редактор преобразования Нечеткое группирование](../../2014/tutorials/media/et-addingfgttoidentifyduplicates-02.jpg "редактор преобразования Нечеткое группирование")  
  
15. Нажмите кнопку **ОК** закрыть **редакторе преобразования Нечеткий группу**.  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 11. Добавление преобразования "Условное разбиение" для фильтрации повторений](../../2014/tutorials/task-11-adding-conditional-split-transform-to-filter-duplicates.md)  
  
  
