---
title: Predict （MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 165d03b886ad8e9beeb09bf5a835c879cc23a2a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055581"
---
# <a name="predict-mdx"></a>Predict (MDX)


    
> [!CAUTION]  
>  這個函式位於由於內部不一致而移除的處理序中。  
>   
>  請檢閱＜範例＞一節中使用 DMX 運算式的解決方法。  
  
 傳回數值運算式在某個資料採擷模型上所評估出的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>引數  
 *Mining_Model_Name*  
 代表採礦模型名稱的有效字串運算式。  
  
 *String_Expression*  
 評估為指定採礦模型之有效 DMX 運算式的有效字串運算式。  
  
## <a name="remarks"></a>備註  
 **Predict**函式會在指定之「採礦模型」的內容中評估指定的字串運算式。  
  
 資料採礦語法及函數的相關文件，記錄於資料採礦運算式 (DMX) 參考中。  
  
## <a name="example"></a>範例  
 下列範例使用客戶群集採礦模型來預測群集名稱，以及特定客戶與群集的距離：  
  
```  
WITH MEMBER MEASURES.CLNAME AS   
PREDICT("Customer Clusters", "Cluster()")  
MEMBER MEASURES.CLDISTANCE AS   
PREDICT("Customer Clusters", "ClusterDistance(Cluster())")  
SELECT {MEASURES.CLNAME, MEASURES.CLDISTANCE} ON 0   
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Customer].&[12012])  
```  
  
## <a name="see-also"></a>另請參閱  
 [Mdx 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
