---
title: Очистка журнала заданий | Документация Майкрософт
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
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 951b5ed4f298d1c2fefdae4ec6e5b3346fdcecaf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317404"
---
# <a name="clear-the-job-history-log"></a>Очистка журнала заданий
  В этом разделе описано, как удалить содержимое журнала заданий агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средствами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для очистки журнала заданий используется:**  
  
     [Среда SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [Управляющие объекты SQL Server](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Дополнительные сведения см. в разделе [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-clear-the-job-history-log"></a>Очистка журнала заданий  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Раскройте узел **Агент SQL Server**, а затем узел **Задания**.  
  
3.  Щелкните правой кнопкой мыши задание и выберите **Просмотреть журнал**.  
  
4.  В **Программе просмотра файла журнала**выберите задание, журнал которого нужно очистить, и выполните одно из следующих действий.  
  
    -   В окне **Удалить журнал**нажмите кнопку **Удалить** , затем **Удалить весь журнал** . Можно удалить как весь журнал заданий, так и только записи, сделанные до указанной даты. Чтобы удалить весь журнал заданий, нажмите кнопку **Удалить весь журнал**. Чтобы удалить из журнала заданий записи определенной давности, нажмите кнопку **Удалить журнал до**и укажите дату.  
  
    -   Чтобы очистить журнал многосерверного задания, нажмите кнопку **Состояние задания** . Нажмите кнопку **Задание**, выберите имя задания, а затем выберите пункт **Просмотреть удаленный журнал заданий**.  
  
5.  Щелкните **Удалить**.  
  
##  <a name="TSQL"></a> Использование Transact-SQL  
  
#### <a name="to-clear-the-job-history-log"></a>Очистка журнала заданий  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
##  <a name="SMO"></a> Использование управляющих объектов SQL Server  
 **Очистка журнала заданий**  
  
 Вызовите метод `PurgeJobHistory` класса `JobServer`, используя выбранный язык программирования, например Visual Basic, Visual C# или PowerShell. Дополнительные сведения см. в статье [Управляющие объекты SQL Server (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
