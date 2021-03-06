---
title: Занятие 5 обучение и сохранить модель, с помощью R и T-SQL (SQL Server машинного обучения) | Документы Microsoft
description: Руководство для внедрения в SQL Server R хранимые процедуры и функции T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bd5bdc7d256a22dbab6662a74dc39073892dbb4d
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250067"
---
# <a name="lesson-5-train-and-save-a-model-using-t-sql"></a>Занятие 5: Обучения и сохранить модель с помощью T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника для разработчиков SQL по использованию R в SQL Server.

На этом занятии вы узнаете, как для обучения модели машинного обучения с помощью R. Будет обучения модели с помощью функции данных, созданный на предыдущем занятии, а затем сохраните обученной модели в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы. В этом случае R-пакеты уже установлены с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], поэтому все, что можно сделать из SQL.

## <a name="create-the-stored-procedure"></a>Создайте хранимую процедуру

При вызове R из T-SQL, можно использовать системную хранимую процедуру [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Тем не менее, для процессов, которые требуется повторно часто, например переподготовки модели проще для инкапсуляции вызов `sp_execute_exernal_script` в другой хранимой процедуры.

1.  Во-первых создайте хранимую процедуру, которая содержит код R для построения модели прогнозирования подсказки. В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], откройте новый **запроса** и выполните следующую инструкцию, чтобы создать хранимую процедуру _TrainTipPredictionModel_. Эта хранимая процедура определяет входные данные и использует пакет R для создания модели логистической регрессии.

    ```SQL
    CREATE PROCEDURE [dbo].[TrainTipPredictionModel]
    
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,
        pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
        from nyctaxi_sample
        tablesample (70 percent) repeatable (98052)
    '
      -- Insert the trained model into a database table
      INSERT INTO nyc_taxi_models
      EXEC sp_execute_external_script @language = N'R',
                                      @script = N'
    
    ## Create model
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)
    summary(logitObj)
    
    ## Serialize model and put it in data frame
    trained_model <- data.frame(model=as.raw(serialize(logitObj, NULL)));
    ',
      @input_data_1 = @inquery,
      @output_data_1_name = N'trained_model'
      ;
    
    END
    GO
    ```

    - Тем не менее чтобы убедиться, что некоторые данные, оставшиеся для проверки модели, 70% данных выбираются в случайном порядке из таблицы данных такси.
    
    - Запрос SELECT использует пользовательскую скалярную функцию _fnCalculateDistance_ для вычисления прямого расстояния между местами посадки и высадки.  Результаты выполнения запроса сохраняются во входной переменной R по умолчанию `InputDataset`.
  
    - Вызовы сценариев R `rxLogit` включены функции, которая является одним из расширенных функциях R с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], чтобы создать модель логистической регрессии.
  
        Двоичная переменная _tipped_ применяется в качестве столбца *меток* или результатов, и модель компонуется с использованием следующих столбцов характеристик:  _passenger_count_, _trip_distance_, _trip_time_in_secs_и _direct_distance_.
  
    -   Модель обучения, сохраненная в переменной R `logitObj`, сериализуется и помещается в кадр данных для вывода в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Выходные данные вставляются в таблицу _nyc_taxi_models_базы данных, чтобы их можно было использовать для составления прогнозов в будущем.
  
2.  Выполните инструкцию, чтобы создать хранимую процедуру, если он еще не существует.

## <a name="generate-the-r-model-using-the-stored-procedure"></a>Создание модели R, с помощью хранимой процедуры

Так как хранимая процедура уже содержит определение входных данных, не требуется для предоставления входного запроса.

1. Создание модели R, вызовите хранимую процедуру без указания параметров:

    ```SQL
    EXEC TrainTipPredictionModel
    ```

2. Контрольное значение **сообщений** окно [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для сообщений, которые может быть выведен R **stdout** потока, как это сообщение: 

    «Сообщения STDOUT из внешнего скрипта: считано строк: 1193025, Всего обработано строк: 1193025, общее время блока: 0.093 секунд»

    Также может отображаться сообщения, относящиеся к конкретной функции `rxLogit`, отображение переменных и показателей, созданных в процессе создания модели.

3.  При завершении инструкции, откройте таблицу *nyc_taxi_models*. Обработка данных и соответствует модели может занять некоторое время.

    Вы увидите, что была добавлена одна новая строка, которая содержит сериализованную модель в столбце _model_.

    ```
    model
    ------
    0x580A00000002000302020....
    ```

В следующем шаге вы используете обученную модель для создания прогнозов.

## <a name="next-lesson"></a>Следующее занятие

[Урок 6: Модель ввода в эксплуатацию](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Предыдущее занятие

[Занятие 4: Создание компонентов данных, с помощью функции T-SQL и R](..//tutorials/sqldev-create-data-features-using-t-sql.md)

