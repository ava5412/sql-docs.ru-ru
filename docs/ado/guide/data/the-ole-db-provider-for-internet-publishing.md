---
title: Поставщик OLE DB для публикации в Интернете | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
ms.assetid: 4869aafa-7401-4ce1-93ce-45406a60274f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee7efbcd02903e8bba38ecfa177ed7e095e0f5e9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273033"
---
# <a name="the-ole-db-provider-for-internet-publishing"></a>Поставщик OLE DB для публикации в Интернете
ADO [запись](../../../ado/reference/ado-api/record-object-ado.md) и [поток](../../../ado/reference/ado-api/stream-object-ado.md) объекты могут использоваться поставщик Microsoft OLE DB для публикаций в Интернете (Интернет поставщика публикаций) для доступа и управления ресурсами, такими как веб-папки или файлы обслуживаемых Microsoft FrontPage. При использовании ADO, можно указать источник **записи**, **поток**, или [записей](../../../ado/reference/ado-api/recordset-object-ado.md) быть URL-адрес. Вы может затем отправить, загрузки, перемещения, копирования и удаление ресурсов или напрямую манипулировать свойства ресурса.  
  
 Пример кода, который использует **записей** и **потоки** публикации поставщика Интернета, в разделе [сценария публикации Интернет](../../../ado/guide/data/internet-publishing-scenario.md).  
  
 Службу публикации в Интернете устанавливается вместе с Microsoft Windows 2000. Также доступны более ранних версиях службу публикации в Интернете с Microsoft Office 2000 и Microsoft Internet Explorer 5.0.  
  
 Для подключения ADO службу публикации в Интернете тремя способами:  
  
-   Укажите «URL-адрес =» в строке подключения. Например:  
  
    ```  
    objConn.Open "URL=http://servername"  
    ```  
  
-   Укажите Msdaipp.dso для *поставщика* ключевое слово строки подключения. Например:  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=http://servername"  
    ```  
  
-   Укажите Msdaipp.dso для [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Например:  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "http://servername"  
    ```  
  
> [!NOTE]
>  Если Msdaipp.dso явно указано в качестве значения поставщика, с помощью *поставщика* ключевое слово строки подключения или **поставщика** свойство, нельзя использовать «URL-адрес =» в строке подключения. В противном случае возникнет ошибка. Вместо этого просто укажите URL-адрес, как показано выше.  
  
 Более конкретные сведения о службу публикации в Интернете в разделе [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), или поставщик документации, поставляемой с исходным приложением с помощью которого поставщик OLE DB для Был установлен публикаций в Интернете: Windows 2000, Microsoft Office 2000 или Internet Explorer 5.0.
