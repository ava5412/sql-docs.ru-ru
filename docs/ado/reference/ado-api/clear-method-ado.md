---
title: Clear-метод (ADO) | Документы Microsoft
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
- Errors::raw_Clear
- Errors::Clear
helpviewer_keywords:
- Clear method [ADO]
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4f02311140a82d869f38d3b64f025a69357c5d2
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276343"
---
# <a name="clear-method-ado"></a>Метод Clear (ADO)
Удаляет все [ошибка](../../../ado/reference/ado-api/error-object.md) объектов из [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Errors.Clear  
```  
  
## <a name="remarks"></a>Примечания  
 Используйте **снимите** метод [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции, чтобы удалить все существующие [ошибка](../../../ado/reference/ado-api/error-object.md) объекты из коллекции. При возникновении ошибки ADO автоматически очищает **ошибки** коллекцию и заполняет его с **ошибка** объекты, основанные на новую ошибку.  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются в виде **ошибка** объекты в **ошибки** коллекции, но не остановить выполнение программы. Перед вызовом метода [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта; [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) задана объекта; или [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство **записей** , вызовите **снимите**метод **ошибки** коллекции. Таким образом, можно прочитать [число](../../../ado/reference/ado-api/count-property-ado.md) свойство **ошибки** коллекцию для проверки возникли предупреждения.  
  
## <a name="applies-to"></a>Объект применения  
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Выполнение и Requery снимите примере методы (Visual Basic)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Выполнение и Requery снимите примере методы (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Выполнение и Requery снимите примере методы (VC ++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод Delete (ADO поля коллекции)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Удаление метода (коллекция параметров ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Удаление метода (набора записей ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [Свойства фильтра](../../../ado/reference/ado-api/filter-property.md)   
 [Метод повторной синхронизации](../../../ado/reference/ado-api/resync-method.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
