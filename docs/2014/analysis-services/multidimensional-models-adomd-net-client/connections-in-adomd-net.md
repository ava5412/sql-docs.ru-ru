---
title: Установление соединений в ADOMD.NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- opening connections
- closing connections
- connections [ADOMD.NET]
- ADOMD.NET, connections
ms.assetid: 7b9610f5-6641-42cc-af4e-bd35771913d1
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d7bf4529df77545cf2d0acf69af5d0b570ef750
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165305"
---
# <a name="establishing-connections-in-adomdnet"></a>Установление соединений в ADOMD.NET
  В ADOMD.NET, используется <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> объекта для открытия соединений с источниками аналитических данных, таких как [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] баз данных. Если необходимости в соединении больше нет, его следует явно закрыть.  
  
## <a name="opening-a-connection"></a>Открытие соединения  
 Чтобы открыть соединение в ADOMD.NET, необходимо сначала задать строку соединения с допустимым источником аналитических данных и базой данных. Затем следует явно открыть соединение с этим источником данных.  
  
### <a name="specifying-a-multidimensional-data-source"></a>Указание многомерного источника данных  
 Чтобы указать источник аналитических данных и базу данных, задается свойство <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Строка соединения, задаваемая для свойства <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>, является совместимой с OLE DB. При помощи указанной строки соединения компонент ADOMD.NET определяет, как подключаться к серверу.  
  
 Свойство <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> можно задать либо в существующем объекте <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, либо при создании экземпляра объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. В следующем коде показано, как задать свойство <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> при создании соединения ADOMD:  
  
```vb  
Dim advwrksConnection As New AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS")  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString)  
```  
  
```csharp  
AdomdConnection advwrksConnection = new AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS");  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString);  
```  
  
### <a name="opening-a-connection-to-the-data-source"></a>Открытие соединения с источником данных  
 Задав строку соединения, следует открыть соединение при помощи метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A>. При открытии объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> для соединения можно задать различные уровни безопасности. Используемый уровень безопасности соединения зависит от значения параметра строки соединения `ProtectionLevel`. Дополнительные сведения об открытии безопасных соединений в ADOMD.NET см. в разделе [установления безопасных соединений в ADOMD.NET](connections-in-adomd-net-establishing-secure-connections.md).  
  
## <a name="working-with-a-connection"></a>Работа с соединением  
 Каждое открытое соединение существует в рамках сеанса, который поддерживает операции с сохранением состояния. Сеанс может совместно использоваться несколькими открытыми соединениями. Совместное использование сеанса позволяет нескольким клиентам пользоваться одним контекстом. Дополнительные сведения см. в разделе [работа с соединениями и сеансами в ADOMD.NET](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
 Открытое соединение можно использовать для получения метаданных, данных и выполнения команд. Дополнительные сведения см. в разделе [получение метаданных из источника аналитических данных](retrieving-metadata-from-an-analytical-data-source.md), [извлечение данных из источника аналитических данных](retrieving-data-from-an-analytical-data-source.md), и [выполнение команды от аналитических данных Источник](executing-commands-against-an-analytical-data-source.md).  
  
 Когда соединение открыто, можно получать данные, метаданные и выполнять команды из транзакции READ-COMMITTED, в которой во время чтения данных устанавливаются совмещаемые блокировки для предотвращения чтения «грязных» данных. Данные по-прежнему можно изменять до окончания транзакции, что вызывает чтение без возможности повторения или фантомные данные. Дополнительные сведения см. в разделе [выполнение транзакций в ADOMD.NET](../../relational-databases/native-client-ole-db-transactions/transactions.md).  
  
## <a name="closing-a-connection"></a>Закрытие соединения  
 Рекомендуется явно закрывать объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, как только необходимость в соединении отпадает. Чтобы явно закрыть соединение, используются методы `Close` и `Dispose` объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Соединение, которое не закрывается явно, а само выходит из области действия, может достаточно долго не освобождать ресурсы сервера, что не позволяет клиентским приложениям служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с высокой степенью параллелизма эффективно открывать новые соединения. В зависимости от того, как было создано соединение, сеанс, используемый объектом <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, может остаться активным, если соединение не было явно закрыто.  
  
 Дополнительные сведения о сеансах см. в разделе [работа с соединениями и сеансами в ADOMD.NET](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md).  
  
> [!IMPORTANT]  
>  В методе `Finalize` любого реализованного класса не следует вызывать методы `Close` или `Dispose` объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>, объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> или любого другого управляемого объекта. В методе завершения следует освобождать только неуправляемые ресурсы, которыми непосредственно владеет реализованный класс. Если реализованный класс не владеет какими-либо неуправляемыми ресурсами, не включайте в его определение метод `Finalize`.  
  
## <a name="see-also"></a>См. также  
 [Программирование клиента ADOMD.NET](adomd-net-client-programming.md)  
  
  
