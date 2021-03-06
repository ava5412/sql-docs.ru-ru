---
title: Учебник. Создание простого табличного отчета (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d9e30521-f8ae-4c45-89c3-d40727f622f7
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5a3831372791023edb9f83064aa77878dcf41dfd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186061"
---
# <a name="tutorial-creating-a-basic-table-report-report-builder"></a>Учебник. Создание простого табличного отчета (построитель отчетов)
  Это учебник поможет создать простой табличный отчет на основе образца данных по продажам. На приведенной ниже иллюстрации показан отчет, который предстоит создать.  
  
 ![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")  
  
##  <a name="BackToTop"></a> Новые знания  
 В этом учебнике рассматриваются следующие темы:  
  
1.  [Создание нового отчета с самого начала](#CreateTable)  
  
    1.  [Укажите подключение к данным в мастере таблиц](#DataConnection)  
  
    2.  [Создание запроса в мастере таблиц](#Query)  
  
    3.  [Разбиение данных по группам в мастере таблиц](#Groups)  
  
    4.  [Добавление строк подытога и итога в мастере таблиц](#Subtotals)  
  
    5.  [Выбор стиля в мастере таблиц](#Style)  
  
2.  [Форматирование данных в денежном формате](#FormatCurrency)  
  
3.  [Форматирование данных в формат даты](#FormatDate)  
  
4.  [Изменение ширины столбцов](#Width)  
  
5.  [Добавление заголовка отчета](#Title)  
  
6.  [Сохранение отчета](#Save)  
  
7.  [Экспорт отчета](#Export)  
  
 Предполагаемое время для выполнения заданий данного учебника: 20 минут  
  
## <a name="requirements"></a>Требования  
 Дополнительные сведения о требованиях см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="CreateTable"></a> 1. Создание нового отчета, начиная со страницы «Приступая к работе»  
 Создание табличного отчета из **Приступая к работе** диалоговое окно. Имеется два режима: конструктор отчетов и конструктор общего набора данных. В режиме конструктора отчетов данные задаются в области данных отчета, а макет отчета — в области конструктора. В режиме конструктора общего набора данных создаются запросы к наборам данных для совместного использования. В этом учебнике будет использоваться режим конструктора отчетов.  
  
#### <a name="to-create-a-new-report"></a>Создание нового отчета  
  
1.  Нажмите кнопку **Пуск**, наведите курсор на пункты **Все программы**, **Построитель отчетов Microsoft SQL Server 2012**и выберите пункт **Построитель отчетов**.  
  
     Откроется диалоговое окно **Приступая к работе** .  
  
    > [!NOTE]  
    >  Если диалоговое окно **Приступая к работе** не откроется, в меню кнопки **Построитель отчетов** выберите **Создать**.  
  
2.  Убедитесь, что на левой панели выбран **Новый отчет** .  
  
3.  Убедитесь в том, что на панели справа выбран **Мастер таблицы или матрицы** .  
  
##  <a name="DataConnection"></a> 1а. Указание подключения к данным в мастере таблиц  
 Подключение к данным содержит сведения, необходимые для подключения к внешнему источнику данных, например к базе данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Обычно сведения о соединении и учетные данные, которые будут использоваться при соединении с источником данных, можно получить у владельца источника данных. Чтобы указать подключение к данным, можно воспользоваться общим источником данных с сервера отчетов или создать внедренный источник данных, используемый только в этом отчете.  
  
 В этом учебнике используется внедренный источник данных. Дополнительные сведения об использовании общих источников данных см. в разделе [Альтернативные способы создания подключения к данным &#40;построитель отчетов&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
#### <a name="to-create-an-embedded-data-source"></a>Создание внедренного источника данных  
  
1.  На странице **Выбор набора данных** выберите команду **Создать набор данных**, а затем нажмите кнопку **Далее**. Откроется страница **Выберите соединение с источником данных** .  
  
2.  Нажмите кнопку **Создать**. Откроется диалоговое окно **Свойства источника данных** .  
  
3.  В **имя**, тип **Product Sales** имя источника данных.  
  
4.  Убедитесь, что в поле **Выберите тип соединения**выбран тип **Microsoft SQL Server** .  
  
5.  В **строку подключения**, введите следующий текст, где  *\<servername >* — имя экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
    ```  
    Data Source=<servername>  
    ```  
  
     Поскольку используется запрос, содержащий данные, а не извлекающий данные из базы, строка подключения не включает имя базы данных. Дополнительные сведения см. в разделе [Предварительные условия для использования учебников (построитель отчетов)](../reporting-services/report-builder-tutorials.md).  
  
6.  Нажмите кнопку **Учетные данные**. Введите учетные данные, необходимые для доступа к внешнему источнику данных.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Снова откроется страница **Выбор соединения с источником данных** .  
  
8.  Нажмите кнопку **Проверить соединение**, чтобы проверить соединение с источником данных.  
  
     Отобразится сообщение «Соединение установлено успешно».  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. Нажмите кнопку **Далее**.  
  
##  <a name="Query"></a> 1б. Создание запроса в мастере таблиц  
 В отчете можно использовать общий набор данных со стандартным запросом или создать внедренный набор данных только для этого отчета. В этом учебнике рассматривается создание внедренного набора данных.  
  
> [!NOTE]  
>  В этом учебнике запрос уже содержит значения данных, поэтому внешний источник данных не требуется. В связи с этим запрос получается весьма длинным. В рабочей среде запрос не будет содержать данные. Этот запрос содержит данные только в учебных целях.  
  
#### <a name="to-create-a-query"></a>Создание запроса  
  
1.  На странице **Создание запроса** открывается конструктор реляционных запросов. В этом учебнике будет использоваться текстовый конструктор запросов.  
  
     Нажмите кнопку **Редактировать как текст**. Текстовый конструктор запросов отображает панель запросов и панель результатов.  
  
2.  Вставьте в поле [!INCLUDE[tsql](../includes/tsql-md.md)] Запрос **следующий запрос** .  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(9924.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Mini Battery Charger' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Telephoto Conversion Lens' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,'Accessories' as Subcategory,    
       'USB Cable' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Business Videographer' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-10' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Social Videographer' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Advanced Digital' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Compact Digital' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Consumer Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera 35mm' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
  
    ```  
  
3.  На панели инструментов конструктора запросов нажмите кнопку **Выполнить** (**!**).  
  
     Запрос выполняется и отображает результирующий набор для полей SalesDate, Subcategory, Product, Sales и Quantity.  
  
     В результирующем наборе столбцам присваиваются заголовки в соответствии с именами в запросе. В наборе данных имена полей основываются на именах столбцов и сохраняются в отчете. После завершения мастера можно просмотреть коллекцию полей набора данных в области данных отчета.  
  
4.  Нажмите кнопку **Далее**.  
  
##  <a name="Groups"></a> 1c. Организация данных в группы в мастере таблиц  
 При выборе полей для группирования создается таблица со строками и столбцами, отображающими подробные и агрегированные данные.  
  
#### <a name="to-organize-data-into-groups"></a>Организация данных в группы  
  
1.  На странице **Размещение полей** перетащите поле "Продукт" в область **Значения**.  
  
2.  Перетащите поле "Количество" в область **Значения** и поместите ниже поля "Продукт".  
  
     Значение поля Quantity автоматически вычисляется с помощью функции Sum, агрегатной функции по умолчанию для числовых полей. Значение вычисляется по формуле [Sum(Quantity)].  
  
     Доступные агрегатные функции можно просмотреть в раскрывающемся списке. Не изменяйте агрегатную функцию.  
  
3.  Перетащите поле Sales в область **Значения** и поместите его ниже поля [Sum(Quantity)].  
  
     Значение поля Sales вычисляется агрегатной функцией Sum. Значение равно [Sum(Sales)].  
  
     Шаги 1, 2 и 3 задают данные, отображаемые в таблице.  
  
4.  Перетащите поле SalesDate в область **Группы строк**.  
  
5.  Перетащите поле "Подкатегория" в область **Группы строк** и поместите его ниже поля SalesDate.  
  
     Шаги 4 и 5 организуют значения полей сначала по дате, а потом по подкатегории продукта для данной даты.  
  
6.  Нажмите кнопку **Далее**.  
  
##  <a name="Subtotals"></a> 1d. Добавление строк подытога и итога в мастере таблиц  
 После создания групп можно добавить и отформатировать строки, в которых будут отображаться значения агрегатной обработки полей. Можно выбрать, следует ли показывать все данные или позволить пользователю сворачивать и разворачивать сгруппированные данные интерактивно.  
  
#### <a name="to-add-subtotals-and-totals"></a>Добавление подытогов и итогов  
  
1.  На странице **Выбор макета** в области **Параметры**убедитесь в том, что выбран параметр **Показать подытоги и общие итоги** .  
  
2.  Убедитесь в том, что выбран параметр **Заблокированный, подытог ниже** .  
  
     На панели просмотра в мастере отображается таблица с пятью строками. При запуске отчета каждая строка отобразится следующим образом:  
  
    1.  Первая строка повторится один раз для таблицы, чтобы отобразить заголовки столбцов.  
  
    2.  Вторая строка повторится один раз для каждого элемента строки в заказе на продажу и отобразит название продукта, количество заказа и линейный итог.  
  
    3.  Третья строка повторится один раз для каждого заказа на продажу и отобразит подытоги для каждого заказа.  
  
    4.  Четвертая строка повторится один раз для каждой даты заказа и отобразит подытоги для каждого дня.  
  
    5.  Пятая строка повторится один раз для таблицы и отобразит итоговые суммы.  
  
3.  Снимите флажок **Развернуть или свернуть группы**. В описываемом здесь отчете не используется функция углубленной детализации, которая позволяет пользователю разворачивать родительскую групповую иерархию, чтобы отобразить строки дочерней группы и строки подробностей.  
  
4.  Нажмите кнопку **Далее**.  
  
##  <a name="Style"></a> 1E. Выбор стиля в мастере таблиц  
 Стиль задает стиль шрифта, набор цветов и стиль границы.  
  
#### <a name="to-specify-a-table-style"></a>Задание стиля таблицы  
  
1.  На **Выбор стиля** страницы, в панели «Стили» выберите «Аквамарин».  
  
     На панели предварительного просмотра отобразится образец таблицы с этим стилем.  
  
2.  При желании можно выбрать другие стили, чтобы увидеть таблицу, оформленную в этих стилях.  
  
3.  Нажмите кнопку **Готово**.  
  
 Таблица добавляется в область конструктора. В таблице содержится 5 столбцов и 5 строк. Панель "Группы строк" содержит три группы строк: SalesDate, Subcategory и Details. Подробные данные — это все данные, которые извлекаются с помощью запроса к набору данных.  
  
##  <a name="FormatCurrency"></a> 2. Форматирование данных в денежном формате  
 По умолчанию сводные данные поля Sales отображаются в виде числа с общим форматом. Отформатируйте его для представления валюты. Чтобы форматируемые текстовые поля и текст заполнителей отображался в виде образцов значений, переключайте параметр **Стили заполнителя** .  
  
#### <a name="to-format-a-currency-field"></a>Форматирование поля валюты  
  
1.  Щелкните **Конструктор** для переключения в режим конструктора.  
  
2.  Щелкните ячейку во второй строке (под строкой заголовков столбцов) в столбце Sales и перетащите указатель мыши вниз, чтобы выбрать все ячейки, содержащие `[Sum(Sales)]`.  
  
3.  На вкладке **Главная** в группе **Число** нажмите кнопку **Валюта** . Ячейки изменятся, отображая содержимое в формате валюты.  
  
     Если в качестве региональных настроек компьютера выбран «Английский (США)», текстом по умолчанию образца будет [**$12,345.00**]. Если значение валюты не отображается, щелкните ссылку **Стили заполнителя** в группе **Числа** , а затем нажмите кнопку **Образцы значений**.  
  
4.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Сводные значения для столбца Sales отображаются в денежном формате.  
  
##  <a name="FormatDate"></a> 3. Форматирование данных в формат даты  
 По умолчанию в поле SalesDate отображаются дата и время. Можно отформатировать его таким образом, чтобы отображалась только дата.  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a>Указание форматирования для поля даты в формат по умолчанию  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните ячейку, содержащую `[SalesDate]`.  
  
3.  На ленте, на вкладке **Корневая папка** в группе **Число** в раскрывающемся списке выберите **Дата**.  
  
     В ячейке будет содержаться дата **[1/31/2000]**. Если дата не отображается, щелкните ссылку **Стили заполнителя** в группе **Числа** , а затем нажмите кнопку **Образцы значений**.  
  
4.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Значения SalesDate отображаются в формате даты по умолчанию.  
  
#### <a name="to-change-the-date-format-to-a-custom-format"></a>Замена формата даты на пользовательский формат  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните ячейку, содержащую `[SalesDate]`.  
  
3.  На **Главная** на вкладке **номер** нажмите кнопку вызова диалогового окна.  
  
     Кнопка запуска — это маленькая стрелка в правом углу группы. Откроется диалоговое окно **Свойства текстового поля** .  
  
4.  Убедитесь в том, что на панели категорий выбран пункт **Дата** .  
  
5.  На панели **Тип** выберите **31 января 2000 года**.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     В ячейке отобразится пример даты **[31 января 2000 года]**.  
  
7.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
 Значение SalesDate отображается с названием месяца вместо его номера.  
  
##  <a name="Width"></a> 4. Изменение ширины столбцов  
 По умолчанию в каждой ячейке таблицы есть текстовое поле. Текстовое поле расширяется вниз, чтобы вместить введенный текст при подготовке страницы к просмотру. В отчете, готовом для просмотра, каждая строка расширяется по высоте самого высокого текстового поля в строке. Высота строки в области конструктора не влияет на высоту строки в отчете, готовом для просмотра.  
  
 Чтобы уменьшить высоту каждой строки, увеличьте ширину столбца, чтобы ожидаемое содержимое текстовых полей умещалось в одну строку.  
  
#### <a name="to-change-the-width-of-table-columns"></a>Изменение ширины столбцов таблицы  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните таблицу, чтобы сбоку и сверху от нее появились маркеры строк и столбцов.  
  
     Серые линии, расположенные вдоль верха и стороны таблицы, — это маркеры столбцов и строк.  
  
3.  Установите указатель на линии раздела между маркерами столбцов, чтобы курсор принял вид двойной стрелки. Перетаскиванием установите нужный размер столбцов. Например, расширьте столбец Product, чтобы название продукта отображалось в одной строке.  
  
4.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
##  <a name="Title"></a> 5. Добавление заголовка отчета  
 Заголовок отчета отображается в верхней части отчета. Можно поместить заголовок отчета в верхнем колонтитуле или, если в отчете колонтитулы не используются, в текстовом поле в верхней части текста отчета. В данном учебнике это текстовое поле автоматически размещается в верхней части текста отчета.  
  
 Текст можно улучшить, применяя к отдельным символам различные стили шрифтов, размеры и цвета. Дополнительные сведения см. в разделе [Форматирование текста в текстовом поле &#40;построитель отчетов и службы SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).  
  
#### <a name="to-add-a-report-title"></a>Добавление заголовка отчета  
  
1.  В области конструктора щелкните ссылку **Щелкните, чтобы добавить заголовок**.  
  
2.  Введите фразу **Product Sales**и щелкните вне текстового поля.  
  
3.  Щелкните правой кнопкой мыши текстовое поле **Продажи товаров** и выберите пункт **Свойства текстового поля**.  
  
4.  В диалоговом окне **Свойства текстового поля** нажмите кнопку **Шрифт**.  
  
5.  В списке **Размер** выберите **18пт**.  
  
6.  В списке **Цвет** выберите **Васильковый**.  
  
7.  Выберите **Полужирное**начертание.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Save"></a> 6. Сохранение отчета  
 Сохраните отчет на сервере отчетов или на своем компьютере. Если не сохранить отчет на сервере отчетов, некоторые функции служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , в том числе элементы отчета и вложенные отчеты, будут недоступны.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Сохранение отчета на сервере отчетов  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Нажмите кнопку **Последние сайты и серверы**.  
  
3.  Выберите или введите имя сервера отчетов, для которого существует разрешение на сохранение отчетов.  
  
     Появится сообщение «Соединение с сервером отчетов». После того как соединение установлено, пользователю представляется содержимое папки, заданной администратором сервера отчетов как место по умолчанию для отчетов.  
  
4.  В поле **Имя**замените имя по умолчанию фразой **Product Sales**.  
  
5.  Нажмите кнопку **Сохранить**.  
  
 Отчет будет сохранен на сервере отчетов. Имя сервера отчетов, с которым установлено соединение, будет отображено в строке состояния в нижней части окна.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Сохранение отчета на компьютере  
  
1.  Нажмите кнопку **Построитель отчетов** и выберите **Сохранить как**.  
  
2.  Перейдите на **Рабочий стол**, откройте папку **Мои документы**или **Мой компьютер**и перейдите в папку, в которую нужно сохранить отчет.  
  
3.  В поле **Имя**замените имя по умолчанию фразой **Product Sales**.  
  
4.  Нажмите кнопку **Сохранить**.  
  
##  <a name="Export"></a> 7. Экспорт отчета  
 Отчеты можно экспортировать в различные форматы, например Microsoft Excel или CSV. Дополнительные сведения см. в разделе [экспорт отчетов &#40;построитель отчетов и службы SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md).  
  
 В этом учебнике описан экспорт отчета в формат Excel и задание свойства отчета, позволяющего присваивать пользовательские имена вкладкам книги.  
  
#### <a name="to-specify-the-workbook-tab-name"></a>Присвоение имени вкладке книги  
  
1.  Щелкните **Конструктор** для возврата в режим конструктора.  
  
2.  Щелкните в любом месте за пределами отчета.  
  
3.  . В панели «Свойства» найдите свойство InitialPageName и введите **Product Sales Excel**.  
  
    > [!NOTE]  
    >  Если панель свойств не отображается, перейдите на вкладку "Вид" на ленте и нажмите кнопку **свойства**.  
  
#### <a name="to-export-a-report-to-excel"></a>Экспорт отчета в Excel  
  
1.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.  
  
2.  . На ленте щелкните **Экспорт**, а затем нажмите кнопку **Excel**.  
  
     Откроется диалоговое окно **Сохранить как** .  
  
3.  Перейдите к **документов** папки.  
  
4.  В **имя файла** текстовое поле, тип **Product Sales Excel**.  
  
5.  Убедитесь, что тип файла **книгу Excel**.  
  
6.  Нажмите кнопку **Сохранить**.  
  
#### <a name="to-view-the-report-in-excel"></a>Просмотр отчета в Excel  
  
1.  Откройте **документов** папку и дважды щелкните **Product Sales Excel.xlsx**.  
  
2.  Убедитесь в том, что вкладка книги имеет имя **Продажи товаров Excel**.  
  
## <a name="next-steps"></a>Следующие шаги  
 На этом пошаговое руководство по созданию простого табличного отчета закончено. Дополнительные сведения о таблицах см. в разделе [Таблицы, матрицы, списки &#40;построитель отчетов и службы SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также  
 [Учебники по &#40;построитель отчетов&#41;](report-builder-tutorials.md)   
 [Построитель отчетов в SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
