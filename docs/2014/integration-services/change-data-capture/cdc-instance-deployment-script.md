---
title: Скрипт развертывания экземпляра CDC | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b8f895fb591d8cf909632aeab4e48d31bbcb343
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173145"
---
# <a name="cdc-instance-deployment-script"></a>Скрипт развертывания экземпляра CDC
  Диалоговое окно «Скрипт развертывания экземпляра CDC», в котором отображается скрипт развертывания экземпляра CDC. С помощью этого скрипта можно воссоздавать базу данных CDC со всеми ее артефактами на другом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 После выполнения скрипта развертывания необходимо проверить следующее.  
  
-   Скрипт развертывания предполагает, что целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был подготовлен для CDC в консоли настройки службы CDC Oracle или с помощью **скрипта подготовки** , сформированный этой программой.  
  
-   Часть скрипта, которая используется для обеспечения работы CDC в базе данных, должен запускать `sysadmin`.  
  
-   Скрипт не сохраняет пароль Oracle для интеллектуального анализа журнала. Его необходимо задать вручную после завершения работы скрипта и запуска службы CDC Oracle.  
  
 В диалоговом окне **Скрипт развертывания экземпляра CDC** выберите следующие параметры.  
  
 **Сохранить как**  
 Сохранение скрипта в текстовый файл, который можно разместить в любом каталоге. Файл со скриптом можно скопировать на любой другой сервер, чтобы выполнить его там.  
  
 **Копировать**  
 Копирует скрипт в буфер обмена. Затем скрипт можно будет вставить в среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или любой текстовый редактор для последующего выполнения.  
  
## <a name="see-also"></a>См. также  
 [Подготовка SQL Server для CDC](prepare-sql-server-for-cdc.md)  
  
  
