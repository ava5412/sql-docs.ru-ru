---
title: Метод SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SetVirtualDirectory method
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e1692ea69ca807924b55811110476f01333cd99d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33031631"
---
# <a name="configurationsetting-method---setvirtualdirectory"></a>Метод ConfigurationSetting — SetVirtualDirectory
  Задает имя виртуального каталога для указанного приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Параметры  
 *Приложение*  
 Имя приложения, для которого задается виртуальный каталог.  
  
 *VirtualDirectory*  
 Имя виртуального каталога.  
  
 *lcid*  
 Идентификатор локали для виртуального каталога.  
  
 *Ошибка*  
 [out] Описания возникших ошибок.  
  
 *HRESULT*  
 [out] Значение, которое указывает, окончился ли вызов успехом или сбоем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение *HRESULT* , являющееся признаком успешного или неуспешного завершение вызова метода. Значение 0 означает, что вызов метода завершился успешно; код ошибки означает, что произошла ошибка.  
  
## <a name="remarks"></a>Remarks  
 Для приложения можно задать только одно имя виртуального каталога для всех зарезервированных URL-адресов.  
  
 Параметр VirtualDirectory должен соответствовать контексту именования для виртуальных каталогов. Параметр VirtualDirectory не должен быть пустой строкой.  
  
 Обновляет значение элемента \Configuration\URLReservations\Application\VirtualDirectory. Выполняется успешно, даже еще не созданы зарезервированные URL-адреса.  
  
## <a name="requirements"></a>Требования  
 **Пространство имен:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Элементы MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
