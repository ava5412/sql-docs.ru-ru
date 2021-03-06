---
title: Создание расширенных хранимых процедур | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- warnings [SQL Server]
- extended stored procedures [SQL Server], debugging
- extended stored procedures [SQL Server], creating
- messages [SQL Server], extended stored procedures
ms.assetid: 9f7c0cdb-6d88-44c0-b049-29953ae75717
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 21d29aa0ceb7ba16216db3f52e18379f55b775dd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32936598"
---
# <a name="creating-extended-stored-procedures"></a>Создание расширенных хранимых процедур
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Расширенная хранимая процедура является функцией с прототипом:  
  
 SRVRETCODE *xp_extendedProcName* **(** SRVPROC  **\*);**  
  
 Указание префикса xp_ необязательно. Имена расширенных хранимых процедур учитывают регистр символов, если на них ссылаются инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], независимо от установленной на сервере кодовой страницы и порядка сортировки. При создании DLL-библиотеки нужно сделать следующее.  
  
-   Если необходима точка входа, напишите функцию DllMain.  
  
     Эта функция необязательна. Если ее нет в исходном коде, то компилятор компонует собственную версию, которая всего лишь возвращает значение TRUE. Если функция DllMain создана, то операционная система вызывает ее в тот момент, когда поток или процесс присоединяется к DLL-библиотеке или отсоединяется от нее.  
  
-   Все функции, которые вызываются за пределами DLL-библиотеки (все расширенные хранимые процедуры и функции), должны быть экспортированы.  
  
     Функцию можно экспортировать, указав ее имя в разделе EXPORTS DEF-файла, или можно задать префикс имени функции в исходном коде с помощью __declspec(dllexport), расширение компилятора Майкрософт (Обратите внимание, что \__declspec() начинается с двух символов подчеркивания).  
  
 Для создания DLL-библиотеки расширенной хранимой процедуры необходимы следующие файлы.  
  
|Файл|Описание|  
|----------|-----------------|  
|Srv.h|Файл заголовка API-интерфейса расширенных хранимых процедур|  
|Opends60.lib|Библиотека импорта для Opends60.dll|  
  
 Чтобы создать DLL-библиотеку расширенной хранимой процедуры, создайте проект типа «Динамическая библиотека». Дополнительные сведения о создании DLL-библиотек см. в документации по среде разработки.  
  
 Настоятельно рекомендуется, чтобы все DLL-библиотеки расширенных хранимых процедур реализовали и экспортировали следующую функцию.  
  
```  
__declspec(dllexport) ULONG __GetXpVersion()  
{  
   return ODS_VERSION;  
}  
```  
  
> [!NOTE]  
>  Объявление __declspec(dllexport) является расширением компилятора Майкрософт. Если компилятор не поддерживает эту директиву, то функцию необходимо экспортировать в DEF-файле в раздел EXPORTS.  
  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается с трассировкой флаг - T260 или если пользователь с правами системного администратора запускает DBCC TRACEON (260), и если расширенная хранимая процедура DLL не поддерживает __GetXpVersion(), предупреждающее сообщение (ошибка 8131: расширенная хранимая процедура Библиотеки DLL «%» не экспортирует \__GetXpVersion().) выводится в журнале ошибок. (Обратите внимание, что \__GetXpVersion() начинается с двух символов подчеркивания.)  
  
 Если DLL-библиотека расширенной хранимой процедуры экспортирует __GetXpVersion(), но версия, возвращенная этой функцией, меньше, чем требует сервер, то в журнал ошибок заносится предупредительное сообщение, содержащее версию, возвращенную функцией, и версию, ожидаемую сервером. Если это сообщение возвращается неверное значение из \__GetXpVersion(), или выполняется компиляция со старой версией srv.h.  
  
> [!NOTE]  
>  Функция [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 SetErrorMode не должна вызываться в расширенных хранимых процедурах.  
  
 Долго выполняющимся расширенным хранимым процедурам рекомендуется периодически вызывать функцию srv_got_attention, чтобы процедура могла завершиться при разрыве соединения или аварийного завершения пакетов.  
  
 Для отладки расширенной DLL-библиотеки хранимой процедуры скопируйте ее в каталог [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn. Чтобы задать исполняемый файл для сеанса отладки, введите путь и имя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] исполняемый файл (например, C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Binn\Sqlservr.exe). Сведения об аргументах sqlservr см. в разделе [приложение sqlservr](../../tools/sqlservr-application.md).  
  
## <a name="see-also"></a>См. также  
 [srv_got_attention &#40;API расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
