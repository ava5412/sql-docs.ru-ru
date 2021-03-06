---
title: Использование выражения в компоненте потока данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], data flow
- expressions [Integration Services], data flow components
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
caps.latest.revision: 26
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 17cc690bc616cfcdaab294eba5db2338c7d02e62
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252325"
---
# <a name="use-an-expression-in-a-data-flow-component"></a>Использование выражения в компоненте потока данных
  Ниже описана процедура добавления выражения в преобразование «Условное разбиение» или «Производный столбец». Преобразование «Условное разбиение» с помощью выражений определяет условия, которые направляют строки данных в выход преобразования, а преобразование «Производный столбец» с помощью выражений определяет значения, присваиваемые столбцам.  
  
 Чтобы реализовать выражение в преобразовании, необходимо, чтобы в пакете уже была хотя бы одна задача потока данных и один источник. Сведения о добавлении элементов к пакетам см. в следующих разделах:  
  
-   [Добавление задачи или контейнера в поток управления или удаление их из него](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
    
  
-   [Добавление или удаление компонента в потоке данных](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
-   [Соединение компонентов в потоке данных](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-create-an-expression"></a>Создание выражения  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  В конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] перейдите на вкладку **Поток управления** , затем щелкните задачу потока данных, содержащую поток данных, в котором нужно реализовать выражение.  
  
4.  Перейдите на вкладку **Поток данных** и перетащите преобразование «Условное разбиение» или «Производный столбец» из окна **Область элементов** в область конструктора.  
  
5.  Перетащите зеленый соединитель из источника или преобразования в преобразование «Условное разбиение» или «Производный столбец».  
  
6.  Дважды щелкните преобразование, чтобы открыть его диалоговое окно.  
  
7.  В левой панели разверните узел **Переменные** для отображения системных и пользовательских переменных, затем разверните узел **Столбцы** . Отобразятся входные столбцы преобразования.  
  
8.  В правой панели разверните узлы **Математические функции**, **Строковые функции**, **Функции даты-времени**, **Функции NULL**, **Приведения типов**и **Операторы** для доступа к функциям, операторам приведения и операторам, предоставляемым грамматикой выражения.  
  
9. В зависимости от вида преобразования выполните одно из следующих действий для создания выражения.  
  
    -   В диалоговом окне **Редактор преобразования «Условное разбиение»** перетащите переменные, столбцы, функции, операторы и приведения в столбец **Условие** . Также можно ввести выражение непосредственно в столбец **Условие** .  
  
    -   В диалоговом окне **Редактор преобразования «Производный столбец»** перетащите переменные, столбцы, функции, операторы и приведения в столбец **Выражение** . Также можно ввести выражение непосредственно в столбец **Выражение** .  
  
        > [!NOTE]  
        >  При переключении фокуса со столбца **Условие** или **Выражение** текст выражения может быть выделен, что указывает на ошибку в синтаксисе выражения.  
  
10. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно.  
  
    > [!NOTE]  
    >  Если выражение является недопустимым, появится предупреждение с описанием синтаксических ошибок данного выражения.  
  
## <a name="see-also"></a>См. также  
 [Выражения служб Integration Services (SSIS)](expressions/integration-services-ssis-expressions.md)   
 [Преобразование «Условное разбиение»](data-flow/transformations/conditional-split-transformation.md)   
 [Преобразование «Производный столбец»](data-flow/transformations/derived-column-transformation.md)   
 [Задача потока данных](control-flow/data-flow-task.md)   
 [Поток данных](data-flow/data-flow.md)  
  
  
