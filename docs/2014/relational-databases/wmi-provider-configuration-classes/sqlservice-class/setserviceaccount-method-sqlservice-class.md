---
title: Метод SetServiceAccount (класс SqlService) | Документация Майкрософт
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
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
caps.latest.revision: 36
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7186220ae32ceb8faa3fd5bdd906712d844d88e1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317944"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>Метод SetServiceAccount (класс SqlService)
  Пытается изменить имя пользователя и пароль, с которыми выполняется экземпляр службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
#### <a name="parameters"></a>Параметры  
 *ServiceStartName*  
 Строковое значение, указывающее имя учетной записи, под которым выполняется служба. В зависимости от типа службы имя учетной записи может иметь формат ИмяДомена\ИмяПользователя. При запуске процесс службы входит в систему, используя один из следующих двух форматов:  
  
-   если учетная запись принадлежит встроенному домену, можно указать \ИмяПользователя;  
  
-   Если задано значение NULL, служба входит в систему как **LocalSystem** учетной записи.  
  
 Для ядра или драйверов системного уровня *StartName* содержит имя объекта драйвера \FileSystem\Rdr или \Driver\Xns, которое система ввода-вывода использует для загрузки драйвера устройства. Если задано значение NULL, драйвер выполняется с именем объекта «значение по умолчанию», созданным системой ввода-вывода на основе имени службы, например DWDOM\Admin.  
  
 *ServiceStartPassword*  
 Строковое значение, указывающее пароль для имени учетной записи в *StartName* параметра. Если пароль не меняется, указывается значение NULL. Если служба не имеет пароля, указывается пустая строка.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  