---
title: Создание, изменение и удаление схем | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schemas [SMO]
ms.assetid: 3e3619de-c6a2-4280-b2be-4ec9924608fb
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7bfbd8aa8265fd0cdc4615cb8a5ed2065e559138
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290350"
---
# <a name="creating-altering-and-removing-schemas"></a>Создание, изменение и удаление схем
  Объект <xref:Microsoft.SqlServer.Management.Smo.Schema> представляет контекст владения для объекта базы данных. Свойство <xref:Microsoft.SqlServer.Management.Smo.Database.Schemas%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Database> представляет коллекцию объектов <xref:Microsoft.SqlServer.Management.Smo.Schema>.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-schema-in-visual-basic"></a>Создание, изменение и удаление схемы на языке Visual Basic  
 Данный пример кода демонстрирует, как создавать схему и назначать ее объекту базы данных. Затем программа предоставляет пользователю разрешение и создает новую таблицу в схеме.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBSchemas1](SMO How to#SMO_VBSchemas1)]  -->  
  
## <a name="creating-altering-and-removing-a-schema-in-visual-c"></a>Создание, изменение и удаление схемы на языке Visual C#  
 Данный пример кода демонстрирует, как создавать схему и назначать ее объекту базы данных. Затем программа предоставляет пользователю разрешение и создает новую таблицу в схеме.  
  
```  
{  
         //Connect to the local, default instance of SQL Server.   
         Server srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db = srv.Databases["AdventureWorks2012"];   
        //Define a Schema object variable by supplying the parent database and name arguments in the constructor.   
        Schema sch = new Schema(db, "MySchema1");   
        sch.Owner = "dbo";   
  
        //Create the schema on the instance of SQL Server.   
        sch.Create();   
  
        //Define an ObjectPermissionSet that contains the Update and Select object permissions.   
        ObjectPermissionSet obperset = new ObjectPermissionSet();   
        obperset.Add(ObjectPermission.Select);   
        obperset.Add(ObjectPermission.Update);   
  
        //Grant the set of permissions on the schema to the guest account.   
        sch.Grant(obperset, "guest");   
  
        //Define a Table object variable by supplying the parent database, name and schema arguments in the constructor.   
        Table tb = new Table(db, "MyTable", "MySchema1");   
       Column mycol = new Column(tb, "Date", DataType.DateTime);   
        tb.Columns.Add(mycol);   
        tb.Create();   
  
        //Modify the owner of the schema and run the Alter method to make the change on the instance of SQL Server.   
        sch.Owner = "guest";   
        sch.Alter();   
  
        //Run the Drop method for the table and the schema to remove them.   
        tb.Drop();   
        sch.Drop();   
}  
```  
  
## <a name="creating-altering-and-removing-a-schema-in-powershell"></a>Создание, изменение и удаление схемы в PowerShell  
 Данный пример кода демонстрирует, как создавать схему и назначать ее объекту базы данных. Затем программа предоставляет пользователю разрешение и создает новую таблицу в схеме.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a schema object variable by supplying the parent database and name arguments in the constructor.   
$sch  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Schema `  
-argumentlist $db, "MySchema1"  
  
# Set schema owner  
$sch.Owner = "dbo"   
  
# Create the schema on the instance of SQL Server.   
$sch.Create()  
  
# Define an ObjectPermissionSet that contains the Update and Select object permissions.   
$obperset  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.ObjectPermissionSet  
$obperset.Add([Microsoft.SqlServer.Management.SMO.ObjectPermission]::Select)  
$obperset.Add([Microsoft.SqlServer.Management.SMO.ObjectPermission]::Update)  
  
# Grant the set of permissions on the schema to the guest account.   
$sch.Grant($obperset, "guest")  
  
#Create a SMO Table with one column and add it to the database  
$tb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Table -argumentlist $db, "MyTable", "MySchema1"  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$mycol =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Date", $Type  
$tb.Columns.Add($mycol)  
$tb.Create()   
  
# Modify the owner of the schema and run the Alter method to make the change on the instance of SQL Server.   
$sch.Owner = "guest"  
$sch.Alter()  
  
# Run the Drop method for the table and the schema to remove them.   
$tb.Drop()  
$sch.Drop()  
```  
  
  