---
title: Экспорт политики управления на основе политик | Документация Майкрософт
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
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9347cf49d82af9d8d758137e1fac7dee18ca5ecd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288940"
---
# <a name="export-a-policy-based-management-policy"></a>Экспорт политики управления на основе политик
  В этом разделе описывается экспорт политики управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Экспорт политики с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-export-a-policy"></a>Экспорт политики  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть сервер, содержащий политику управления на основе политик, которую необходимо экспортировать.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните знак «плюс», чтобы развернуть папку **Политики** .  
  
5.  Щелкните правой кнопкой мыши политику, которую необходимо экспортировать, а затем выберите пункт **Экспортировать политику**.  
  
6.  В диалоговом окне **Экспорт политики** введите в адресной строке имя файла и путь к нему. Также можно найти подходящее расположение для файла в области панели навигации диалогового окна, а затем ввести имя XML-файла в поле **Имя файла** .  
  
7.  После завершения нажмите кнопку **Сохранить**.  
  
  
