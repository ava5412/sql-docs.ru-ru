---
title: Диспетчер подключений Azure Data Lake Store | Документы Майкрософт
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSCM.F1
- SQL11.DTS.DESIGNER.AFPADLSCM.F1
ms.assetid: 7f1323f9-9dc3-4378-9c70-bbc65bfeabfd
caps.latest.revision: 5
author: yualan
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7786055b26bdc1ef2706dc54a9f74f975b42dafe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314314"
---
# <a name="azure-data-lake-store-connection-manager"></a>Диспетчер подключений Azure Data Lake Store
  **Диспетчер подключений Azure Data Lake Store** позволяет пакету служб SSIS подключаться к службе Azure Data Lake Store с помощью двух типов проверки подлинности: удостоверение пользователя Azure AD и удостоверение службы Azure AD.  

## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Настройка диспетчера подключений Azure Data Lake Store 
  
1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureDataLake**и щелкните **Добавить**.   
  
2.  В диалоговом окне "Редактор диспетчера подключений Azure Data Lake Store" введите URL-адрес узла Azure Data Lake Store в поле **Узел ADLS** . Например: https://test.azuredatalakestore.net или test.azuredatalakestore.net.
  
3.  Выберите соответствующий тип проверки подлинности для доступа к данным Azure Data Lake Store.

    1.  Если вы выбрали вариант **удостоверение пользователя Azure AD** , выполните следующие действия.

        1. Укажите значения в полях **Имя пользователя** и **Пароль** . 
    
        2. Щелкните **Проверить подключение** для проверки подключения. Если вы ранее не согласовали доступ служб SSIS к данным Azure Data Lake Store с администратором клиента, во всплывающем диалоговом окне нажмите кнопку **Принять** , чтобы разрешить службам SSIS доступ к данным Azure Data Lake Store. Дополнительные сведения о предоставлении согласия см. в разделе [Интеграция приложений с Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] 
        >   При выборе параметра проверки подлинности "Удостоверение пользователя Azure AD" многофакторная проверка подлинности и учетная запись Майкрософт НЕ поддерживаются.
    
    2.  Если вы выбрали вариант **удостоверение службы Azure AD** , выполните следующие действия.
        1. Создайте приложение AAD и субъект-службу, которые могут получать доступ к ресурсам Azure Data Lake.
    
        2. Назначьте приложению AAD соответствующие разрешения. Дополнительные сведения об этом параметре проверки подлинности см. в разделе [Использовать портал для создания приложения и службы-участника, который имеет доступ к ресурсам Active Directory](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).
    
        3. Укажите значения в полях **Идентификатор клиента**, **Секретный ключ** и **Имя клиента** .
    
        4. Щелкните **Проверить подключение** для проверки подключения.  
  
4.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
    Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .  
  
  
