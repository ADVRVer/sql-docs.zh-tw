---
title: "EXISTING 關鍵字 (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5078aa14be3c476e8b89545ed1541f12b7686f4e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-query---existing-keyword"></a>MDX 查詢-EXISTING 關鍵字
  強制在目前內容內評估指定的集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 有效的多維度運算式 (MDX) 集合運算式。  
  
## <a name="remarks"></a>備註  
 根據預設，會在包含集合成員的 Cube 內容內評估集合。 但是 **Existing** 關鍵字會強制在目前的內容內評估指定的集合。  
  
## <a name="example"></a>範例  
 下列範例會根據使用 **Aggregate** 函數評估之使用者選取的 State-Province 成員值，傳回上一個時間週期銷售值衰退的轉售商計數。 但是 [Hierarchize &#40;MDX&#41;](../../../mdx/hierarchize-mdx.md) 和 [DrilldownLevel (MDX)](../../../mdx/drilldownlevel-mdx.md) 函數是用來傳回 Product 維度中產品類別目錄的衰退銷售值。 **Existing** 關鍵字會強制 **Filter** 函數中的集合在目前內容中評估，亦即針對 State-Province 屬性階層的 Washington 和 Oregon 成員。  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a>請參閱＜  
 [Count &#40;集合&#41; &#40;MDX&#41;](../../../mdx/count-set-mdx.md)   
 [AddCalculatedMembers &#40;MDX &#41;](../../../mdx/addcalculatedmembers-mdx.md)   
 [彙總 &#40;MDX &#41;](../../../mdx/aggregate-mdx.md)   
 [篩選 &#40;MDX &#41;](../../../mdx/filter-mdx.md)   
 [屬性 &#40;MDX &#41;](../../../mdx/properties-mdx.md)   
 [DrilldownLevel &#40;MDX &#41;](../../../mdx/drilldownlevel-mdx.md)   
 [Hierarchize &#40;MDX &#41;](../../../mdx/hierarchize-mdx.md)   
 [MDX 函數參考 &#40;MDX &#41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  

