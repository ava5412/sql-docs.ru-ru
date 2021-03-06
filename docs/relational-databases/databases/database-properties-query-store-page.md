---
title: Свойства базы данных (страница "Хранилище запросов") | Документация Майкрософт
ms.custom: ''
ms.date: 11/09/2015
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.querystore.f1
ms.assetid: da47d75e-291a-4305-acef-4b0aaf5215da
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e775734fbcf8fab632f3d2783f98cbe369390a1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32928079"
---
# <a name="database-properties-query-store-page"></a>Свойства базы данных (страница хранилища запросов)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Откройте эту страницу из основной базы данных и используйте ее для настройки и изменения свойств хранилища запросов базы данных. Эти параметры можно также настроить с помощью [параметров ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md). Дополнительные сведения о хранилище запросов см. в разделе [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (от[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
## <a name="options"></a>Параметры  
 Режим работы  
 Допустимые значения: OFF, READ_ONLY и READ_WRITE. OFF отключает хранилище запросов. В режиме READ_WRITE хранилище запросов собирает и сохраняет план запросов и статистические данные о выполнении. В режиме READ_ONLY можно считывать данные из хранилища запросов, но новые сведения не добавляется. Если выделенное свободное место в хранилище запросов будет исчерпано, хранилище переключится в режим работы READ_ONLY.  
  
 Режим работы (фактический)  
 Получает фактический режим работы хранилища запросов.  
  
 Режим работы (запрошенный)  
 Получает и задает нужный режим работы хранилища запросов.  
  
 Интервал сброса данных (в минутах)  
 Определяет частоту, с которой данные, записанные в хранилище запросов, сохраняются на диск. Для оптимизации производительности данные, собранные хранилищем запросов, асинхронно записываются на диск. Настраивается частота, с которой происходит эта асинхронная передача.  
  
 Интервал сбора статистики  
 Получает и задает значение интервала сборка статистики.  
  
 Максимальный размер (Мбайт)  
 Получает и задает свободное место, выделенное для хранилища запросов.  
  
 Режим записи хранилища запросов  
 -   None — новые запросы не записываются.  
  
-   All — записываются все запросы.  
  
-   Auto — запросы записываются с учетом потребления ресурсов.  
  
 Пороговое значение устаревших запросов (в днях)  
 Получает и задает пороговое значение устаревшего запроса. Настройте аргумент STALE_QUERY_THRESHOLD_DAYS, чтобы указать длительность хранения данных в хранилище запросов в днях.  
  
 Очистка данных запроса  
 Удаляет содержимое хранилища запросов.  
  
 Круговые диаграммы  
 На схеме слева показано общее использование файлов базы данных на диске и часть файла, в которой содержатся данные хранилища запросов.  
  
 На схеме справа показана часть квоты хранилища запросов, которая сейчас занята. Обратите внимание, что на левой схеме квота не показана. Квота может превышать текущий размер базы данных.  
  
## <a name="remarks"></a>Remarks  
 Хранилище запросов предоставляет DBA подробные сведения о выборе и производительности плана запросов. Оно упрощает устранение неполадок с производительностью, позволяя быстро находить разницу в производительности, вызванную изменениями в планах запросов. Функция автоматически записывает журнал запросов, планы и статистику выполнения и сохраняет их для просмотра. Она разделяет данные по временным окнам, позволяя просмотреть шаблоны использования и понять, когда изменения плана запросов произошли на сервере. Хранилище запросов можно настроить на странице свойств базы данных хранилища запросов или с помощью параметра [ALTER DATABASE SET](../../t-sql/statements/alter-database-transact-sql-set-options.md) . Сведения в хранилище запросов представлены в диалоговом окне [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] . Дополнительные сведения о хранилище запросов см. в разделе [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры в хранилище запросов (Transact-SQL)](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [Представления каталога хранилища запросов (Transact-SQL)](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)  
  
  
