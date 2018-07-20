---
title: Добавление в отчет ссылку на сборку (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
caps.latest.revision: 42
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 93f77d928916628ecb3ed5d11d4da49a3c8e61d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159955"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a>Добавление в отчет ссылку на сборку (службы SSRS)
  При внедрении пользовательского кода, содержащего ссылки на классы платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , не входящие в <xref:System.Math> или <xref:System.Convert>, необходимо предоставить в отчете ссылку на сборку, чтобы обработчик отчетов мог разрешать имена этих классов. Дополнительные сведения см. в разделе [Добавление кода в отчет (службы SSRS)](add-code-to-a-report-ssrs.md).  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a>Добавление в отчет ссылки на сборку  
  
1.  В режиме **конструктора** щелкните правой кнопкой мыши в области конструктора за границей отчета и выберите команду **Свойства отчета**.  
  
2.  Нажмите кнопку **Ссылки**.  
  
3.  В окне **Добавить или удалить сборки**нажмите кнопку **Добавить** и затем нажмите кнопку с многоточием, чтобы найти сборку.  
  
4.  В окне **Добавить или удалить классы**нажмите кнопку **Добавить** , а затем введите имя класса и предоставьте имя экземпляра для использования в отчете.  
  
    > [!NOTE]  
    >  Укажите имя класса и имя экземпляра только для элементов, зависимых от экземпляров. Не задавайте статические элементы в списке **Классы** . Дополнительные сведения см. в разделе [Пользовательский код и ссылки на сборки в выражениях в конструкторе отчетов (службы SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Использование пользовательских сборок с отчетами](../custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Диалоговое окно "Свойства отчета" — "Ссылки"](../report-properties-dialog-box-references.md)  
  
  