---
title: Параметры (Загрузка системных объектов) проекта (DB2ToSQL) | Документы Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a36764c5799b78c1de460e5c462d6c28c3d84806
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34775500"
---
# <a name="project-settingsloading-system-objects-db2tosql"></a>Параметры (Загрузка системных объектов) проекта (DB2ToSQL)
На странице загрузки системных объектов **параметры проекта** диалоговое окно позволяет указать, какие объекты системы DB2 SSMA преобразует и загружает в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
Загрузка системных объектов области доступна в **параметры проекта** и **параметры проекта по умолчанию** диалоговые окна:  
  
-   Для задания параметров для всех проектов SSMA на **средства** последовательно выберите пункты **параметры проекта по умолчанию**, выберите тип проекта миграции, для которого требуются параметры для просмотра и изменения из **миграции целевой версии** раскрывающегося списка пункт **Общие** в нижней части левой панели, а затем нажмите кнопку **загрузке системных объектов**.  
  
-   Для задания параметров для текущего проекта на **средства** последовательно выберите пункты **параметры проекта**, нажмите кнопку **Общие** в нижней части левой панели, а затем нажмите кнопку **загрузке системных объектов**.  
  
## <a name="default-settings"></a>Параметры по умолчанию  
Преобразование объектов системы использует системные ресурсы и занимает время. Чтобы повысить производительность, SSMA выбирает только наиболее часто используемые системные объекты, как показано в следующем списке:  
  
-   SYS.DBMS_OUTPUT  
  
-   SYS.DBMS_PIPE  
  
-   SYS. DBMS_UTILITY  
  
-   SYS. СТАНДАРТ  
  
-   SYS. UTL_FILE  
  
-   SYS.DBMS_LOB  
  
-   SYS.DBMS_SQL  
  
-   SYS. DBMS_SESSION  
  
Если объекты DB2 ссылается на дополнительные системные объекты, следует выбрать этих объектов. Если системные объекты, на которые ссылается объектов базы данных DB2 не выбран, SSMA выдает ошибки преобразования. Если возникнут ошибки преобразования, причиной является отсутствие системных объектов, выберите объекты, отсутствующие в этом диалоговом окне. Затем можно повторить преобразование при необходимости.  
  
