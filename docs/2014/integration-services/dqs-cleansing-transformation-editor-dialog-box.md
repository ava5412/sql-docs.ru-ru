---
title: Диалоговое окно Редактор преобразования очистки DQS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssdqs.designer.cleansing.f1
- SQL12.SSDQS.DESIGNER.DQCONNECTION.F1
ms.assetid: 07e79641-71ee-45d0-a9ba-ed6f9f68f333
caps.latest.revision: 15
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0034984a58971af442ab7154bbba50820dfe1a16
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219674"
---
# <a name="dqs-cleansing-transformation-editor-dialog-box"></a>Диалоговое окно редактора преобразования «Очистка DQS»
  Диалоговое окно **Редактор преобразования "Очистка DQS"** служит для исправления данных с помощью служб Data Quality Services (DQS). Дополнительные сведения см. в статье [Data Quality Services Concepts](../../2014/data-quality-services/data-quality-services-concepts.md).  
  
 Дополнительные сведения об этом преобразовании см. в разделе [DQS Cleansing Transformation](data-flow/transformations/dqs-cleansing-transformation.md).  
  
 **Выбор действия**  
  
-   [Открытие редактора преобразования «Очистка DQS»](#open)  
  
-   [Задание параметров на вкладке «Диспетчер соединений»](#connection)  
  
-   [Задание параметров на вкладке «Сопоставление»](#mapping)  
  
-   [Задание параметров на вкладке «Дополнительно»](#advanced)  
  
-   [Задание параметров в диалоговом окне диспетчера соединений «Очистка DQS»](#manager)  
  
##  <a name="open"></a> Открытие редактора преобразования «Очистка DQS»  
  
1.  Добавьте преобразование «Очистка DQS» в пакет служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Щелкните правой кнопкой мыши компонент и выберите команду **Изменить**.  
  
##  <a name="connection"></a> Задание параметров на вкладке «Диспетчер соединений»  
 **Диспетчер соединений DQS**  
 Выберите существующий диспетчер соединений DQS из списка или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новый диспетчер соединений с помощью диалогового окна **Диспетчер соединений "Очистка DQS"** . См. раздел [Задание параметров в диалоговом окне диспетчера соединений "Очистка DQS"](#manager)  
  
 **База знаний DQS**  
 Выберите существующую базу знаний DQS для подключенного источника данных. Дополнительные сведения о базе знаний DQS см. в разделе [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
 **Шифровать соединение**  
 Укажите, нужно ли шифровать соединение для защиты данных, передаваемых между сервером DQS и службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 **Доступные домены**  
 Выводит список доступных доменов для выбранной базы знаний. Существует два типа доменов: одиночные и составные домены, которые содержат несколько одиночных доменов.  
  
 Дополнительные сведения о сопоставлении столбцов с составными доменами см. в разделе [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).  
  
 Дополнительные сведения о доменах см. в разделе [DQS Knowledge Bases and Domains](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md).  
  
 **Настройка вывода ошибок**  
 Укажите, как следует обрабатывать ошибки уровня строк. Ошибки могут возникать при корректировке в ходе преобразования данных из подключенного источника данных из-за неожиданных значений данных или ограничений проверки.  
  
 Допустимыми являются следующие значения:  
  
-   **Сбой компонента**указывает, что преобразование выполнить не удалось, а входные данные не были вставлены в базу данных служб Data Quality Services. Это значение по умолчанию.  
  
-   **Перенаправить строку**указывает, что входные данные не вставляются в базу данных служб Data Quality Services, а перенаправляются в поток вывода ошибок.  
  
##  <a name="mapping"></a> Задание параметров на вкладке «Сопоставление»  
 Дополнительные сведения о сопоставлении столбцов с составными доменами см. в разделе [Map Columns to Composite Domains](data-flow/transformations/map-columns-to-composite-domains.md).  
  
 **Доступные входные столбцы**  
 Выводит список столбцов из подключенного источника данных. Выберите один или несколько столбцов, содержащих данные, которые нужно исправить.  
  
 **Входной столбец**  
 Показывает входной столбец, выбранный в области **Доступные входные столбцы** .  
  
 **Домен**  
 Выберите домен, сопоставляемый с входным столбцом.  
  
 **Псевдоним источника**  
 Выводит исходный столбец, содержащий исходное значение столбца.  
  
 Щелкните в этом поле, чтобы изменить имя столбца.  
  
 **Псевдоним вывода**  
 Показывает столбец, который выводится **преобразованием "Очистка DQS"**. Это столбец содержит исходное значение столбца или исправленное значение.  
  
 Щелкните в этом поле, чтобы изменить имя столбца.  
  
 **Псевдоним состояния**  
 Показывает столбец, содержащий сведения о состоянии для исправленных данных. Щелкните в этом поле, чтобы изменить имя столбца.  
  
##  <a name="advanced"></a> Задание параметров на вкладке «Дополнительно»  
 **Стандартный вывод**  
 Показывает, будут ли данные выводиться в стандартном формате с учетом выходного формата, определенного для доменов. Дополнительные сведения о стандартном формате см. в разделе [Очистка данных](../../2014/data-quality-services/data-cleansing.md).  
  
 **Достоверность**  
 Показывает, включается ли уровень достоверности для исправленных данных. Уровень достоверности определяет степень уверенности в правильности изменений, выполненных или рекомендуемых службами DQS. Дополнительные сведения об уровнях достоверности см. в разделе [Очистка данных](../../2014/data-quality-services/data-cleansing.md).  
  
 **Причина**  
 Указывает, включается ли причина исправления данных.  
  
 **Добавленные данные**  
 Укажите, следует ли выводить дополнительные данные, полученные от существующего поставщика ссылочных данных. Дополнительные сведения см. в статье [Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md).  
  
 **Схема добавленных данных**  
 Укажите, следует ли выводить схему данных. Дополнительные сведения см. в разделе [Добавление домена или составного домена к ссылочным данным](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).  
  
##  <a name="manager"></a> Задание параметров в диалоговом окне диспетчера соединений «Очистка DQS»  
 **Имя сервера**  
 Выберите или введите имя сервера DQS, к которому нужно подключиться. Дополнительные сведения об этом сервере см. в разделе [DQS Administration](../../2014/data-quality-services/dqs-administration.md).  
  
 **Проверка соединения**  
 Нажмите, чтобы убедиться в работоспособности выбранного соединения.  
  
 Также можно открыть диалоговое окно **Диспетчер соединений «Очистка DQS»** из области соединений, выполнив следующие действия.  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте существующий проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или создайте новый.  
  
2.  Щелкните правой кнопкой мыши в области соединений, выберите команду **Создать соединение**, а затем выберите пункт **DQS**.  
  
3.  Нажмите кнопку **Добавить**.  
  
## <a name="see-also"></a>См. также  
 [Применение правил качества данных к источнику данных](data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
  
