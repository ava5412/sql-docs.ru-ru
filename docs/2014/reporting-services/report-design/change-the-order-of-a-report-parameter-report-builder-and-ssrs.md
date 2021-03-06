---
title: Изменение порядка параметров отчета (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 199b83364fceb93e59b9a1b32824166448a4c23f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191294"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Изменение порядка параметров отчета (построитель отчетов и службы SSRS)
  Изменять порядок параметров отчета необходимо в случае, если зависимый параметр расположен перед параметром, от которого он зависит. Порядок параметров имеет значение при наличии каскадных параметров или в случае, если необходимо показать пользователям значение по умолчанию одного параметра перед тем, как они выберут значения для других параметров. Зависимый параметр отчета ссылается (в своем запросе значений по умолчанию или в запросе допустимых значений) на параметр запроса, указывающий на параметр отчета, расположенный после него в списке параметров на панели данных отчета.  
  
 Порядок, в котором параметры отображаются на панели инструментов средства просмотра отчетов, определяется порядком параметров в области данных отчета.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a>Изменение порядка параметров отчета  
  
1.  В области данных отчета разверните узел «Параметры».  
  
2.  Щелкните параметр и используйте кнопки со стрелками вниз и вверх, расположенные на панели инструментов области данных отчета, чтобы переместить параметр выше или ниже в списке. На рисунке показана панель инструментов области данных отчета в построителе отчетов.  
  
     ![Область данных отчета](../media/reportdatapane.png "область данных отчета")  
  
## <a name="see-also"></a>См. также  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](report-parameters-report-builder-and-report-designer.md)   
 [Справка построителя отчетов для диалоговых окон, панелей и мастеров](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Добавление каскадных параметров в отчет &#40;построитель отчетов и службы SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Учебник. Добавление параметра к отчету (построитель отчетов)](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Добавление фильтров набора данных, фильтров области данных и групповых фильтров (построитель отчетов и службы SSRS)](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Ссылки на коллекцию параметров &#40;построитель отчетов и службы SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
