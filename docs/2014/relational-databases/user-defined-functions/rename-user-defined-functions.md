---
title: Переименование определяемых пользователем функций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2a148cc6188c3750eb9996c692b3c42715f6bd0b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421643"
---
# <a name="rename-user-defined-functions"></a>Переименование определяемых пользователем функций
  Определяемые пользователем функции в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно переименовать с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для переименования определяемой пользователем функции используются.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Имена функций должны соответствовать правилам для [идентификаторов](../databases/database-identifiers.md).  
  
-   При переименовании определяемой пользователем функции не изменяется имя соответствующего объекта в столбце определения представления каталога **sys.sql_modules** . Поэтому не рекомендуется переименовывать объекты этого типа. Лучше удалить хранимую процедуру и создать ее повторно с новым именем.  
  
-   Изменение имени или определения определяемой пользователем функции может привести к тому, что все зависящие от нее объекты при выполнении будут возвращать ошибку, если они не будут обновлены в соответствии с внесенными в функцию изменениями.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для удаления функции у пользователя должно быть разрешение ALTER на схему, которой принадлежит функция, или разрешение CONTROL на функцию. Для повторного создания функции требуется разрешение CREATE FUNCTION на базу данных и разрешение ALTER на схему, в которой создается функция.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-user-defined-functions"></a>Переименование определяемой пользователем функции  
  
1.  В **обозревателе объектов**щелкните значок «плюс» рядом с базой данных, содержащей функцию, которую нужно переименовать.  
  
2.  Щелкните значок «плюс» рядом с папкой **Программирование** .  
  
3.  Щелкните значок «плюс» рядом с папкой, содержащей функцию, которую надо переименовать.  
  
    -   Table-valued Function  
  
    -   Скалярная функция  
  
    -   Агрегатная функция  
  
4.  Щелкните правой кнопкой мыши функцию, которую нужно переименовать, и выберите пункт **Переименовать**.  
  
5.  Введите новое имя функции.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Переименование определяемой пользователем функции**  
  
 Эту задачу нельзя выполнить с помощью инструкций Transact-SQL. Чтобы переименовать определяемую пользователем функцию с помощью Transact-SQL, необходимо сначала удалить существующую функцию, а затем создать ее повторно с новым именем. Убедитесь, что весь код и приложения, ссылающиеся на старое имя функции, теперь используют новое имя.  
  
 Дополнительные сведения см. в разделах [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql) и [DROP FUNCTION (Transact-SQL)](/sql/t-sql/statements/drop-function-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Представление каталога sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)   
 [Просмотр определяемых пользователем функций](user-defined-functions.md)  
  
  
