---
title: Создание политики управления на основе политик | Документация Майкрософт
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
- Policy-Based Management, creating policies
ms.assetid: b28bf963-89f9-4941-b6c1-6004fec347f1
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: dec5fa8f9f5ec6d1b4784cea1f1f92654b1fa69d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294574"
---
# <a name="create-a-policy-based-management-policy"></a>Создание политики управления на основе политик
  В этом разделе описывается создание политики управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Создание политики с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-policy"></a>Создание политики  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, на котором необходимо создать новую политику управления на основе политик.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните правой кнопкой мыши папку **Политики** и выберите команду **Создать политику**.  
  
5.  В диалоговом окне **Создание новой политики** в поле **Имя** введите имя новой политики.  
  
6.  Установите флажок **Включено** , если требуется, чтобы политика была включена сразу после ее создания. Если режим вычисления имеет значение **По запросу**, флажок **Включено** недоступен.  
  
7.  В списке **Проверить условие** выберите одно из существующих условий или укажите пункт **Создать условие**. Для изменения условия выберите его и нажмите кнопку с многоточием (**...**). Дополнительные сведения см. в статье [Создание нового условия управления на основе политик](create-a-new-policy-based-management-condition.md) или [Просмотр или изменение свойств условия управления на основе политик](view-or-modify-the-properties-of-a-policy-based-management-condition.md).  
  
8.  Выберите один или несколько типов целевого объекта для данной политики в окне **Применить к** . Некоторые условия и аспекты можно применить только к определенным типам целей. Доступные наборы целей появляются в соответствующем окне. Чтобы выбрать условие фильтрации для некоторых типов целей, разверните **Каждый** . Если в разделе не появляются целевые объекты, убедитесь, что условие ограничено уровнем сервера.  
  
9. Выберите тип поведения данной политики в окне **Режим вычисления** . Разные условия могут иметь разные допустимые режимы вычисления. Дополнительные сведения о допустимых режимах вычисления см. в статье [Администрирование серверов с помощью управления на основе политик](administer-servers-by-using-policy-based-management.md).  
  
10. Если политика вычисляется по расписанию, установите режим вычисления в состояние **По запросу**и нажмите **Выбрать** для выбора расписания либо нажмите кнопку **Создать** для создания нового расписания.  
  
11. Чтобы ограничить политику поднабором типов целевого объекта, выберите условия в окне **Ограничение сервера** или создайте новое условие.  
  
     Дополнительные сведения о параметрах, доступных в диалоговом окне **Создание новой политики** , см. в разделах [Диалоговое окно «Создание новой политики» или «Открытие политики», страница «Общие»](../../integration-services/general-page-of-integration-services-designers-options.md) и [Диалоговое окно «Создание новой политики» или «Открытие политики», страница «Описание»](create-new-policy-or-open-policy-dialog-box-description-page.md).  
  
12. В завершение нажмите кнопку **ОК**.  
  
  
