---
title: Добавление, обновление и удаление данных (Master Data Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2014
ms.assetid: b6295ead-bd2f-49dd-8756-35c6afb59648
caps.latest.revision: 6
author: leolimsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cd14b50e3b883a92aa611b13553a6ecc5647f32c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311994"
---
# <a name="add-update-and-delete-data-master-data-services"></a>Добавление, обновление и удаление данных (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]поддерживает массовое добавление данных в модель и их изменение.  
  
 **Предварительные требования**  
  
-   Требуется разрешение на вставку данных в таблицу stg.\<имя>_Leaf, the stg.\<имя>_Consolidated, stg.\<имя>_Relationship в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
-   Необходимы разрешения на выполнение хранимой процедуры stg.udp_\<имя>_Leaf, stg.udp\_\<имя>_Consolidated или stg.udp\_\<имя>_Relationship в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
-   Эта модель не должна иметь состояние **Зафиксирована**.  
  
 **Добавление, обновление и удаление данных в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]**  
  
1.  Подготовьте элементы к импорту в соответствующую промежуточную таблицу в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , в том числе укажите значения обязательных полей. Общие сведения о промежуточных таблиц, см. в разделе [импорта данных &#40;службы Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
    -   Таблица для конечных элементов — stg.\<имя>_Leaf, где \<имя> — это имя соответствующей сущности. Сведения о требуемых полях см. в разделе [Конечный элемент таблицы элементов (службы Master Data Services)](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md).  
  
    -   Таблица для консолидированных элементов — stg.\<имя>_Consolidated. Сведения о требуемых полях см. в разделе [Промежуточная таблица консолидированных элементов (службы Master Data Services)](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
    -   Таблица для перемещения расположения элементов в явных иерархиях — stg.\<имя>_Relationship. Сведения о требуемых полях см. в разделе [Промежуточная таблица связей (службы Master Data Services)](../../2014/master-data-services/relationship-staging-table-master-data-services.md).  
  
         Общие сведения о перемещении элементов в явных иерархиях см. в разделе [импорта данных &#40;службы Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
    -   Используя значение поля **ImportType** , укажите нужное действие: создание, деактивация или удаление элементов. Дополнительные сведения о значениях см. в разделах [Конечный элемент таблицы элементов (службы Master Data Services)](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md) и [Промежуточная таблица консолидированных элементов (службы Master Data Services)](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
         Общие сведения о деактивации и удалении элементов, см. в разделе [импорта данных &#40;службы Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
2.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и подключитесь к экземпляру ядра базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
     Дополнительные сведения см. в разделе [SQL Server Management Studio](../ssms/sql-server-management-studio-ssms.md).  
  
3.  Импортируйте данные в промежуточные таблицы с помощью мастера импорта и экспорта [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
     Дополнительные сведения см. в разделе [SQL Server Import and Export Wizard](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
4.  Загрузите данные из промежуточных таблиц в таблицы [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , выполнив одно из следующих действий:  
  
    -   Запустите промежуточную хранимую процедуру, которая соответствует промежуточной таблице, в которую нужно переместить данные.  
  
         Общие сведения о промежуточных хранимых процедурах и промежуточных таблиц, см. в разделе [импорта данных &#40;службы Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md). Дополнительные сведения о параметрах для промежуточных хранимых процедур и пример кода см. в разделе [Промежуточная хранимая процедура (службы Master Data Services)](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).  
  
    -   Используйте функциональную область **Управление интеграцией** системы управления основными данными.  
  
         На странице **Промежуточные пакеты** в раскрывающемся списке выберите модель, к которой вы добавляете данные, и нажмите кнопку **Запустить пакеты**. Состояние пакетной обработки указывается в поле **Состояние** . Дополнительные сведения о состояниях см. в разделе [Состояния операции импорта (службы Master Data Services)](../../2014/master-data-services/import-statuses-master-data-services.md).  
  
         ![Страница промежуточных пакетов в диспетчере основных данных](../../2014/master-data-services/media/mds-staging-batches.png "Страница промежуточных пакетов в диспетчере основных данных")  
  
         Промежуточный процесс запускается через промежутки времени, указанные с помощью параметра **Интервал промежуточных пакетов** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../../2014/master-data-services/system-settings-master-data-services.md).  
  
5.  Просмотрите ошибки, возникшие во время помещения на промежуточное хранение и обработку. Дополнительные сведения см. в разделе [Просмотр ошибок, возникновении во время промежуточного процесса &#40;службы Master Data Services&#41; ](view-errors-that-occur-during-staging-master-data-services.md) и [ошибки промежуточного процесса &#40;службы Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
6.  Проверьте данные с помощью бизнес-правил.  
  
     В диспетчере основных данных перейдите к функциональной области **Обозреватель** и примените бизнес-правила для проверки данных. Дополнительные сведения см. в разделе [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md). Для проверки данных также можно использовать хранимую процедуру. Дополнительные сведения см. в разделе [Проверка хранимых процедур (службы Master Data Services)](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
     При загрузке из промежуточных таблиц данные не проверяются автоматически с помощью бизнес-правил. Дополнительные сведения о том, что такое проверка и когда она выполняется, см. в разделе [Проверка (службы Master Data Services)](../../2014/master-data-services/validation-master-data-services.md).  
  
## <a name="see-also"></a>См. также  
 [Импорт данных &#40;службы Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
