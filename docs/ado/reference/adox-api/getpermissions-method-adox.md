---
title: "Метод GetPermissions (ADOX) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _User25::GetPermissions
- _Group25::raw_GetPermissions
- _Group25::GetPermissions
- _User25::raw_GetPermissions
helpviewer_keywords:
- GetPermissions method [ADOX]
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 542abb8ab3c8fb5857508b4fafb6f50412c825bb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getpermissions-method-adox"></a>Метод GetPermissions (ADOX)
Возвращает разрешения для [группы](../../../ado/reference/adox-api/group-object-adox.md) или [пользователя](../../../ado/reference/adox-api/user-object-adox.md) на объект или объект контейнера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **длинные** значение, которое задает битовую маску, содержащие разрешения, которые группа или пользователь имеет для этого объекта. Это значение может быть один или несколько [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) константы.  
  
#### <a name="parameters"></a>Параметры  
 *Название*  
 Объект **Variant** значение, указывающее имя объекта, для которого требуется задать разрешения. Задать *имя* со значением null, если вы хотите получить разрешения для контейнера объекта.  
  
 *ObjectType*  
 Объект **длинные** значение может быть одним из [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) константы, которое указывает тип объекта, для которого необходимо получить разрешения.  
  
 *ObjectTypeId*  
 Необязательно. Объект **Variant** значение, которое не указывает идентификатор GUID для типа поставщика объектов, определенных в спецификации OLE DB. Этот параметр является обязательным, если *ObjectType* равно **adPermObjProviderSpecific**; в противном случае он не используется.  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Объект группы (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Объект пользователя (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>См. также:  
 [GetPermissions и пример SetPermissions методы (Visual Basic)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Свойство Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [Метод SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)