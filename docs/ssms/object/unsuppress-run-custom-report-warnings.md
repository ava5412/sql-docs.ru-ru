---
title: Отмена запрета предупреждений для пользовательских отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5952681cf102d162c7e4b2d930509ab580667ee8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33043941"
---
# <a name="unsuppress-run-custom-report-warnings"></a>Отмена подавления предупреждений для пользовательских отчетов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Для пользовательских отчетов предусмотрено два типа предупреждающих диалоговых окон. В этом разделе описано, как отменить подавление отображения этих полей в [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
По умолчанию перед запуском пользовательского отчета отображается диалоговое окно **Запустить пользовательский отчет** . Если установить флажок **Больше не показывать это предупреждение** , то это диалоговое окно больше отображаться не будет. Также по умолчанию диалоговое окно **Запустить пользовательский отчет** отображается, если после открытия одного пользовательского отчета нажать ссылку для открытия другого отчета. В этом диалоговом окне отображается полный путь к файлу пользовательского детализированного отчета. Если установить флажок **Больше не показывать это предупреждение** , то это диалоговое окно больше отображаться не будет.  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>Отмена подавления основного диалогового окна предупреждения для пользовательских отчетов  
  
1.  Подключитесь к файлу \<*сервер*>\\<*общая папка*>|\<*диск*>\Documents and Settings\\<UserProfile>\Application Data\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml.  
  
2.  Щелкните правой кнопкой мыши файл **reports.xml**и выберите команду **Изменить**.  
  
3.  Измените значение **<SuppressWarning>true\<\/SuppressWarning> на <SuppressWarning>false\<\/SuppressWarning>**.  
  
4.  Перезапустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>Отмена подавления диалогового окна предупреждений для детализированных пользовательских отчетов  
  
1.  Подключитесь к файлу \<*сервер*>\\<*общая папка*>|\<*диск*>\Documents and Settings\\<UserProfile>\Application Data\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml.  
  
2.  Щелкните правой кнопкой мыши файл **reports.xml**и выберите команду **Изменить**.  
  
3.  Измените значение  **<SuppressDrillthroughWarning>true\<\/SuppressDrillthroughWarning> на <SuppressDrillthroughWarning>false\<\/SuppressDrillthroughWarning>**.  
  
4.  Перезапустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
## <a name="see-also"></a>См. также:  
[Пользовательские отчеты в среде Management Studio](../../ssms/object/custom-reports-in-management-studio.md)  
[Добавление пользовательского отчета в среду Management Studio](../../ssms/object/add-a-custom-report-to-management-studio.md)  
[Использование пользовательских отчетов совместно со свойствами узлов обозревателя объектов](../../ssms/object/use-custom-reports-with-object-explorer-node-properties.md)  
  
