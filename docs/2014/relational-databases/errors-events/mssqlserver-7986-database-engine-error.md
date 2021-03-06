---
title: MSSQLSERVER_7986 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7986 (Database Engine error)
ms.assetid: ae64276c-4e1e-4ef3-9ee9-ebeb2f61e565
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46e7ca71044b07851e2bfa5cff1883cdf62f2967
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415843"
---
# <a name="mssqlserver7986"></a>MSSQLSERVER_7986
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7986|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE|  
|Текст сообщения|Предварительная проверка системных таблиц: объект с идентификатором O_ID содержит связи межобъектных цепочек. Страница P_ID1 указывает на P_ID2 в единице распределения с идентификатором A_ID1 (должно быть A_ID2). Инструкция проверки прервана из-за неустранимой ошибки.|  
  
## <a name="explanation"></a>Объяснение  
 Первый этап работы DBCC CHECKDB заключается в осуществлении примитивных проверок страниц данных важных системных таблиц. Найденные на этом этапе ошибки не подлежат исправлению, поэтому при их обнаружении DBCC CHECKDB немедленно прекращает свою работу. Указатель следующей страницы для страницы *P_ID1* на уровне данных заданного объекта указывает на страницу другого объекта, *P_ID2*.  
  
## <a name="user-action"></a>Действие пользователя  
  
### <a name="look-for-hardware-failure"></a>Поиск сбоев оборудования  
 Выполните диагностику оборудования и исправьте все найденные проблемы. Кроме того, просмотрите журнал системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и журнал приложений, а также журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы определить, была ли ошибка вызвана сбоем оборудования. Исправьте все неполадки оборудования, обнаруженные в журналах.  
  
 Если постоянно возникают проблемы с повреждением данных, попробуйте изменить некоторые компоненты оборудования, чтобы локализовать проблему. Убедитесь, что в системе не включено кэширование записи для контроллера дисков. Если есть подозрение, что неполадки вызваны кэшированием записи, обратитесь к поставщику оборудования.  
  
 В конце концов можно попробовать сменить оборудование. Это может включать форматирование дисков и переустановку операционной системы.  
  
### <a name="restore-from-backup"></a>Восстановление из резервной копии  
 Если неполадка не связана с оборудованием и есть безошибочная резервная копия, восстановите базу данных из этой копии.  
  
### <a name="run-dbcc-checkdb"></a>Запуск DBCC CHECKDB  
 Неприменимо. Эту ошибку невозможно исправить автоматически. Если восстановить базу данных из резервной копии не удается, свяжитесь со службой поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  
