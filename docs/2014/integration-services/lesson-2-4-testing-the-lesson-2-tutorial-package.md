---
title: Шаг 4. Проверка учебного пакета, созданного на занятии 2 | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 83aa206c8ac809e814fd89a415c25be2912aaa8e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298554"
---
# <a name="step-4-testing-the-lesson-2-tutorial-package"></a>Шаг 4. Проверка учебного пакета, созданного на занятии 2
  Используя настроенный контейнер «цикл по каждому элементу» и диспетчер соединений с неструктурированными файлами, можно в пакете, созданном на занятии 2, поочередно обрабатывать коллекцию из 14 неструктурированных файлов в папке образцов данных. Каждый раз при обнаружении имени файла, отвечающего указанным критериям имен файлов, в контейнере «цикл по каждому элементу» это имя подставляется в определенную пользователем переменную. В переменной, в свою очередь, обновляется свойство ConnectionString диспетчера соединений с неструктурированными файлами, после чего выполняется соединение с новым неструктурированным файлом. Затем в контейнере «цикл по каждому элементу» выполняется задача неизмененного потока данных по данным нового неструктурированного файла, после чего устанавливается соединение со следующим файлом в папке.  
  
 Для проверки новой функциональности циклов, которая была добавлена в пакет, используйте следующую процедуру.  
  
> [!NOTE]  
>  Если вы запускали пакет из занятия 1, то перед запуском пакета из этого занятия необходимо удалить записи из dbo.FactCurrency в AdventureWorksDW2012. В противном случае запуск пакета завершится ошибкой, указывающей на нарушение ограничения первичного ключа. Те же ошибки возникнут в случае, если вы запустите пакет путем выбора из меню пунктов «Отладка или начать отладку» (или нажатия клавиши F5), так как будут запущены и занятие 1, и занятие 2. Инструкция из занятия 2 попытается вставить записи, которые уже были вставлены в занятии 1.  
  
## <a name="checking-the-package-layout"></a>Проверка макета пакета  
 Прежде чем тестировать пакет, следует убедиться, что поток управления и поток данных пакета, созданного на занятии 2, содержит объекты, показанные на следующих диаграммах. Поток данных должен быть идентичен потоку данных в занятии 1.  
  
 **Поток управления**  
  
 ![Поток управления в пакете](../../2014/tutorials/media/task4lesson2control.gif "Поток управления в пакете")  
  
 **Поток данных**  
  
 ![Поток данных в пакете](../../2014/tutorials/media/task9lesson1data.gif "Поток данных в пакете")  
  
### <a name="to-test-the-lesson-2-tutorial-package"></a>Тестирование пакета учебника занятия 2  
  
1.  В **обозревателе решений**щелкните правой кнопкой мыши элемент **Lesson 2.dtsx** и выберите команду **Выполнить пакет**.  
  
     Будет начато выполнение пакета. Состояние каждого из циклов можно проверить в окне вывода или на вкладке **Выполнение** . Например можно увидеть, что в целевую таблицу было добавлено 1097 строк из файла Currency_VEB.txt.  
  
2.  После окончания работы пакета выберите в меню **Отладка** пункт **Остановить отладку**.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 5. Добавление конфигураций пакетов в модель развертывания пакета](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## <a name="see-also"></a>См. также  
 [Запуск проектов и пакетов](packages/run-integration-services-ssis-packages.md)  
  
  
