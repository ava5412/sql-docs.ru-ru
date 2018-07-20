---
title: srv_paramname (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_paramname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8108cbf1c08f9259734280105df931dc3f91203a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37217274"
---
# <a name="srvparamname-extended-stored-procedure-api"></a>srv_paramname (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Возвращает имя параметра вызова удаленной хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, который получил вызов удаленной хранимой процедуры). Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *n*  
 Указывает номер параметра. Первый параметр имеет значение 1.  
  
 *len*  
 Содержит указатель на переменную `int`, которая содержит длину имени параметра в байтах. Если параметр *len* равен NULL, то длина имени параметра удаленной хранимой процедуры не возвращается.  
  
## <a name="returns"></a>Возвращает  
 Указатель на строку, заканчивающуюся нулевым символом, которая содержит имя параметра. Длина имени параметра хранится в *len*. Если параметра с номером *n* или удаленной хранимой процедуры не существует, то возвращается значение NULL, *len* получает значение -1 и отправляется информационное сообщение об ошибке. Если имя параметра равно NULL, для *len* устанавливается значение 0 и возвращается пустая строка, заканчивающаяся нулевым символом.  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает имя параметра вызова удаленной хранимой процедуры. Когда удаленная хранимая процедура вызывается с параметрами, эти параметры могут быть переданы либо по имени, либо по позиции — без указания имени. Если при вызове удаленной хранимой процедуры часть параметров передается по имени, а часть — по позиции, возникает ошибка. Обработчик SRV_RPC по-прежнему вызывается, однако он отображается так, как если бы не имел параметров, а функция **srv_rpcparams** возвращает 0.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также  
 [srv_rpcparams (интерфейс API расширенных хранимых процедур)](srv-rpcparams-extended-stored-procedure-api.md)  
  
  