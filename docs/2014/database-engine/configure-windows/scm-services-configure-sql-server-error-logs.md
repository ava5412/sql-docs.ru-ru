---
title: Настройка журналов ошибок SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 37f20171007715cc4be89feeb1dcbef34ba797ef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189131"
---
# <a name="configure-sql-server-error-logs"></a>Настройка журналов ошибок SQL Server
  В этом разделе описано, как просмотреть и изменить способ очистки журналов ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Открытие диалогового окна «Настройка журналов ошибок SQL Server»  
  
1.  В обозревателе объектов разверните экземпляр SQL Server, раскройте узел **Управление**, щелкните правой кнопкой мыши **Журналы SQL Server**, а затем выберите пункт **Настройка**.  
  
2.  В диалоговом окне **Настройка журналов ошибок SQL Server** выберите один из следующих параметров.  
  
     **Ограничить количество файлов журнала ошибок перед очисткой**  
     Установите этот флажок, чтобы ограничить количество файлов журнала ошибок, создаваемых до их очистки. При каждом запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создается новый журнал ошибок. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет резервные копии шести предыдущих журналов, если этот флажок не установлен и ниже не указано иное максимальное число файлов журнала ошибок.  
  
     **Максимальное количество файлов журналов ошибок**  
     Укажите максимальное количество файлов журнала ошибок, создаваемых до их очистки. Значение по умолчанию — 6, то есть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет шесть предыдущих резервных копий журналов до их очистки.  
  
  
