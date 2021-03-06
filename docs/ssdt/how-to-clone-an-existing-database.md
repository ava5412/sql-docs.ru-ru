---
title: Практическое руководство. Клонирование существующей базы данных | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aad3594a-11cf-4e68-a622-071a93d43875
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1037250907c897ce08f85da5af1c739849091338
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085926"
---
# <a name="how-to-clone-an-existing-database"></a>Как клонировать существующую базу данных
В этой задаче используются некоторые из рассмотренных ранее шагов для создания новой базы данных и переноса существующих данных. Кроме того, в ней используются шаги для синхронизации схемы исходной базы данных и базы данных проекта, которые описаны в статье [Как использовать сравнение схем для сопоставления различных определений баз данных](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md).  
  
Использование этих шагов позволяет создать базу данных для разработки или тестирования на основе производственной базы данных с идентичной схемой и данными. Затем можно продолжить разработку тестовой базы данных в подключенном режиме либо создать проект базы данных для разработки и тестирования вне сети, причем все это не нарушая работу производственной базы данных.  
  
> [!WARNING]  
> В следующих процедурах используются сущности, созданные ранее с помощью руководства по [разработке подключенной базы данных](../ssdt/connected-database-development.md).  
  
### <a name="to-create-a-development-database"></a>Создание базы данных разработки  
  
1.  В окне **обозревателя объектов SQL Server** в узле **SQL Server** разверните подключенный экземпляр сервера.  
  
2.  Правой кнопкой мыши щелкните узел **Базы данных** и выберите пункт **Добавить новую базу данных**.  
  
3.  Присвойте новой базе данных имя **TradeDev**.  
  
4.  Правой кнопкой мыши щелкните базу данных **Trade** в **обозревателе объектов SQL Server** и выберите пункт **Сравнение схем**. Выполните действия, указанные в разделе [Как использовать сравнение схем для сопоставления различных определений баз данных](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md), выбрав первоначальную базу данных **Trade** в качестве исходной и новую базу данных **TradeDev** в качестве целевой. В результате схема **TradeDev** обновится в соответствии со схемой **Trade**.  
  
### <a name="to-replicate-data"></a>Репликация данных  
  
1.  В предыдущем шаге дублировалась только схема производственной базы данных в базу данных разработки. В данной процедуре производственные данные дублируются в базу данных разработки.  
  
    Правой кнопкой мыши щелкните таблицу **Suppliers** в базе данных **Trade** и выберите **Просмотр данных**. Откроется редактор данных.  
  
2.  Нажмите кнопку **Скрипт** рядом с элементом **Максимальное количество строк** на панели инструментов.  
  
3.  Когда откроется окно скрипта, убедитесь, что в строке состояния под областью скрипта Transact\-SQL для состояния отображается значение "Подключено". Если отображается значение "Отключено", нажмите кнопку **Подключить** (крайняя слева на панели инструментов) и введите сведения и учетные данные для сервера.  
  
4.  В раскрывающемся меню **База данных** рядом с кнопками **Подключить**/**Отключить** выберите **TradeDev**. Это действие аналогично инструкции `USE` в Transact\-SQL и гарантирует, что скрипт в редакторе кода будет выполнен для базы данных **TradeDev**.  
  
5.  Нажмите кнопку **Выполнить запрос**, чтобы выполнить инструкции `INSERT`. В результате все строки из таблицы `Suppliers` базы данных `Trade` будут вставлены в таблицу `Suppliers` базы данных `TradeDev`.  
  
6.  Повторите приведенные выше шаги для всех таблиц в базе данных `Trade` для репликации в базу данных `TradeDev`.  
  
7.  С помощью редактора данных убедитесь, что все таблицы в новой базе данных `TradeDev` заполнены.  
  
## <a name="see-also"></a>См. также:  
[Как использовать сравнение схем для сопоставления различных определений баз данных](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
