---
title: 聯集 (MDX) |Microsoft 文件
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7712e1f925aa514ec059a88d46db05d337f0c140
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582230"
---
# <a name="union--mdx"></a>聯集 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  傳回兩個集合的聯集而產生的集合，可選擇性地保留重複的成員。  
  
## <a name="syntax"></a>語法  
  
```  
  
Standard syntax  
Union(Set_Expression1, Set_Expression2 [,...n][, ALL])  
  
Alternate syntax 1  
Set_Expression1 + Set_Expression2 [+...n]  
  
Alternate syntax 2  
{Set_Expression1 , Set_Expression2 [,...n]}  
```  
  
## <a name="arguments"></a>引數  
 *設定運算式 1*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *集合運算式 2*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 此函式傳回的聯集兩個或多個指定集合 *。* 搭配標準語法和替代語法 1，預設會刪除重複項目。 搭配標準語法時，使用**所有**旗標會在聯結集合中保留重複項。 從集合結尾刪除重複項。 使用替代語法 2 時，一律會保留重複項。  
  
## <a name="examples"></a>範例  
 下列範例示範的行為**Union**函式使用每個語法。  
  
### <a name="standard-syntax-duplicates-eliminated"></a>標準語法，刪除重複項  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="standard-syntax-duplicates-retained"></a>標準語法，保留重複項  
  
```  
SELECT Union   
   ([Date].[Calendar Year].children  
   , {[Date].[Calendar Year].[CY 2002]}  
   , {[Date].[Calendar Year].[CY 2003]}  
   , ALL  
   ) ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-1-duplicates-eliminated"></a>替代語法 1，刪除重複項  
  
```  
SELECT   
   [Date].[Calendar Year].children   
   + {[Date].[Calendar Year].[CY 2002]}   
   + {[Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
### <a name="alternate-syntax-2-duplicates-retained"></a>替代語法 2，保留重複項  
  
```  
SELECT   
   {[Date].[Calendar Year].children  
   , [Date].[Calendar Year].[CY 2002]  
   , [Date].[Calendar Year].[CY 2003]} ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [+ &#40;Union&#41; &#40;MDX&#41;](../mdx/union-mdx-operator-reference.md)   
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
