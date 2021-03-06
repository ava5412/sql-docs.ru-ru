---
title: Обработка исключений SMO | Документация Майкрософт
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
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2d8e121a9fdc76073a016041f102fa36e6685f72
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299844"
---
# <a name="handling-smo-exceptions"></a>Обработка исключений SMO
  В управляемом коде при возникновении ошибок вызываются исключения. Методы и свойства объектов SMO не сообщают об ошибке или успешном выполнении в возвращаемом значении. Исключения могут быть перехвачены и обработаны в обработчике исключений.  
  
 В объектах SMO существуют различные классы исключений. Сведения об исключении можно извлечь из свойств исключения, таких как свойство `Message`, которое предоставляет текстовое сообщение об исключении.  
  
 Инструкции обработки исключения зависят от конкретного языка программирования. Например, в языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic это инструкция `Catch`.  
  
## <a name="inner-exceptions"></a>Внутренние исключения  
 Исключения могут быть общими и конкретными. Общие исключения содержат набор конкретных исключений. Несколько `Catch` операторы могут использоваться, чтобы обработать ожидаемые ошибки и позволить остальным ошибкам пройти через обработку общих исключений. Исключения часто происходят в каскадной последовательности. Часто исключение объекта SMO может быть вызвано исключением SQL. Для обнаружения этого рекомендуется использовать `InnerException` последовательно, чтобы определить исходное исключение, которое вызвало конечное исключение верхнего уровня.  
  
> [!NOTE]  
>  `SQLException` Исключение объявлено в **System.Data.SqlClient** пространства имен.  
  
 ![Диаграмма, показывающая уровни, из которых могут вызываться исключения](../../../database-engine/dev-guide/media/exception-flow.gif "диаграмма, показывающая уровни, из которых могут вызываться исключения")  
  
 Диаграмма показывает поток исключений по уровням приложения.  
  
## <a name="example"></a>Пример  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) или [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md).  
  
## <a name="catching-an-exception-in-visual-basic"></a>Перехват исключения на языке Visual Basic  
 Данный пример кода показывает, как использовать `Try…Catch…Finally` [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] инструкции для перехвата исключения объекта SMO. Все исключения объектов SMO имеют тип SmoException и перечислены в справке по объектам SMO. Последовательность внутренних исключений отображается, чтобы показать основание ошибки. Дополнительные сведения см. в разделе [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] документация по .NET.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBExceptions1](SMO How to#SMO_VBExceptions1)]  -->  
  
## <a name="catching-an-exception-in-visual-c"></a>Перехват исключения на языке Visual C#  
 В этом примере кода показано, как использовать инструкцию `Try…Catch…Finally` в Visual C# для перехвата исключения объекта SMO. Все исключения объектов SMO имеют тип SmoException и перечислены в справке по объектам SMO. Последовательность внутренних исключений отображается, чтобы показать основание ошибки. Дополнительные сведения см. в документации по языку Visual C#.  
  
```  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
