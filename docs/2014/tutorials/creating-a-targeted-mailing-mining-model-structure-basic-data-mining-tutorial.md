---
title: Создание структуры модели интеллектуального анализа данных прямой почтовой рассылки (учебник интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
caps.latest.revision: 54
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c9c760ddd7f5445dfc00cc7c40ef877269940383
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282240"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a>Создание структуры модели интеллектуального анализа данных прямой почтовой рассылки (учебник по интеллектуальному анализу данных — начальный уровень)
  Первым шагом в создании сценария прямой почтовой рассылки является использование мастера интеллектуального анализа данных среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для создания новой структуры интеллектуального анализа данных и модели интеллектуального анализа данных дерева принятия решений.  
  
 В этой задаче нужно настроить новую структуру интеллектуального анализа данных и добавление начального интеллектуального анализа данных модели на основе [!INCLUDE[msCoName](../includes/msconame-md.md)] алгоритм дерева принятия решений. Для создания такой структуры сначала необходимо выбрать таблицы и представления, а затем указать столбцы для обучения и столбцы для проверки.  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a>Создание структуры интеллектуального анализа данных для сценария прямой почтовой рассылки  
  
1.  В обозревателе решений щелкните правой кнопкой мыши **структуры интеллектуального анализа данных** и выберите **создать структуру интеллектуального анализа** запустить мастер интеллектуального анализа данных.  
  
2.  На странице **Вас приветствует мастер интеллектуального анализа данных** нажмите кнопку **Далее**.  
  
3.  На **Выбор метода определения** странице, убедитесь, что **из существующей реляционной базы данных или хранилища данных** выбран, а затем нажмите кнопку **Далее**.  
  
4.  На **создать структуру интеллектуального анализа данных** раздела **какой метод интеллектуального анализа данных вы хотите использовать?** выберите **дерева принятия решений Майкрософт**.  
  
    > [!NOTE]  
    >  Если появится предупреждение о том, что алгоритмов интеллектуального анализа данных не обнаружено, это может означать, что свойства проекта настроены неправильно. Это предупреждение выдается, только когда проект пытается получить список алгоритмов интеллектуального анализа данных с сервера служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и не находит сервера. По умолчанию [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] будет использовать **localhost** сервером. Если используется другой экземпляр или именованный экземпляр, нужно изменить свойства проекта. Дополнительные сведения см. в разделе [Создание проекта служб Analysis Services &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).  
  
5.  Нажмите кнопку **Далее**.  
  
6.  На **Выбор представления источников данных** странице **доступные представления источников данных** области, выберите **Прямая почтовая рассылка**. Можно щелкнуть **Обзор** просмотреть таблицы в представлении источника данных, а затем нажмите кнопку **закрыть** чтобы вернуться в мастер.  
  
7.  Нажмите кнопку **Далее**.  
  
8.  На **определение типов таблиц** странице, установите флажок в **случай** столбец для vTargetMail использовать его в качестве таблицы вариантов и нажмите кнопку **Далее**. Таблица ProspectiveBuyer будет использоваться позже в целях проверки, поэтому на данном этапе ее не нужно учитывать.  
  
9. На **Определение обучающих данных** страницы, вы определите по крайней мере один прогнозируемый столбец, один ключевой столбец и один входной столбец для модели. Установите флажок в **прогнозируемый** столбца в **BikeBuyer** строки.  
  
    > [!NOTE]  
    >  Обратите внимание на предупреждение в нижней части окна. Вы не сможете перейти на следующую страницу, пока не будет выбран хотя бы один **ввода** и один **прогнозируемый** столбца.  
  
10. Нажмите кнопку **предложить** открыть **предложение связанных столбцов** диалоговое окно.  
  
     **Предложить** кнопка включена, каждый раз, когда был выбран по крайней мере один прогнозируемый атрибут. **Предложение связанных столбцов** диалоговое окно содержит столбцы, наиболее тесно связаны с прогнозируемым столбцом, а также перечисляются атрибуты в порядке их корреляции с прогнозируемым атрибутом. Столбцы со значительной корреляцией (степень достоверности превышает 95 %) автоматически выделены как включаемые в модель.  
  
     Посмотрите рекомендации, а затем нажмите кнопку **отменить** toignore предложения.  
  
    > [!NOTE]  
    >  Если щелкнуть **ОК**, все перечисленные предложения будут помечены как входные столбцы в мастере. Если нужны не все предложения, значения придется изменять вручную.  
  
11. Убедитесь, что флажок в **ключ** выбран столбец **CustomerKey** строки.  
  
    > [!NOTE]  
    >  Если для таблицы с входными данными из представления источников данных указан ключ, мастер интеллектуального анализа данных автоматически выберет этот столбец в качестве ключа для модели.  
  
12. Установите флажки в **ввода** столбца в перечисленных ниже строках. Чтобы установить флажки в нескольких столбцах, можно выделить диапазон ячеек и удерживать нажатой клавишу CTRL при установке флажка.  
  
    -   **Срок действия**  
  
    -   **CommuteDistance**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **Gender**  
  
    -   **GeographyKey**  
  
    -   **HouseOwnerFlag**  
  
    -   **MaritalStatus**  
  
    -   **NumberCarsOwned**  
  
    -   **NumberChildrenAtHome**  
  
    -   **Регион**  
  
    -   **TotalChildren**  
  
    -   **YearlyIncome**  
  
13. В крайнем левом столбце на странице установите флажки в перечисленных ниже строках.  
  
    -   **AddressLine1**  
  
    -   **AddressLine2**  
  
    -   **DateFirstPurchase**  
  
    -   **EmailAddress**  
  
    -   **FirstName**  
  
    -   **Фамилия**  
  
     Убедитесь, что эти строки имеют флажки только в левом столбце. Эти столбцы будут добавлены в структуру, но не будут включены в модель. Однако после построения модели их можно будет использовать для детализации и проверки. Дополнительные сведения о детализации см. в разделе [запросы детализации &#40;интеллектуального анализа данных&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
14. Нажмите кнопку **Далее**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Указание типа данных и типа содержимого &#40;учебник интеллектуального анализа данных&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>См. также  
 [Определение типов таблиц &#40;мастер интеллектуального анализа данных&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md)   
 [Конструктор интеллектуального анализа данных](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Алгоритм дерева принятия решений (Майкрософт)](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
