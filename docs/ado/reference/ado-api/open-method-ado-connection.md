---
title: Open-метод (соединение ADO) | Документы Microsoft
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
- Connection15::raw_Open
- Connection15::Open
- _Connection::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 663defab-5545-4973-9036-24d5882c9737
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8035a40949e269fd8d8b039eb1931e8ed17c73c7
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280013"
---
# <a name="open-method-ado-connection"></a>Метод Open (соединение ADO)
Открывает подключение к источнику данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>Параметры  
 *connectionString*  
 Необязательный параметр. Объект **строка** значение, содержащее сведения о соединении. В разделе [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство сведения о допустимых значений.  
  
 *Идентификатор пользователя*  
 Необязательный параметр. Объект **строка** значение, содержащее имя пользователя для использования при установке соединения.  
  
 *Пароль*  
 Необязательный параметр. Объект **строка** значение, содержащее пароль для использования при установке соединения.  
  
 *Параметры*  
 Необязательный параметр. Объект [ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md) значение, определяющее, является ли этот метод должен возвращать после (синхронно) или до (асинхронно) подключения.  
  
## <a name="remarks"></a>Примечания  
 С помощью **откройте** метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объект устанавливает физическое соединение с источником данных. После успешного завершения этого метода, подключение считается активным и может отдавать команды ее и обрабатывать результаты.  
  
 Дополнительно *ConnectionString* аргумент, чтобы указать строку соединения, содержащий ряд *аргумент* *= значение* инструкций, разделенных точкой с запятой, или файл или каталог ресурс, указанный в URL-адресе. **ConnectionString** свойство автоматически наследует значение, используемое для *ConnectionString* аргумент. Таким образом, можно либо установить **ConnectionString** свойство **подключения** объекта перед его открытием или использовать *ConnectionString* аргумент, чтобы задать или переопределить параметры текущего подключения во время **откройте** вызова метода.  
  
 Если передать имя пользователя и пароль сведения обоих в *ConnectionString* аргумент и в необязательном *UserID* и *пароль* аргументы, *UserID*  и *пароль* аргументы переопределяют значения, заданные в *ConnectionString*.  
  
 После завершения операции через открытый **подключения**, используйте [закрыть](../../../ado/reference/ado-api/close-method-ado.md) метод, чтобы освободить все связанные с ним ресурсы системы. Закрывает объект не удаляется из памяти; можно изменить настройки его свойств и использовать **откройте** метод, чтобы открыть его позже. Для полного устранения объекта из памяти, присвойте переменной объекта *ничего не*.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **подключения** объекта, **откройте** метод фактически не установить подключение к серверу до [набора записей ](../../../ado/reference/ado-api/recordset-object-ado.md) открывается на **подключения** объекта.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Открытие и закрытие примере методы (Visual Basic)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Пример методов открытия и закрытия (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Пример методов открытия и закрытия (VC ++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Метод Open (ADO запись)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Метод OpenSchema](../../../ado/reference/ado-api/openschema-method.md)
