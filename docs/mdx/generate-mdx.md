---
title: "產生 (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: GENERATE
dev_langs: kbMDX
helpviewer_keywords: Generate function
ms.assetid: 696a229d-c2f1-47b7-9dca-7b0a6b547d9b
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b64e0aca29625cf83021666c29b6306192e8b877
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="generate-mdx"></a>Generate (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  套用一個集合到另一個集合的每個成員，然後以聯集的方式將結果集聯結。 或者，針對集合進行字串運算式評估之後，傳回所產生的串連字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
Set expression syntax  
Generate( Set_Expression1 ,  Set_Expression2 [ , ALL ]  )  
  
String expression syntax  
Generate( Set_Expression1 ,  String_Expression [ ,Delimiter ]  )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression1*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Set_Expression2*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *String_Expression*  
 有效的字串運算式，這通常是指定集合中每個 Tuple 的目前成員名稱 (CurrentMember.Name)。  
  
 *分隔符號*  
 以字串運算式表示的有效分隔符號。  
  
## <a name="remarks"></a>備註  
 如果未指定第二個集合，則**產生**函式會傳回第二個集合的 tuple 套用第一個集合中的每個 tuple 所產生的集合*，*和聯集，然後將聯結所產生的設定。 如果**所有**指定，則此函式會保留在結果集中的重複項。  
  
 如果指定的字串運算式，則**產生**函式會傳回產生評估指定的字串運算式，對每個 tuple 中第一個集合的字串*，*然後串連結果。 另外，也可以選擇字串分隔符號，在產生的串連字串中分隔每個結果。  
  
## <a name="examples"></a>範例  
  
### <a name="set"></a>將  
 在以下範例中，查詢會傳回包含 Measure Internet Sales 數量四次的集合，因為 [Date].[Calendar Year].[Calendar Year].MEMBERS 集合中有四個成員：  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]}, ALL)  
ON 0  
FROM [Adventure Works]  
```  
  
 移除 ALL 會變更此查詢，好讓 Internet Sales Amount 只傳回一次：  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]})  
ON 0  
FROM [Adventure Works]  
```  
  
 最常見的實際使用**產生**評估複雜設定成員的集合運算式，例如 TopCount。 下列範例查詢會針對資料列上的每一個 Calendar Year 顯示前 10 大產品：  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS  
, TOPCOUNT(  
[Date].[Calendar Year].CURRENTMEMBER  
*  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount]))  
ON 1  
FROM [Adventure Works]  
```  
  
 請注意，不同的前 10 個會顯示每年，而且使用**產生**是為得到此結果的唯一方式。 只是交叉聯結 Calendar Years 以及前 10 大產品集合將會顯示所有年度的前 10 大產品，每一年都會重複，如以下範例所示：  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS  
*   
TOPCOUNT(  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount])  
ON 1  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>字串  
 下列範例示範使用**產生**傳回的字串：  
  
```  
WITH   
MEMBER MEASURES.GENERATESTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME)  
MEMBER MEASURES.GENERATEDELIMITEDSTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME, " AND ")  
SELECT   
{MEASURES.GENERATESTRINGDEMO, MEASURES.GENERATEDELIMITEDSTRINGDEMO}  
ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  這種形式的**產生**函式有助於進行偵錯計算，因為它可讓您傳回一個字串來顯示集合中所有成員的名稱。 這可能是一組的嚴格 MDX 表示比閱讀， [SetToStr &#40;MDX &#41;](../mdx/settostr-mdx.md)函式會傳回。  
  
## <a name="see-also"></a>請參閱＜  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
