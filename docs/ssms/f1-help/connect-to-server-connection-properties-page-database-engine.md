---
title: "Соединение с сервером (страница &quot;Свойства подключения&quot;) ядра СУБД | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connecttoce.connectionproperties.f1
- sql13.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 22cef3465036947ad6389b41c4c80bfc5ef965cb
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-connection-properties-page-database-engine"></a>Соединение с сервером (страница "Свойства подключения") ядра СУБД
Данная вкладка позволяет просмотреть или указать параметры при соединении с экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] или регистрации компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)] в списке **Зарегистрированные серверы**. Кнопки**Соединить** и **Параметры** появляются в этом диалоговом окне только при соединении с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)]. Кнопки**Проверить** и **Сохранить** появляются в этом диалоговом окне только при регистрации компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
## <a name="options"></a>Параметры  
**Подключиться к базе данных**  
Выберите базу данных для подключения из списка. При выборе **<default>**будет выполнено подключение к базе данных по умолчанию для сервера. Если выбрано значение **<Browse server>**, можно найти на сервере базу данных для подключения.  
  
При соединении с экземпляром ядра СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] через [!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)]необходимо использовать проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и указать базу данных в диалоговом окне **Соединение с сервером** на вкладке **Свойства соединения** . Обязательно установите флажок **Шифрование соединения** .  
  
По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] соединяется с базой данных **master**. Если указать пользовательскую базу данных, то в обозревателе объектов будет видна только эта база данных и ее объекты. Если соединиться с базой данных **master**, будут видны все базы данных. Дополнительные сведения см. в разделе [Общие сведения о базе данных SQL Windows Azure](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
**Сетевой протокол**  
Выберите протокол из списка. Доступны те клиентские протоколы, которые настроены с помощью «Настройки сети клиента» в меню «Управление компьютером».  
  
**Размер сетевого пакета**  
Введите размер пакетов, отправляемых по сети. Значение по умолчанию равно 4096 байт.  
  
**Время ожидания соединения**  
Укажите в секундах время ожидания установки соединения. Значение по умолчанию — 15 секунд.  
  
**Время ожидания выполнения**  
Введите время ожидания в секундах до завершения выполнения задачи на сервере. Значение по умолчанию равно 0. Это означает, что время ожидания не установлено.  
  
**Шифрование соединения**  
Задает принудительное шифрование соединения.  
  
**Использовать пользовательский цвет**  
Выберите, чтобы указать цвет фона для строки состояния в окне редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)] . Чтобы указать цвет, нажмите кнопку **Выбрать**. В диалоговом окне **Цвет** выберите стандартный цвет в сетке **Основные цвета** или нажмите кнопку **Определить цвет** , чтобы определить и применить пользовательский цвет.  
  
-   Если указан цвет для записи сервера на панели **Обозреватель объектов** , он используется при открытии окна "Редактор запросов". Чтобы открыть окно "Редактор запросов", щелкните правой кнопкой мыши запись сервера и выберите команду **Создать запрос**или, если область **Обозреватель объектов** активна и в ее фокусе находится требуемый сервер, нажмите кнопку **Создать запрос** на панели инструментов.  
  
-   Если указан цвет для записи сервера на панели **Зарегистрированные серверы** , он используется при открытии окна редактора запросов. Чтобы открыть окно редактора запросов, щелкните правой кнопкой мыши запись сервера и выберите команду **Создать запрос**или, если область **Зарегистрированный сервер** активна и в ее фокусе находится требуемый сервер, нажмите кнопку **Создать запрос** на панели инструментов.  
  
-   В меню **Файл** после выбора команд **Создать** и **Запрос ядра СУБД**цвет, указанный в диалоговом окне **Соединение с сервером** , применяется к окну редактора запросов.  
  
**Сбросить все**  
Заменяет все значения введенных вручную свойств соединения значениями по умолчанию.  
  
**Соединить**  
Выполнить попытку соединения, используя значения из списка.  
  
**Параметры**  
Нажмите, чтобы изменить вид диалогового окна и скрыть дополнительные параметры соединения с сервером (такие как «Запомнить пароль»).  
  
**Проверить**  
При регистрации компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)] в списке **Зарегистрированные серверы**выберите этот параметр для проверки соединения.  
  
**Сохранить**  
Сохраняет параметры в списке **Зарегистрированные серверы**.  
  
## <a name="see-also"></a>См. также:  
[Диалоговое окно «Свойства соединения»](../../ssms/f1-help/connection-properties-dialog-box.md)  
  
