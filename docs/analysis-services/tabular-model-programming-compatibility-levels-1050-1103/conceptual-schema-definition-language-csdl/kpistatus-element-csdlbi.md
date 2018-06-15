---
title: KpiStatus 元素 (CSDLBI) |Microsoft 文件
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd4766295a985948572ce17702a86d3e53adb747
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34042412"
---
# <a name="kpistatus-element-csdlbi"></a>KpiStatus 元素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  KpiStatus 元素會定義包含在關鍵效能指標 (KPI) 中當做狀態指標使用之值的資料行參考。  
  
## <a name="elements-and-attributes"></a>元素和屬性  
 下表列出定義 KpiStatus 元素的元素和屬性。  
  
|名稱|是否必要|說明|  
|----------|-----------------|-----------------|  
|PropertyRef|是|包含在 KPI 中當做狀態指標使用之值的資料行參考。<br /><br /> 此元素「必須」只包含單獨一個資料行參考，如 TPropertyRefcomplex 類型所定義。|  
  
## <a name="example"></a>範例  
 **表格式**  
  
 下列 CSDLBI 1.1 版中的範例顯示 AdventureWorks 表格式模型範例中的 KPI。 KpiStatus 元素會參考包含值的資料行 (表示為 PropertyRef)。  
  
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
  
## <a name="example"></a>範例  
 **多維度**  
  
 下列 CSDLBI 1.1 版中的範例會顯示來自 Contoso Operations Cube 的 KPI。 KpiStatus 元素會參考計算 KPI 狀態值的量值。  
  
```  
<bi:Measure   
       Caption="Sum of SalesAmount"   
       ReferenceName="Sum of SalesAmount"   
       FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
  
    <bi:Kpi   
       StatusGraphic="Three Circles Colored">  
  
      <bi:KpiGoal>  
         <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Goal" />  
       </bi:KpiGoal>  
  
       <bi:KpiStatus>  
          <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Status" />  
        </bi:KpiStatus>  
  
       </bi:Kpi>  
</bi:Measure>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [KPI 元素 & #40;CSDLBI & #41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)  
  
  
