---
title: "常用的篩選 （報表產生器及 SSRS） |Microsoft 文件"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multivalued parameters [Reporting Services]
- single-valued parameters [Reporting Services]
- parameters [Reporting Services], multivalued
- valid values [Reporting Services]
ms.assetid: cb70d0cd-707b-4de5-b39f-e4eb57d316aa
caps.latest.revision: 36
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6d41e46b2fb9f9dc9016d04254ef289fe4a44372
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="commonly-used-filters-report-builder-and-ssrs"></a>常用的篩選 (報表產生器及 SSRS)
  若要建立篩選，您必須指定一個或多個篩選方程式。 篩選方程式包含運算式、資料類型、運算子和值。 本主題提供常用的篩選範例。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>篩選範例  
 下表說明使用不同資料類型和不同運算子的篩選方程式範例。 比較的範圍是由定義篩選的報表項目所決定。 例如，如果是資料集上所定義的篩選， **TOP % 10** 就是資料集中前百分之 10 的值；如果是群組上所定義的篩選， **TOP % 10** 就是群組中前百分之 10 的值。  
  
|簡單運算式|資料類型|運算子|Value|說明|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|**Integer**|**>**|`7`|包含大於 7 的資料值。|  
|`[SUM(Quantity)]`|**Integer**|**TOP N**|`10`|包含前 10 大資料值。|  
|`[SUM(Quantity)]`|**Integer**|**TOP %**|`20`|包含前百分之 20 的資料值。|  
|`[Sales]`|**Text**|**>**|`=CDec(100)`|包含所有大於 $100 之 System.Decimal 類型 (SQL "money" 資料類型) 的值。|  
|`[OrderDate]`|**DateTime**|**>**|`2088-01-01`|包含從 2008 年 1 月 1 日到目前的所有日期。|  
|`[OrderDate]`|**DateTime**|**BETWEEN**|`2008-01-01`<br /><br /> `2008-02-01`|包含從 2008 年 1 月 1 日 (含) 算起的日期。|  
|`[Territory]`|**Text**|**LIKE**|`*east`|所有以 "east" 結尾的領域名稱。|  
|`[Territory]`|**Text**|**LIKE**|`%o%th*`|所有在名稱開頭包含 North 和 South 的領域名稱。|  
|`=LEFT(Fields!Subcat.Value,1)`|**Text**|**IN**|`B, C, T`|所有以字母 B、C 或 T 為開頭的子類別目錄值。|  
  
## <a name="examples-with-report-parameters"></a>報表參數的範例  
 下表提供篩選運算式的範例，其中包含了單一值或多重值的參數參考。  
  
|參數類型|(篩選) 運算式|運算子|Value|資料類型|  
|--------------------|---------------------------|--------------|-----------|---------------|  
|單一值|`[EmployeeID]`|=|`[@EmployeeID]`|Integer|  
|多重值|`[EmployeeID]`|IN|`[@EmployeeID]`|Integer|  
  
## <a name="see-also"></a>請參閱＜  
 [報表參數 &#40;報表產生器和報表設計師&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [新增資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [運算式範例 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)  
  
  
