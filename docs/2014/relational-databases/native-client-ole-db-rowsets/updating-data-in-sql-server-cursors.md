---
title: Обновление данных в курсорах SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caa3f5d35d51a90809175da88c9732fd883d291d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428333"
---
# <a name="updating-data-in-sql-server-cursors"></a>Обновление данных в курсорах SQL Server
  При выборке и обновлении данных через [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] курсоров, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложение-потребитель поставщика OLE DB для собственного клиента ограничивается те же рекомендации и ограничения, применяемые для любого другого клиентского приложения.  
  
 В управлении параллельным доступом к данным участвуют только строки курсоров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Когда потребитель запрашивает изменяемый набор строк, управление параллелизмом осуществляется свойством DBPROP_LOCKMODE. Чтобы изменить уровень управления параллельным доступом, потребитель устанавливает свойство DBPROP_LOCKMODE до того, как открывает набор строк.  
  
 Уровни изоляции транзакции могут вызвать значительные задержки при позиционировании строк, если клиентское приложение оставляет транзакции долгое время открытыми. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB для собственного клиента использует уровень изоляции read committed, определяемое DBPROPVAL_TI_READCOMMITTED. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента поддерживает "грязных" изоляции read, если параллелизм набора строк только для чтения. Поэтому потребитель может запросить более высокий уровень изоляции в изменяемом наборе строк, но не может успешно запросить более низкий уровень.  
  
## <a name="immediate-and-delayed-update-modes"></a>Режимы немедленного и отложенного обновления  
 В режиме немедленного обновления, при каждом вызове **IRowsetChange::SetData** приводит к обмену данными с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если потребитель выполняет несколько изменений в одну строку, это более эффективно, чтобы отправить все изменения в одном **SetData** вызова.  
  
 В режиме отложенного обновления круговое обращение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для каждой строки, указанной в *cRows* и *rghRows* параметры **IRowsetUpdate::Update**.  
  
 В каждом режиме обмен данными представляет отдельную транзакцию, если для набора строк отсутствует открытый объект транзакции.  
  
 При использовании **IRowsetUpdate::Update**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента пытается обработать каждую указанную строку. Ошибка, происходящая из-за недопустимых значений данных, длину или состояния для любой строки не останавливает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обработки поставщика OLE DB для собственного клиента. Можно изменить все строки, участвующие в обновлении, или ни одной. Потребитель должен изучить возращенный *prgRowStatus* массива, чтобы определить ошибку для каждой конкретной строки, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение DB_S_ERRORSOCCURRED, поставщик OLE DB для собственного клиента.  
  
 Потребитель не должен предполагать, что строки обрабатываются в каком-то определенном порядке. Если потребителю требуется упорядоченная обработка данных нескольких строк, он должен установить этот порядок в логике приложения и открыть транзакцию, содержащую процесс упорядочивания.  
  
## <a name="see-also"></a>См. также  
 [Обновление данных в наборах строк](updating-data-in-rowsets.md)  
  
  
