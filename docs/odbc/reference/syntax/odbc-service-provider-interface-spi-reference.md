---
title: Справочник по интерфейсу (SPI) поставщик службы ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c909e38e1aa4ee78412c7025cb6ed53254e98d0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-service-provider-interface-spi-reference"></a>Справочник по интерфейсу (SPI) поставщик службы ODBC
В большинстве случаев ODBC определен интерфейс программирования (API). Можно вызывать функции в API приложениями и они должны быть реализованы в диспетчер драйверов и драйвер.  
  
 При добавлении функция объединения соединений с учетом драйвера ODBC появился интерфейс поставщика службы (SPI). Функции в SPI используются для взаимодействия между диспетчером драйверов и драйверов. Функции SPI реализуются с помощью драйвера; Диспетчер драйверов не предоставляет функции SPI для приложения. Приложения не должны напрямую вызывать эти функции.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
 В этом разделе рассматриваются следующие вопросы  
  
-   [SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Разработка драйвера ODBC, поддерживающие пула соединений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Организация пулов соединений диспетчера драйверов](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
