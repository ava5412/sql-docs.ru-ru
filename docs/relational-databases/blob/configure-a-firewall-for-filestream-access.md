---
title: Настройка брандмауэра для доступа к FILESTREAM | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: filestream
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39e648a2535f069d3c17276c81bd32acae5e915b
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36915005"
---
# <a name="configure-a-firewall-for-filestream-access"></a>Настройка брандмауэра для доступа FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Чтобы использовать FILESTREAM в среде, защищенной брандмауэром, как клиент, так и сервер должны быть в состоянии разрешать имена DNS для сервера, содержащего файлы FILESTREAM. Для данных FILESTREAM требуется, чтобы были открыты порты 139 и 445 для общего доступа к файлам Windows.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>Открытие портов общего доступа к файлам Windows на компьютере под управлением Windows 7  
  
1.  На панели управления откройте элемент **Брандмауэр Windows**.  
  
2.  На левой панели нажмите кнопку **Дополнительные параметры**. Если появится запрос пароля администратора или подтверждения, введите пароль или подтверждение.  
  
3.  На левой панели окна **Брандмауэр Windows в режиме повышенной безопасности** щелкните раздел **Правила для входящих подключений**, затем на правой панели выберите пункт **Создать правило**.  
  
4.  Чтобы добавить TCP-порт 139, следуйте инструкциям мастера создания правила для нового входящего подключения.  
  
5.  Повторите предыдущий шаг для добавления TCP-порта 445.  
  
6.  Закройте диалоговое окно **Брандмауэр Windows в режиме повышенной безопасности** .  
  
  
