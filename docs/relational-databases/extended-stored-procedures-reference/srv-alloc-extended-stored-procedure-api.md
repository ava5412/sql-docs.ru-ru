---
title: srv_alloc (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_alloc
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b95185ccec1d1c7c3be112340d4894df097f2617
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32935057"
---
# <a name="srvalloc-extended-stored-procedure-api"></a>srv_alloc (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Динамически распределяет память.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *size*  
 Указывает число байтов для распределения.  
  
## <a name="returns"></a>Возвращает  
 Указатель на распределенную память. Если объем памяти, указываемый аргументом *size*, выделить не удалось, возвращается указатель NULL.  
  
## <a name="remarks"></a>Remarks  
 Функция **srv_alloc** является эквивалентом функции [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API **GlobalAlloc**. Обычные функции управления памятью библиотеки времени выполнения Windows API на языке C могут использоваться в приложении API-интерфейса расширенных хранимых процедур.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
