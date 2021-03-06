---
title: Создание роли пользователей (среда Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: fe31fbe487fbbe1688e9c633482bb5891ea0fa85
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082346"
---
# <a name="new-user-role-management-studio"></a>Создание пользовательской роли (среда Management Studio)
  На этой странице можно создать определение роли на уровне элемента. Определение роли на уровне элемента — это именованная коллекция задач, которые пользователь может выполнять в отношении папок, отчетов, моделей, ресурсов и общих источников данных. Примером определения роли на уровне элемента является заранее определенная роль «Браузер», определяющая типы действий, которые могут понадобиться конечным пользователям отчетов для перемещения по папкам и просмотра отчетов.  
  
 Предполагается, что определений ролей должно быть немного. В большинстве организаций необходимо задать небольшое число определений ролей. Однако если заранее заданных определений ролей недостаточно, их можно изменять или создавать новые.  
  
> [!NOTE]  
>  Определения ролей используются только на сервере отчетов, работающем в собственном режиме. Если сервер отчетов настроен для интеграции с SharePoint, эта страница недоступна.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Имя определения роли. Имя определения роли должно быть уникальным в пределах пространства имен сервера отчетов. Имя должно содержать хотя бы одну букву или цифру. В него могут также входить пробелы и другие символы. При задании имени нельзя использовать следующие символы:  
  
 ; ? : \@ & = + , $ / * < >  
  
 " /  
  
 **Описание**  
 Описание назначения роли с указанием функций, поддерживаемых ею.  
  
 **Задача**  
 Выберите задачи, которые могут выполняться с помощью этой роли. Нельзя создавать новые задачи или изменять существующие, если они поддерживаются службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В определении роли на уровне элемента могут указываться только задачи уровня элемента.  
  
 **Описание задачи**  
 Описание задачи с указанием поддерживаемых ею операций и разрешений.  
  
## <a name="see-also"></a>См. также:  
 [Справка F1 по использованию сервера отчетов среде Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Определение ролей](../../reporting-services/security/role-definitions.md)  
  
  
