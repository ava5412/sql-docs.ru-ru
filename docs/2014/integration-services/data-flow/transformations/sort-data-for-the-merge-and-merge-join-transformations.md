---
title: Сортировка данных для преобразований "Слияние" и "Соединение слиянием" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 21b60f8b5007ae574ab48bdd46e2e8f430b299cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316064"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a>Сортировка данных для преобразований «Слияние» и «Соединение слиянием»
  В службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]для преобразований «Слияние» и «Соединение слиянием» необходимы отсортированные входные данные. Входные данные должны быть отсортированы физически, а параметры сортировки должны быть установлены на выходы и выходные столбцы источника или вышестоящего преобразования. Если параметры сортировки определяют, что данные отсортированы, но данные в действительности не отсортированы, операция слияния или соединения слиянием может дать непредвиденные результаты.  
  
## <a name="sorting-the-data"></a>Сортировка данных  
 Сортировку данных можно выполнить одним из следующих способов.  
  
-   В источнике — в инструкции, с помощью которой загружаются данные, — использовать предложение ORDER BY.  
  
-   В потоке данных преобразование «Сортировка» должно предшествовать преобразованию «Слияние» или «Соединение слиянием».  
  
 Если данные являются строковыми, то и преобразование «Слияние», и преобразование «Соединение слиянием» ожидают, что строковые значения отсортированы с использованием параметров сортировки Windows. Чтобы строковые значения передавались преобразованиям «Слияние» и «Соединение слиянием», отсортированным с помощью параметров сортировки Windows, примените следующую процедуру.  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a>Чтобы передавались строковые значения, отсортированные с помощью параметров сортировки Windows  
  
-   Используйте преобразование «Сортировка» для сортировки данных.  
  
     Преобразование «Сортировка» использует параметры сортировки Windows для упорядочения строковых значений.  
  
     —или—  
  
-   Используйте оператор языка Transact-SQL CAST для преобразования значений `varchar` в значения `nvarchar`, а затем с помощью предложения языка Transact-SQL ORDER BY отсортируйте эти данные.  
  
    > [!IMPORTANT]  
    >  Нельзя использовать одно предложение ORDER BY, поскольку для сортировки строковых значений оно использует параметры сортировки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Применение параметров сортировки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , которые отличаются от параметров сортировки Windows порядком сортировки, может привести к тому, что преобразование «Слияние» или «Соединение слиянием» сформирует непредвиденные результаты.  
  
## <a name="setting-sort-options-on-the-data"></a>Настройка параметров сортировки данных  
 Есть два важных свойства сортировки, которые необходимо задать для источника или вышестоящего преобразования, которые предоставляют данные для преобразования «Слияние» или «Соединение слиянием».  
  
-   Свойство `IsSorted` выхода показывает, были ли данные отсортированы. Это свойство должно быть присвоено `True`.  
  
    > [!IMPORTANT]  
    >  Если значением `IsSorted` свойства `True` не приводит к сортировке данных. Это свойство только указывает компонентам нисходящего потока, что данные раньше были отсортированы.  
  
-   `SortKeyPosition` Свойства выходных столбцов, которое указывает, отсортирован ли столбец, порядок сортировки и последовательность, в которой сортируется несколько столбцов. Это свойство должно быть задано для каждого столбца отсортированных данных.  
  
 При сортировке данных с помощью преобразования «Сортировка» это преобразование задает оба свойства требуемым образом для преобразования «Слияние» или «Соединение слиянием». То есть преобразование «Сортировка» задает `IsSorted` свойства своего выхода значение `True`и задает `SortKeyPosition` свойства его выходных столбцов.  
  
 Однако если не отсортировать данные с помощью преобразования «Сортировка», то придется задавать эти свойства вручную на источнике или в вышестоящем преобразовании. С помощью следующей процедуры можно вручную настроить эти свойства на источнике или в вышестоящем преобразовании.  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a>Задание атрибутов сортировки вручную на источнике или в компоненте преобразования  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Найдите на вкладке **Поток данных** соответствующий источник или вышестоящее преобразование или перетащите его из **области элементов** в область конструктора.  
  
4.  Щелкните компонент правой кнопкой мыши и выберите пункт **Показать расширенный редактор**.  
  
5.  Щелкните вкладку **Свойства входов и выходов** .  
  
6.  Нажмите кнопку  **\<имя компонента > выходной**и задайте `IsSorted` свойства `True`.  
  
    > [!NOTE]  
    >  Если пользователь вручную задаст `IsSorted` свойства выходных данных значение `True` и данные не отсортированы, существует могут отсутствующие или недопустимые сравнения данных нисходящему преобразованию слияния или соединение слиянием при выполнении пакета.  
  
7.  Разверните элемент **Выходные столбцы**.  
  
8.  Щелкните столбец, который необходимо обозначить отсортированный и задать его `SortKeyPosition` ненулевое целочисленное значение, следуя следующим правилам:  
  
    -   Целое число должно представлять числовую последовательность начиная с 1 с добавлением по единице.  
  
    -   Положительные целые значения соответствуют возрастающему порядку сортировки.  
  
    -   Отрицательные целые значения соответствуют убывающему порядку сортировки. Если задано отрицательное целое число, положение столбца в последовательности сортировки будет определять абсолютное значение этого числа.  
  
    -   Значение 0 указывает на то, что столбец не отсортирован. Чтобы выходные столбцы не участвовали в сортировке, задайте значение 0.  
  
     В качестве примера настройки свойства `SortKeyPosition` рассмотрите приведенную ниже инструкцию Transact-SQL, которая загружает данные в источник.  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     Для этой инструкции, как задать `SortKeyPosition` свойство для каждого столбца следующим образом:  
  
    -   Задайте для свойства `SortKeyPosition` столбца ColumnA значение 1. Это показывает, что столбец ColumnA является первым при сортировке, а сортировка производится по возрастанию.  
  
    -   Задайте для свойства `SortKeyPosition` столбца ColumnB значение -2. Это показывает, что столбец ColumnB является вторым при сортировке, а сортировка производится по убыванию.  
  
    -   Задайте `SortKeyPosition` свойство столбца ColumnC 3. Это показывает, что столбец ColumnC является третьим при сортировке, а сортировка производится по возрастанию.  
  
9. Повторите шаг 8 для каждого отсортированного столбца.  
  
10. Нажмите кнопку **ОК**.  
  
11. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Преобразование «Слияние»](merge-transformation.md)   
 [Преобразование соединения слиянием](merge-join-transformation.md)   
 [Преобразования служб Integration Services](integration-services-transformations.md)   
 [Пути служб Integration Services](../integration-services-paths.md)   
 [Задача потока данных] ((.. /.. /Control-Flow/Data-Flow-Task.MD)  
  
  
