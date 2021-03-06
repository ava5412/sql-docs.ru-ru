---
title: RecordStatusEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordStatusEnum
helpviewer_keywords:
- RecordStatusEnum enumeration [ADO]
ms.assetid: 506fdd70-4452-4e83-95d5-c94311988dfa
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f61d0d948730cfb39cd2c0429eb53dcab311fe5
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281233"
---
# <a name="recordstatusenum"></a>RecordStatusEnum
Указывает [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) записи по отношению к пакетные обновления и других операций массового.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adRecCanceled**|0x100|Указывает, что запись не была сохранена, так как операция была отменена.|  
|**adRecCantRelease**|0x400|Указывает, новая запись не был сохранен, так как существующую запись была заблокирована.|  
|**adRecConcurrencyViolation**|0x800|Указывает, записи не был сохранен, поскольку использовалось оптимистичного параллелизма.|  
|**adRecDBDeleted**|0x40000|Указывает, что запись уже удалены из источника данных.|  
|**adRecDeleted**|0x4|Указывает, что запись была удалена.|  
|**adRecIntegrityViolation**|0x1000|Указывает, что запись не была сохранена, так как пользователь противоречит ограничениям целостности.|  
|**adRecInvalid**|0x10|Указывает, что запись не была сохранена, из-за недопустимого ее закладки.|  
|**adRecMaxChangesExceeded**|0x2000|Указывает, что запись не была сохранена, из-за наличия слишком много ожидающих изменений.|  
|**adRecModified**|0x2|Указывает, что запись была изменена.|  
|**adRecMultipleChanges**|0x40|Указывает, что запись не была сохранена, так как затрагивала несколько записей.|  
|**adRecNew**|0x1|Указывает, что запись является новой.|  
|**adRecObjectOpen**|0x4000|Указывает, что запись не была сохранена из-за конфликта с открытый объект хранилища.|  
|**adRecOK**|0|Указывает, что запись успешно обновлен.|  
|**adRecOutOfMemory**|0x8000|Указывает, что запись не была сохранена, так как серверу хватает памяти.|  
|**adRecPendingChanges**|0x80|Указывает, что запись не была сохранена, так как он ссылается на ожидается Вставка.|  
|**adRecPermissionDenied**|0x10000|Указывает, что запись не была сохранена, поскольку у пользователя недостаточно разрешений.|  
|**adRecSchemaViolation**|0x20000|Указывает, что запись не была сохранена, из-за нарушения структуры базы данных.|  
|**adRecUnmodified**|0x8|Указывает, что записи не были изменены.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 AdoEnums.RecordStatus.  
  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.RecordStatus.CANCELED|  
|AdoEnums.RecordStatus.CANTRELEASE|  
|AdoEnums.RecordStatus.CONCURRENCYVIOLATION|  
|AdoEnums.RecordStatus.DBDELETED|  
|AdoEnums.RecordStatus.DELETED|  
|AdoEnums.RecordStatus.INTEGRITYVIOLATION|  
|AdoEnums.RecordStatus.INVALID|  
|AdoEnums.RecordStatus.MAXCHANGESEXCEEDED|  
|AdoEnums.RecordStatus.MODIFIED|  
|AdoEnums.RecordStatus.MULTIPLECHANGES|  
|AdoEnums.RecordStatus.NEW|  
|AdoEnums.RecordStatus.OBJECTOPEN|  
|AdoEnums.RecordStatus.OK|  
|AdoEnums.RecordStatus.OUTOFMEMORY|  
|AdoEnums.RecordStatus.PENDINGCHANGES|  
|AdoEnums.RecordStatus.PERMISSIONDENIED|  
|AdoEnums.RecordStatus.SCHEMAVIOLATION|  
|AdoEnums.RecordStatus.UNMODIFIED|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Status (объект Recordset ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md)
