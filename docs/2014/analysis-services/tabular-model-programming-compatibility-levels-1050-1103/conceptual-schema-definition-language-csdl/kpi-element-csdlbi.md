---
title: Элемент KPI (CSDLBI) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 203ee6e8-eef2-4476-b09f-bd95e492ddaa
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a649ffffe6f2d9f5902ede9e6d7a6126fd09e25
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155085"
---
# <a name="kpi-element-csdlbi"></a>Элемент KPI (CSDLBI)
  В элементе Kpi определяется вычисление, которое может быть использовано в качестве ключевого показателя эффективности (KPI). В модели данных бизнес-аналитики ключевые показатели эффективности (KPI) основаны на мерах, поэтому определение KPI содержит все метаданные, связанные с мерами, а также сведения, необходимые для представления значений KPI, в том числе рисунок по умолчанию.  
  
 В элементе Kpi не указывается формула, содержащаяся в определении меры, однако указаны дополнительные метаданные, связанные с мерами, используемыми в качестве ключевых показателей эффективности. Обозначив меру в качестве ключевого показателя эффективности, уже нельзя использовать ее в других контекстах.  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 В следующей таблице перечислены элементы и атрибуты, определяющие элемент ключевого показателя эффективности.  
  
|Имя|Обязателен|Описание|  
|----------|-----------------|-----------------|  
|Документация|Нет|Описание ключевого показателя эффективности.|  
|KpiGoal|Да|Ссылка на столбец, содержащий значения, которые могут быть использованы в качестве цели.<br /><br /> См. раздел [Элемент PropertyRef (CSDLBI)](propertyref-element-csdlbi.md).|  
|KpiStatus|Да|Ссылка на столбец, содержащий значения, которые представляют текущее состояние ключевого показателя эффективности.|  
|StatusGraphic|Да|Ссылка на изображение, которое указывает на отрицательный, нейтральный или положительный результат выполнения с учетом целей, определенных в качестве ключевого показателя эффективности.|  
  
## <a name="remarks"></a>Примечания  
 При разработке модели можно создать ключевой показатель эффективности,, создав меру и назначив ее в качестве ключевого показателя эффективности. Затем добавляются сведения, относящиеся к ключевым показателям эффективности, например рисунок, который используется при отображении трендов.  
  
## <a name="example"></a>Пример  
 **Табличный**  
  
 В следующем примере CSDLBI версии1.0 представлен ключевой показатель эффективности, с помощью которого измеряются продажи. Пример взят из образца табличной модели AdventureWorks.  
  
```  
  
<Property Name="InternetCurrSalesPerf" Type="Double">  
  <bi:Measure>  
    <bi:Kpi StatusGraphic="Three Stars Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>Пример  
 **Multidimensional**  
  
 В следующем примере для CSDLBI версии 1.1 показан ключевой показатель эффективности из куба операций Contoso.  
  
```  
<Property Name="Sum_of_SalesAmount" Type="Decimal" Precision="19" Scale="4">  
   <Documentation>  
     <Summary>KPI Description</Summary>  
   </Documentation>  
     <bi:Measure   
         Caption="Sum of SalesAmount"   
         ReferenceName="Sum of SalesAmount"   
         FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
     <bi:Kpi   
           StatusGraphic="Three Circles Colored">  
         <bi:KpiGoal>  
            <bi:PropertyRef Name="v_Sum_of_SalesAmount_Goal" />  
          </bi:KpiGoal>  
          <bi:KpiStatus>  
              <bi:PropertyRef Name="v_Sum_of_SalesAmount_Status" />  
          </bi:KpiStatus>  
     </bi:Kpi>  
     </bi:Measure>  
</Property>  
```  
  
## <a name="see-also"></a>См. также  
 [Технический справочник по аннотациям бизнес-аналитики для языка CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
