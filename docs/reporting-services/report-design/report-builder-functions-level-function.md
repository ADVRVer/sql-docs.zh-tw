---
title: Level 函式 (報表產生器) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1e70847a25230be39166ac6fa489f1fdc3f23e43
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "77081245"
---
# <a name="report-builder-functions---level-function"></a>報表產生器函式 - Level 函式
  傳回遞迴階層中之目前所在的層級。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>語法  
  
```  
  
Level(scope)  
```  
  
#### <a name="parameters"></a>參數  
 *範圍 (scope)*  
 (**字串**) (選擇性)。 包含要套用彙總函式之報表項目的資料集、群組或資料區的名稱。 如果未指定 *scope* ，則使用目前的範圍。  
  
## <a name="return-type"></a>傳回類型  
 傳回 **Integer**。 如果 *scope* 指定資料集或資料區，或指定非遞迴群組 (亦即，沒有 **Parent** 元素的群組)， **Level** 會傳回 0。 如果省略 *scope* ，則會傳回目前範圍的層級。  
  
## <a name="remarks"></a>備註  
 **Level** 函數傳回的值是以零為基礎；亦即，階層中的第一個層級是 0。  
  
 **Level** 函數可以在遞迴階層 (例如員工清單) 中提供縮排。  
  
 如需遞迴階層的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例提供 Employees 群組中的資料列層級：  
  
```  
=Level("Employees")  
```  
  
## <a name="see-also"></a>另請參閱  
 [報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [運算式範例 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
