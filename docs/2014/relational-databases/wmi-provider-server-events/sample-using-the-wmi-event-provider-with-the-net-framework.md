---
title: 'Пример: Использование поставщика событий WMI с платформой .NET Framework | Документация Майкрософт'
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
- WMI Provider for Server Events, samples
- sample applications [WMI]
- managed code [WMI]
ms.assetid: 3d7aa7e9-0bb3-4a5b-9a3c-047f3240a6f8
caps.latest.revision: 13
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ec2511bd6f2e1f184dd2123750bcda02a50f59cc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193024"
---
# <a name="sample-using-the-wmi-event-provider-with-the-net-framework"></a>Пример: Использование поставщика событий WMI с платформой .NET Framework
  В следующем образце создается приложение на языке C#, которое использует поставщика событий WMI, чтобы возвратить данные событий для всех событий языка описания данных DDL, которые происходят на установочном экземпляре по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 Следующий пример компилируется с использованием следующего командного файла:  
  
```  
set compiler_path=C:\WINNT\Microsoft.NET\Framework\v2.0.50110  
  
%compiler_path%\csc %1  
```  
  
```  
using System;  
using System.Management;  
  
class SQLWEPExample   
{  
    public static void Main(string[] args)  
    {  
        string query =  @"SELECT * FROM DDL_EVENTS " ;  
        // Default namespace for default instance of SQL Server   
        string managementPath =  
            @"\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER";  
        ManagementEventWatcher  watcher =   
            new ManagementEventWatcher(new WqlEventQuery (query));  
        ManagementScope scope = new ManagementScope (managementPath);  
        scope.Connect();  
        watcher.Scope = scope;  
        Console.WriteLine("Watching...");  
        while (true)  
        {  
            ManagementBaseObject obj = watcher.WaitForNextEvent();  
            Console.WriteLine("Event!");  
            foreach (PropertyData data in obj.Properties)  
            {  
                Console.Write("{0}:", data.Name);  
                if (data.Value == null)  
                {  
                    Console.WriteLine("<null>");  
                }  
                else  
                {  
                    Console.WriteLine(data.Value.ToString());  
                }  
            }  
            Console.WriteLine("-----");  
            Console.WriteLine();  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Основные понятия о поставщике WMI для событий сервера](wmi-provider-for-server-events-concepts.md)  
  
  
