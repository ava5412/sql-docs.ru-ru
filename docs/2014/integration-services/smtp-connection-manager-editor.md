---
title: Редактор диспетчера соединений SMTP | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
caps.latest.revision: 37
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c67233452d294a6bc0f6f106a59678827ef17b3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235214"
---
# <a name="smtp-connection-manager-editor"></a>редактор диспетчера SMTP-сеансов
  Используйте диалоговое окно **Редактор диспетчера SMTP-сеансов** для задания SMTP-сервера.  
  
 Дополнительные сведения о диспетчере SMTP-соединений см. в разделе [SMTP Connection Manager](connection-manager/smtp-connection-manager.md).  
  
## <a name="options"></a>Параметры  
 **Название**  
 Задает уникальное имя диспетчера соединений.  
  
 **Описание**  
 Задайте описание диспетчера соединений. Рекомендуется описать назначение диспетчера соединений, чтобы сделать пакеты самодокументируемыми и более простыми в использовании.  
  
 **SMTP-сервер**  
 Позволяет задать имя сервера SMTP.  
  
 **Использовать проверку подлинности Windows**  
 Выберите для отправки почты с помощью SMTP-сервера, который использует проверку подлинности Windows для доступа к серверу.  
  
> [!IMPORTANT]  
>  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
> [!NOTE]  
>  При использовании Microsoft Exchange в качестве SMTP-сервера, может потребоваться задать **использовать проверку подлинности Windows** для `True`. Серверы Exchange можно настроить так, чтобы они запрещали использовать соединения SMTP, не прошедшие проверку подлинности.  
  
 **Включить протокол SSL**  
 Выберите, чтобы отправляемые почтовые сообщения шифровались по протоколу SSL.  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
