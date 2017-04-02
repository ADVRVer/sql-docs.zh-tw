---
title: "RowNumber 函數 (報表產生器及 SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# RowNumber 函數 (報表產生器及 SSRS)
  傳回指定範圍中資料列數的執行計數。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 語法  
  
```  
  
RowNumber(scope)  
```  
  
#### 參數  
 *範圍 (scope)*  
 (**字串**) 資料集、資料區或群組的名稱，或為 Null (在 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 中為 **Nothing**)，指定要在其中評估資料列數的內容。 **Nothing** 指定最外層的內容，這通常為報表資料集。  
  
## 備註  
 **RowNumber** 會傳回指定範圍內資料列計數的執行值，如同 [RunningValue](../../reporting-services/report-design/runningvalue-function-report-builder-and-ssrs.md) 傳回彙總函式的執行值一樣。 當您指定範圍時，可以指定何時要將資料列計數重設為 1。  
  
 *scope* 不可為運算式。 *scope* 必須是包含範圍。 就一般範圍而言，從最外層到最內層的內含項目依序為報表資料集、資料區域、資料列群組或資料行群組。  
  
 若要在全部資料行中累加值，請將範圍指定為資料行群組的名稱。 若要在資料列中向下累加數目，請將範圍指定為資料列群組的名稱。  
  
> [!NOTE]  
>  不支援在單一運算式中包含同時指定資料列群組和資料行群組的彙總。  
  
 如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)。  
  
## 程式碼範例  
 下列的運算式可用於 Tablix 資料區域詳細資料列的 **BackgroundColor** 屬性，以改變每個群組的詳細資料列色彩 (永遠從白色開始)。  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## 請參閱＜  
 [報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [運算式範例 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  