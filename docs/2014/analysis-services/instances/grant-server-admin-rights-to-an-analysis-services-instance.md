---
title: Предоставление разрешений администратора сервера (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4af61a59de6175d4241cb6b1b9700ff7ba816430
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328854"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a>Предоставление разрешений администратора сервера (службы Analysis Services)
  Члены роли администратора сервера в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеют неограниченный доступ ко всем объектам и данным данного экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Для выполнения любых задач на уровне сервера, например для создания или обработки базы данных, изменения свойств сервера или запуска трассировки (кроме обработки событий), пользователь должен быть членом роли администратора сервера.  
  
 Членство в ролях определяется при установке служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Пользователь, выполняющий программу установки, может добавить себя к этой роли или добавить другого пользователя при провизионировании сервера. Используя следующую процедуру, можно изменять членство в роли после установки.  
  
## <a name="modify-server-role-membership"></a>Изменение членства в роли сервера  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], в обозревателе объектов щелкните правой кнопкой мыши имя экземпляра и выберите пункт **Свойства**.  
  
2.  На панели **Выбор страницы** щелкните **Безопасность** и нажмите кнопку **Добавить** , расположенную в нижней части страницы, чтобы добавить к роли сервера одного или нескольких пользователей или групп Windows.  
  
     ![Добавить пользователей диалоговое окно в среде management studio](../media/ssas-serveradminadd.png "добавить пользователей диалоговое окно в среде management studio")  
  
 Во время установки программа установки SQL Server требует указания по крайней мере одной учетной записи пользователя в качестве администратора служб Analysis Services.  
  
 По умолчанию члены локальной группы администраторов автоматически получают права администраторов в службе Analysis Server. Хотя локальной группе явно не предоставлено членство в роли администратора сервера [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , локальные администраторы могут создавать базы данных, создавать пользователей и разрешения и выполнять другие разрешенные системным администраторам задачи. Это настраивается. Он определяется `BuiltinAdminsAreServerAdmins` свойства сервера, которому присвоено значение **true** по умолчанию. Это свойство вы можете изменить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Security Properties](../server-properties/security-properties.md).  
  
 Ролями сервера вы можете также управлять с помощью объектов AMO. Дополнительные сведения см. в разделе [Разработка объектов управления аналитикой (объекты AMO)](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
## <a name="see-also"></a>См. также  
 [Авторизация доступа к объектам и операциям &#40;служб Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Роли безопасности &#40;службы Analysis Services — многомерные данные&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  
