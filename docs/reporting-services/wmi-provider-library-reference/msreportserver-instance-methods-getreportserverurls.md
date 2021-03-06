---
title: Метод GetReportServerUrls (WMI MSReportServer_Instance) | Документы Майкрософт
ms.custom: ''
ms.date: 06/09/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 1cd4e616f22872f87d9df3fc9d624f5513e8b040
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33031361"
---
# <a name="msreportserverinstance-methods---getreportserverurls"></a>Методы MSReportServer_Instance — GetReportServerUrls
  Возвращает список URL-адресов, которые пользователи могут использовать для доступа к серверу отчетов и [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *ApplicationName[]*  
 Массив, который содержит установленные приложения. Значения: либо **ReportServerWebService** либо **ReportServerWebApp**.  
  
 *URLs[]*  
 Массив, который содержит успешно зарегистрированные URL-адреса.  
  
 *Длина*  
 Целое значение, представляющее длину возвращенных массивов.  
  
 *HRESULT*  
 Значение, показывающее успешное завершение или код ошибки.  
  
## <a name="return-values"></a>Возвращаемые значения  
  
## <a name="remarks"></a>Remarks  
 Методы, доступные в управляющих объектах WMI, вызываются с помощью функции InvokeMethod. Дополнительные сведения см. в разделе «Выполнение методов в управляющих объектах» документации по инструментарию WMI платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
