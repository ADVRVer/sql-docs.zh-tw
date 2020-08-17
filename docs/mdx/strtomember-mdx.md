---
description: StrToMember (MDX)
title: StrToMember (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 68d2d99bb51412a98919d1ab1626c7a86bd86245
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386804"
---
# <a name="strtomember-mdx"></a>StrToMember (MDX)


  傳回多維度運算式所指定的成員， (MDX) 格式的字串。  
  
## <a name="syntax"></a>語法  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>引數  
 *Member_Name*  
 直接或間接指定成員的有效字串運算式。  
  
## <a name="remarks"></a>備註  
 **StrToMember**函數會傳回字串運算式中指定的成員。 **StrToMember**函數通常會搭配使用者自訂函數使用，以將外部函數的成員規格傳回至 mdx 語句，或在 mdx 查詢參數化時使用。  
  
-   使用 CONSTRAINED 旗標時，成員名稱必須可直接解析成合格的或不合格的成員名稱。 這個旗標用於降低遭到由指定字串發動資料隱碼攻擊的風險。 如果所提供的字串不能直接解析成限定或未限定成員名稱，會出現下列錯誤：「違反了 STRTOMEMBER 函數中 CONSTRAINED 旗標所加諸的限制。」  
  
-   沒有使用 CONSTRAINED 旗標時，指定的成員可以直接解析為成員名稱，或解析成會解析成名稱的 MDX 運算式。  
  
-   若要進一步了解集合和成員之間的差異，請參閱＜使用集合運算式＞和＜使用成員運算式＞。  
  
## <a name="examples"></a>範例  
 下列範例會使用 **StrToMember** 函數，傳回 [省份] 屬性階層中 Bayern 成員的 [轉售商銷售量] 量值。 指定的字串提供了限定成員名稱。  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 下列範例會使用 **StrToMember** 函數，傳回 Bayern 成員的轉售商銷售量量值。 因為成員名稱字串只提供不合格的成員名稱，所以查詢會傳回指定成員的第一個執行個體，這正好是在 Customer 維度的 Customer Geography 階層中，與 Reseller Sales 沒有交集。 最佳做法應規定指定合格的名稱，以確保預期的結果。  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 下列範例會使用 **StrToMember** 函數，傳回 [省份] 屬性階層中 Bayern 成員的 [轉售商銷售量] 量值。 所提供的成員名稱字串會解析成合格的成員名稱。  
  
```  
SELECT {StrToMember('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 下列範例傳回因為 CONSTRAINED 旗標而發生的錯誤。 雖然所提供的成員名稱字串包含會解析成限定成員名稱的有效 MDX 成員運算式，但 CONSTRAINED 旗標要求成員名稱字串中包含限定或未限定成員名稱。  
  
```  
SELECT StrToMember ('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
