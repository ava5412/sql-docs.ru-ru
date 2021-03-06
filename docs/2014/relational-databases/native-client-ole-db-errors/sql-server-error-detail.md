---
title: Сведения об ошибке SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b937fda454ae08549917cdf3682ef20c76373a6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408993"
---
# <a name="sql-server-error-detail"></a>Подробные сведения об ошибках SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента определяет интерфейс поставщика ошибка [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md). Интерфейс возвращает более подробные сведения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и полезен, если выполнение команды или операции работы с наборами строк завершились с ошибкой.  
  
 Существует два способа получить доступ к **ISQLServerErrorInfo** интерфейс.  
  
 Потребитель может вызвать **IErrorRecords::GetCustomerErrorObject** для получения **ISQLServerErrorInfo** указателя, как показано в следующем образце кода. (Нет необходимости для получения **ISQLErrorInfo.**) Оба **ISQLErrorInfo** и **ISQLServerErrorInfo** являются пользовательские объекты ошибок OLE DB, с помощью **ISQLServerErrorInfo** является интерфейсом для получения сведений из ошибки на сервере, включая такие данные, как процедура имени и номера строк.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Еще один способ получения **ISQLServerErrorInfo** указатель является вызов **QueryInterface** метод уже получал **ISQLErrorInfo** указатель. Обратите внимание, что поскольку **ISQLServerErrorInfo** содержит надмножество информации, доступной из **ISQLErrorInfo**, имеет смысл перейти непосредственно на **ISQLServerErrorInfo**через **GetCustomerErrorObject**.  
  
 **ISQLServerErrorInfo** интерфейс предоставляет одну функцию-член [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). Функция возвращает указатель на структуру SSERRORINFO и указатель на буфер строк. Оба указателя ссылаются на память, потребитель должен освободить с помощью **IMalloc::Free** метод.  
  
 Элементы структуры SSERRORINFO обрабатываются потребителем следующим образом.  
  
|Член|Описание|  
|------------|-----------------|  
|*pwszMessage*|Сообщение об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Идентично строке, возвращаемой **IErrorInfo::GetDescription**.|  
|*pwszServer*|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для сеанса.|  
|*pwszProcedure*|При необходимости, имя процедуры, в которой произошла ошибка. Пустая строка в противном случае.|  
|*lNative*|Номер собственной ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Идентичен значению, возвращенному в *plNativeError* параметр **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|Состояние сообщения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Серьезность сообщения об ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Если применимо, номер строки хранимой процедуры, в которой возникла ошибка.|  
  
## <a name="see-also"></a>См. также  
 [Ошибки](errors.md)   
 [RAISERROR (Transact-SQL)](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
