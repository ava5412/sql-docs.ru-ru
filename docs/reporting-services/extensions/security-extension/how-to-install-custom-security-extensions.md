---
title: Как установить настраиваемые модули безопасности | Документы Майкрософт
ms.custom: ''
ms.date: 07/10/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa0a35b-ccfb-4279-bae6-106c227c5f16
caps.latest.revision: 3
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7b344fb4320af3ca9c4778740c6a5055481d6fce
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37971760"
---
# <a name="how-to-install-custom-security-extensions"></a>Как установить настраиваемые модули безопасности

[!INCLUDE[ssrs-appliesto](../../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../../includes/ssrs-appliesto-pbirs.md)]

В службах Reporting Services 2016 появился новый веб-портал для размещения новых API-интерфейсов Odata и новых рабочих нагрузок отчетов, например мобильных отчетов и ключевых показателей эффективности. На новом портале используются современные технологии, и он изолирован от известной службы Reporting Services, выполняясь в отдельном процессе. Этот процесс не является размещенным приложением ASP.NET и поэтому не подтверждает предположение относительно существующих пользовательских модулей безопасности. Кроме того, имеющиеся интерфейсы настраиваемых модулей безопасности не разрешают передачу внешнего контекста, поэтому у исполнителей остается только один вариант для проверки хорошо известных глобальных объектов ASP.NET, требующий внесения некоторых изменений в интерфейс.

## <a name="what-changed"></a>Что изменилось?

Появился новый доступный для реализации интерфейс, предоставляющий IRSRequestContext с дополнительными общими свойствами, используемыми модулями для принятия решений относительно проверки подлинности.

В предыдущих версиях диспетчер отчетов был интерфейсным и мог быть настроен с собственной страницей входа. В службах Reporting Services 2016 поддерживается только одна страница, размещенная на сервере отчетов, которая должна проходить проверку подлинности в обоих приложениях.

## <a name="implementation"></a>Реализация

В предыдущих версиях расширения могли полагаться на общие предположения, что объекты ASP.NET будут доступны. Так как новый портал не работает в ASP.NET, у модуля могут возникать проблемы с объектами, имеющими значение NULL.

Наиболее общим примером является доступ к HttpContext.Current для чтения сведений о запросе, таких как заголовки и файлы cookie. Чтобы модули могли принимать те же решения, мы представили новый метод в модуле, который предоставляет сведения о запросе и вызывается при проверке подлинности на портале. 

Для поддержки этого подхода модулям необходимо реализовать интерфейс <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension2>. Модули должны реализовать обе версии метода <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A>, так как он вызывается контекстом сервера отчетов, используемого в процессе webhost. В приведенном ниже примере показана одна из простых реализаций для портала, где используется удостоверение, разрешенное сервером отчетов.

``` 
public void GetUserInfo(IRSRequestContext requestContext, out IIdentity userIdentity, out IntPtr userId)
{
    userIdentity = null;
    if (requestContext.User != null)
    {
        userIdentity = requestContext.User;
    }

    // initialize a pointer to the current user id to zero
    userId = IntPtr.Zero;
}
```

## <a name="deployment-and-configuration"></a>Развертывание и конфигурация

Основные конфигурации, необходимые для настраиваемого модуля безопасности, совпадают с конфигурациями из предыдущих выпусков. Необходимо внести изменения в web.config и rsreportserver.config. Дополнительные сведения см. в разделе [Настройка нестандартной проверки подлинности или проверки подлинности с помощью форм на сервере отчетов](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md).

Больше нет отдельного файла web.config для диспетчера отчетов, портал будет наследовать те же параметры, что и конечная точка сервера отчетов.

## <a name="machine-keys"></a>Ключи компьютера

При использовании проверки подлинности на основе форм, когда требуется расшифровка файла cookie проверки подлинности, оба процесса необходимо настроить с помощью того же ключа компьютера и алгоритма расшифровки. Это действие было знакомо пользователям, которые раньше устанавливали службы Reporting Services для работы в средах с горизонтальным масштабированием. Сейчас это обязательное требование даже для развертываний на одном компьютере.

Следует использовать ключ проверки, соответствующий вашему развертыванию. Существует несколько средств для формирования ключей, например диспетчер служб IIS. Другие средства можно найти в Интернете.

### <a name="sql-server-reporting-services-2017-and-later"></a>Службы SQL Server Reporting Services 2017 и более поздние версии

**\ReportServer\rsReportServer.config**

Добавьте в `<configuration>`.

```
<machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

### <a name="sql-server-reporting-services-2016"></a>SQL Server Reporting Services 2016

**\ReportServer\web.config**

Добавьте в `<system.web>`.
    
```
    <machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

**\RSWebApp\Microsoft.ReportingServices.Portal.WebHost.exe.config**

Добавьте в `<configuration>`.

```
    <system.web>
        <machineKey validationKey=="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
    </system.web>
```

### <a name="power-bi-report-server"></a>Сервер отчетов Power BI

Доступен начиная с выпуска в июне 2017 г. (сборка 14.0.600.301).

**\ReportServer\rsReportServer.config**

Добавьте в `<configuration>`.

```
<machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

## <a name="configure-passthrough-cookies"></a>Настройка транзитных файлов cookie

Взаимодействие нового портала и сервера отчетов осуществляется через внутренние API-интерфейсы SOAP (аналогично предыдущей версии диспетчера отчетов). Если с портала на сервер необходимо передать дополнительные файлы cookie, можно по-прежнему воспользоваться свойствами PassThroughCookies. Дополнительные сведения см. в разделе [Настройка передачи файлов cookie для пользовательской проверки подлинности на веб-портале](../../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).

```
<UI>
   <CustomAuthenticationUI>
      <PassThroughCookies>
         <PassThroughCookie>sqlAuthCookie</PassThroughCookie>
      </PassThroughCookies>
   </CustomAuthenticationUI>
</UI>
```

## <a name="next-steps"></a>Следующие шаги

[Настройка нестандартной аутентификации или аутентификации с помощью форм на сервере отчетов](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md)  
[Настройка передачи файлов cookie для пользовательской проверки подлинности в диспетчере отчетов](https://msdn.microsoft.com/library/ms345241(v=sql.120).aspx)

Остались вопросы? [Посетите форум служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
