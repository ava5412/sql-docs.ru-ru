---
title: Использование режима PATH для FOR XML | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode
- characters [SQL Server], XML
- aliases [SQL Server], XML
- FOR XML clause, PATH mode
- FOR XML PATH mode
- column names [SQL Server]
- XPath queries [SQL Server]
ms.assetid: a685a9ad-3d28-4596-aa72-119202df3976
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52a6570436741e0c1b556a578d71dc304307ad34
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33014371"
---
# <a name="use-path-mode-with-for-xml"></a>Использование режима PATH совместно с FOR XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Как описано в разделе [Создание XML с помощью предложения FOR XML](../../relational-databases/xml/for-xml-sql-server.md), режим PATH является простым способом смешивания элементов и атрибутов. Режим PATH является также простым способом создания дополнительных вложенных объектов для отражения сложных свойств. Для построения таких XML-документов из набора строк можно использовать запросы FOR XML в режиме EXPLICIT, но режим PATH является более простой альтернативой зачастую громоздким запросам в режиме EXPLICIT. Режим PATH дополнительно к возможности записи вложенных запросов FOR XML и возвращения экземпляров типа **xml** с помощью директивы TYPE позволяет писать менее сложные запросы.  
  
 В режиме PATH имена или псевдонимы столбцов обрабатываются как выражения XPath. Эти выражения показывают, как значения сопоставляются с XML-данными. Каждое выражение на языке XPath является относительным элементом XPath, предоставляющим такие сведения, как атрибут, элемент, скалярное значение, а также имя и иерархию узла, который будет сформирован в связи с элементом строки.  
  
 В этом разделе описано сопоставление столбцов в наборе строк в различных условиях и представлены соответствующие примеры.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Столбцы без имени](../../relational-databases/xml/columns-without-a-name.md)  
  
-   [Столбцы с именем](../../relational-databases/xml/columns-with-a-name.md)  
  
-   [Столбцы с именем, заданным в виде символа-шаблона](../../relational-databases/xml/columns-with-a-name-specified-as-a-wildcard-character.md)  
  
-   [Столбцы с именем XPath-функции проверки узла](../../relational-databases/xml/columns-with-the-name-of-an-xpath-node-test.md)  
  
-   [Имена столбцов с путем, указанным как data()](../../relational-databases/xml/column-names-with-the-path-specified-as-data.md)  
  
-   [Столбцы, по умолчанию содержащие значение NULL](../../relational-databases/xml/columns-that-contain-a-null-value-by-default.md)  
  
-   [Поддержка пространства имен в режиме PATH](../../relational-databases/xml/namespace-support-in-path-mode.md)  
  
-   [Примеры, использование режима PATH](../../relational-databases/xml/examples-using-path-mode.md)  
  
## <a name="see-also"></a>См. также:  
 [Добавление пространств имен в запросы с WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md)  
  
  
