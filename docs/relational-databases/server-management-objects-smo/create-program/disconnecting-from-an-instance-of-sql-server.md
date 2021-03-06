---
title: Отсоединение от экземпляра сервера SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: fffcb2d7d9ef6f9d8b0f3e13717985f7a8032047
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555444"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Отсоединение от экземпляра SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Вручную закрытие и отсоединение [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] объектов управляющих объектов (SMO) не является обязательным. Соединения открываются и закрываются по мере необходимости.  
  
## <a name="connection-pooling"></a>Организация пулов соединений  
 Когда [Connect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.connect) вызывается метод, соединение не освобождается автоматически. [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) метод должен вызываться явным образом, чтобы освободить соединение обратно в пул подключений. Можно также запросить соединение вне пула. Это можно сделать, задав [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойство, ссылающееся на [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) объекта.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Отсоединение от экземпляра SQL Server для объектов RMO  
 При программировании с использованием объектов RMO закрытие серверных соединений немного отличается от закрытия при использовании объектов SMO.  
  
 Так как соединение с сервером для объекта RMO обслуживается [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) объекта, этот объект также используется при отсоединении от экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при программировании с помощью объектов RMO. Закрыть подключение с помощью [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) , вызовите [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) метод объекта RMO. После закрытия соединения объекты RMO использовать нельзя.  
  
## <a name="example"></a>Пример  
Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Закрытие и отсоединение объекта SMO на языке Visual Basic  
 Данный пример кода показано, как запросить соединение вне пула, задав [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойство объекта.  
  
```VBNET
Dim srv As Server
srv = New Server
'Disable automatic disconnection.
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect
'Connect to the local, default instance of SQL Server.
srv.ConnectionContext.Connect()
'The actual connection is made when a property is retrieved.
Console.WriteLine(srv.Information.Version)
'Disconnect explicitly.
srv.ConnectionContext.Disconnect()
```
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Закрытие и отсоединение объекта SMO на языке Visual C#  
 Данный пример кода показано, как запросить соединение вне пула, задав [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> свойство объекта.  
  
```csharp  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)  
  
  
