---
title: 'Урок 3: Обработка временных рядов, структуры и моделей | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f69c21f87a56a65fabd781c18612e6b475ca85c0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271990"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>Урок 3. Обработка структуры и моделей временных рядов
  На этом занятии вы воспользуетесь [INSERT INTO &#40;расширений интеллектуального анализа данных&#41; ](/sql/dmx/insert-into-dmx) инструкции для обработки структуры интеллектуального анализа данных и созданные модели интеллектуального анализа данных временных рядов.  
  
 При обработке структуры интеллектуального анализа данных службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] считывают исходные данные и создают структуры, поддерживающие модели интеллектуального анализа данных. Всегда необходимо выполнять обработку модели интеллектуального анализа данных и структуры при первом создании. Если задана структура интеллектуального анализа данных при использовании инструкции INSERT INTO, инструкция обрабатывает эту структуру и все связанные с ней модели интеллектуального анализа данных.  
  
 При добавлении модели интеллектуального анализа данных к уже обработанной структуре интеллектуального анализа данных можно использовать инструкцию `INSERT INTO MINING MODEL` для обработки новой модели интеллектуального анализа данных с помощью существующих данных.  
  
 Дополнительные сведения об обработке моделей интеллектуального анализа данных см. в разделе [обработки требования и соображения &#40;интеллектуального анализа данных&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="insert-into-statement"></a>Инструкция INSERT INTO  
 Для обучения структуры интеллектуального анализа данных временных рядов и все связанные с ней модели используется [INSERT INTO &#40;расширений интеллектуального анализа данных&#41; ](/sql/dmx/insert-into-dmx) инструкции. Код инструкции можно разбить на следующие части.  
  
-   Определение структуры интеллектуального анализа данных  
  
-   Список столбцов структуры интеллектуального анализа  
  
-   Определение обучающих данных  
  
 Далее приведен общий пример инструкции `INSERT INTO`:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 В первой строчке кода задается структура интеллектуального анализа данных, которую необходимо обучить:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Следующие строки кода указывают столбцы, определенные структурой интеллектуального анализа данных. Необходимо перечислить все столбцы структуры интеллектуального анализа данных, и каждый столбец должен сопоставляться с каким-либо столбцом из данных исходного запроса.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 Последние строки кода определяют данные, которые будут использованы для обучения структуры интеллектуального анализа данных.  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 На этом занятии требуется определить исходные данные с помощью инструкции `OPENQUERY`. Дополнительные сведения о других способах задания запроса к исходным данным см. в разделе [ &#60;запросом источника данных&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии требуется выполнить следующую задачу:  
  
-   обработать структуру интеллектуального анализа данных Forecasting_MIXED_Structure;  
  
-   обработать связанные модели интеллектуального анализа данных Forecasting_MIXED, Forecasting_ARIMA и Forecasting_ARTXP.  
  
## <a name="processing-the-time-series-mining-structure"></a>Обработка структуры интеллектуального анализа данных временных рядов  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>Обработка структуры интеллектуального анализа данных и связанных с ней моделей с помощью инструкции INSERT INTO  
  
1.  В **обозревателя объектов**, щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], пункты **новый запрос**, а затем нажмите кнопку **расширений интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
2.  Скопируйте стандартный пример использования инструкции INSERT INTO в пустое окно запроса.  
  
3.  Вместо  
  
    ```  
    [<mining structure>]  
    ```  
  
     вставьте  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  Вместо  
  
    ```  
    <mining structure columns>  
    ```  
  
     вставьте  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  Вместо  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     вставьте  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     Исходный запрос ссылается на [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] источник данных, определенный в образце проекта «intermediatetutorial». Этот источник данных используется запросом для доступа к представлению vTimeSeries. Это представление содержит исходные данные, которые будут использованы для обучения модели интеллектуального анализа данных. Если вы не знакомы с этого проекта или о представлении, см. в разделе[занятии 2: построение сценария прогнозирования &#40;данных учебник по интеллектуальному анализу&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
     Полная инструкция теперь должна выглядеть следующим образом.  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
7.  В **Сохранить как** диалоговом окне перейдите к соответствующей папке и присвойте файлу имя `ProcessForecastingAll.dmx`.  
  
8.  На панели инструментов нажмите кнопку **Выполнить** .  
  
 После окончания выполнения запроса можно создавать прогнозы с использованием обработанных моделей интеллектуального анализа данных. В следующем занятии будет создано несколько прогнозов на основе созданных моделей интеллектуального анализа данных.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 4. Создание прогнозов временных рядов с использованием расширений интеллектуального анализа данных](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>См. также  
 [Требования к обработке и рекомендации по &#40;интеллектуального анализа данных&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;запрос источника данных&#62;](/sql/dmx/source-data-query)   
 [OPENQUERY &AMP;#40;РАСШИРЕНИЙ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ&AMP;#41;](/sql/dmx/source-data-query-openquery)  
  
  
