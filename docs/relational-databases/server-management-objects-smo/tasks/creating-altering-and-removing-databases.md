---
title: "Создание, изменение и удаление баз данных | Документы Microsoft"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- databases [SMO]
- databases [SMO], creating
- databases [SMO], modifying
- databases [SMO], deleting
ms.assetid: fcfb3ec2-7556-4f72-971a-501295892cb0
caps.latest.revision: "41"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e195aeb11109743b5ff17748e16b17ba3790694e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="creating-altering-and-removing-databases"></a>Создание, изменение и удаление баз данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В SMO база данных представлена <xref:Microsoft.SqlServer.Management.Smo.Database> объекта.  
  
 Чтобы изменить или удалить ее, необязательно создавать объект <xref:Microsoft.SqlServer.Management.Smo.Database>. На базу данных можно сослаться с помощью коллекции.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Create Visual C# 35; Проект SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-database-in-visual-basic"></a>Создание, изменение и удаление базы данных на языке Visual Basic  
 В этом примере кода создается новая база данных. Для этой базы данных автоматически создаются файлы и файловые группы.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define a Database object variable by supplying the server and the database name arguments in the constructor.
Dim db As Database
db = New Database(srv, "Test_SMO_Database")
'Create the database on the instance of SQL Server.
db.Create()
'Reference the database and display the date when it was created.
db = srv.Databases("Test_SMO_Database")
Console.WriteLine(db.CreateDate)
'Remove the database.
db.Drop()
```
  
## <a name="creating-altering-and-removing-a-database-in-visual-c"></a>Создание, изменение и удаление базы данных на языке Visual C#  
 В этом примере кода создается новая база данных. Для этой базы данных автоматически создаются файлы и файловые группы.  
  
```csharp  
{  
                //Connect to the local, default instance of SQL Server.   
                Server srv;  
                srv = new Server();  
                //Define a Database object variable by supplying the server and the database name arguments in the constructor.   
                Database db;  
                db = new Database(srv, "Test_SMO_Database");  
                //Create the database on the instance of SQL Server.   
                db.Create();  
                //Reference the database and display the date when it was created.   
                db = srv.Databases["Test_SMO_Database"];  
                Console.WriteLine(db.CreateDate);  
                //Remove the database.   
                db.Drop();  
            }  
```  
  
## <a name="creating-altering-and-removing-a-database-in-powershell"></a>Создание, изменение и удаление баз данных в PowerShell  
 В этом примере кода создается новая база данных. Для этой базы данных автоматически создаются файлы и файловые группы.  
  
```powershell  
#Get a server object which corresponds to the default instance  
cd \sql\localhost\  
$srv = get-item default  
  
#Create a new database  
$db = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Database -argumentlist $srv, "Test_SMO_Database"  
$db.Create()  
  
#Reference the database and display the date when it was created.   
$db = $srv.Databases["Test_SMO_Database"]  
$db.CreateDate  
  
#Drop the database  
$db.Drop()  
```  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.SqlServer.Management.Smo.Database>  
  
  