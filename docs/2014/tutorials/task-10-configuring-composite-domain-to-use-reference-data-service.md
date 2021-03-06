---
title: 'Задача 10: Настройка составного домена для использования службы ссылочных данных | Документация Майкрософт'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
caps.latest.revision: 8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5abc5bc02b2c7ee365886ba54a603890c4b2aa0f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228354"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Задача 10. Настройка составного домена для использования службы ссылочных данных
  В этой задаче вы настраиваете **проверка адреса** составного домена для использования **Melissa Data — Address Check** службы. Во время выполнения при проведении очистки данных службы DQS передают значения доменов в домен проверки адреса, чтобы служба выполнила очистку данных. См. в разделе [карты домена/составного домена к эталонным данным](http://msdn.microsoft.com/library/hh213030.aspx) для получения дополнительных сведений.  
  
1.  На главной странице **клиента DQS**, нажмите кнопку **Suppliers (Управление доменами)** под **Недавние базы знаний** для запуска **Управление доменами**страницы.  
  
2.  Выберите **проверка адреса** составной домен в **список доменов**.  
  
3.  В области справа перейдите **ссылочных данных** вкладки.  
  
     ![Ссылаться на вкладке данные](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "ссылаться вкладка \"данные\"")  
  
4.  Нажмите кнопку **Обзор** на панели инструментов.  
  
5.  На **Online каталог поставщиков ссылочных данных** выберите **флажок** рядом с полем **Melissa Data — Address Check**.  
  
     ![Выбрать Melissa Data — проверка адреса](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "выбрать Melissa Data — проверка адреса")  
  
6.  В области справа в **схемы** раздел "," Карта **строка адреса** домена **Address Line (M)** элемента схемы с помощью раскрывающегося списка.  
  
     ![Сопоставление элемента схемы RDS с доменом](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "сопоставление элемента схемы RDS с доменом")  
  
7.  Нажмите кнопку **добавить элемент схемы (+)** на панели инструментов, чтобы создать запись в списке.  
  
     ![Добавьте кнопки панели инструментов для записи схемы](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "схемы запись кнопка добавления панели инструментов")  
  
8.  Сопоставьте следующие домены DQS с помощью раскрывающегося списка, как показано на следующем рисунке.  
  
     ![Сопоставление элементов схемы RDS с доменами](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "сопоставление элементов схемы RDS с доменами")  
  
9. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 11. Публикация базы знаний](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
