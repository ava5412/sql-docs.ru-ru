---
title: Таблицы сбора (ADOX) | Документы Microsoft
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
- Catalog::Tables
- Tables
helpviewer_keywords:
- Tables collection [ADOX]
ms.assetid: 38d750e7-f3fb-426e-b4b4-55eea4f1a654
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6b97d189907d8f226867748e25e64972b8aba2b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35287213"
---
# <a name="tables-collection-adox"></a>Коллекция таблиц (ADOX)
Содержит все [таблицы](../../../ado/reference/adox-api/table-object-adox.md) объектов каталога.  
  
## <a name="remarks"></a>Примечания  
 [Append](../../../ado/reference/adox-api/append-method-adox-tables.md) метод **таблиц** является уникальным для ADOX. Возможные действия:  
  
-   Добавить новую таблицу в коллекцию с **Append** метод.  
  
 Остальные свойства и методы являются стандартными коллекциям ADO. Возможные действия:  
  
-   Доступ к таблице в коллекции с [элемент](../../../ado/reference/ado-api/item-property-ado.md) свойство.  
  
-   Возвращает количество таблиц, содержащихся в коллекции с [число](../../../ado/reference/ado-api/count-property-ado.md) свойство.  
  
-   Удалить таблицу из коллекции с помощью [удалить](../../../ado/reference/adox-api/delete-method-adox-collections.md) метод.  
  
-   Обновление объектов в коллекции в соответствии с текущей схемы базы данных с [обновление](../../../ado/reference/ado-api/refresh-method-ado.md) метод.  
  
 Некоторые поставщики могут возвращать другие объекты схемы, например, представление в **таблиц** коллекции. Таким образом некоторые ADOX коллекции может содержать несколько ссылок на тот же объект. Следует ли удалить объект из одной коллекции, изменения не будут отображаться в другой коллекции, который ссылается на удаленный объект, пока не **обновление** метод вызывается для коллекции. Например, с помощью поставщика OLE DB для Microsoft Jet, представления с возвращаются **таблиц** коллекции. При удалении представления, необходимо обновить **таблиц** коллекции, прежде чем изменения будут отражены коллекции.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Tables](../../../ado/reference/adox-api/tables-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства ActiveConnection каталога (Visual Basic)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Столбцы и таблицы добавьте методы примера имя свойства (Visual Basic)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Подключение метода закрытия, пример свойство типа таблицы (Visual Basic)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Ключи добавить метод, тип ключа, RelatedColumn, RelatedTable и UpdateRule-пример свойства (Visual Basic)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)
