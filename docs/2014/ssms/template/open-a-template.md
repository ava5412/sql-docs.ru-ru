---
title: Открытие шаблона | Документация Майкрософт
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
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 108f68c9501e4af37a2a2a1ee29787738b638522
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240034"
---
# <a name="open-a-template"></a>Открытие шаблона
  Можно открыть шаблон в обозревателе шаблонов.  
  
## <a name="to-open-a-template-from-template-explorer"></a>Открытие шаблона в Обозревателе шаблонов  
 Можно открыть шаблоны в обозревателе шаблонов.  
  
1.  Чтобы открыть обозреватель шаблонов, выберите пункт **Обозреватель шаблонов** в меню **Вид**.  
  
2.  В списке категорий шаблонов разверните категорию, в которой находится нужный шаблон.  
  
3.  Предусмотрены три способа открыть шаблон.  
  
    1.  Дважды щелкните шаблон, чтобы открыть его в окне редактора кода.  
  
    2.  Щелкните шаблон правой кнопкой мыши и выберите в меню пункт **Открыть** , чтобы открыть его в окне редактора кода.  
  
    3.  Перетащите шаблон в окно редактора кода, чтобы добавить код шаблона в содержимое окна редактора.  
  
 Нужные значения аргументов открытого шаблона задаются в окне **Замена параметров шаблона** .  
  
 При открытии шаблона запускается новое окно редактора. Окно редактора откроется с учетными данными текущего активного соединения. Например, если выбрать экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в обозревателе объектов при открытии шаблона CREATE DATABASE, откроется новое окно редактора кода с подключением к этому экземпляру. Если активных соединений нет, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] представит диалоговое окно входа.  
  
## <a name="see-also"></a>См. также  
 [Обозреватель шаблонов](template-explorer.md)   
 [Замена параметров шаблона](replace-template-parameters.md)  
  
  
