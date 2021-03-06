---
title: Создание учетных данных — аутентификация в хранилище Azure | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c08bd603b3b56bb6759e3bc5d1fa34f2e54c5efc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917559"
---
# <a name="create-credential---authenticate-to-azure-storage"></a>Создание учетных данных — проверка подлинности в хранилище Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Чтобы создать новые учетные данные SQL, воспользуйтесь диалоговым окном **Резервное копирование по URL-адресу — создать учетные данные** .  
  
 При создании учетных данных с помощью этого диалогового окна необходимо предоставить сертификат управления Windows Azure, добавленный в локальное хранилище сертификатов, или профиль публикации, загруженный на компьютер для проверки подписки и сведений об учетной записи хранения.  
  
 **Учетные данные SQL**  
 Задайте имя создаваемых учетных данных SQL.  
  
## <a name="windows-azure-credentials"></a>Учетные данные Windows Azure  
 **Сертификат управления**  
 Используйте этот параметр, чтобы указать сертификат из локального хранилища сертификатов, соответствующий сертификату управления из Windows Azure. Дополнительные сведения по сертификату управления Windows Azure см. в разделе [Создание и передача сертификата для Windows Azure](http://go.microsoft.com/fwlink/?LinkId=320781).  
  
 **Подписка**  
 Выберите, введите или вставьте идентификатор подписки Windows Azure, который соответствует сертификату управления из локального хранилища сертификатов.  
  
 **Профиль публикации**  
 Используйте этот параметр, если имеется профиль публикации, загруженный на компьютер. Если воспользоваться этим параметром, идентификатор подписки и сертификат будут заполнены автоматически.  
  
> [!CAUTION]  
>  SQL Server в настоящий момент поддерживает версию 2.0 профиля публикации. Для загрузки поддерживаемой версии профиля публикации см. раздел [Загрузка профиля публикации 2.0](http://go.microsoft.com/fwlink/?LinkId=396421).  
  
## <a name="storage-account"></a>Учетная запись хранения  
 Выберите учетную запись хранения, которую нужно использовать для хранения файлов резервных копий.  
  
  
