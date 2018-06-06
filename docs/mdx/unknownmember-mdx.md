---
title: UnknownMember (MDX) |Microsoft 文件
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b74454c00f48a36b963e6c7f5b7b1bdf4e2ea44e
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582210"
---
# <a name="unknownmember-mdx"></a>UnknownMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  傳回與層級或成員相關的未知的成員。  
  
## <a name="syntax"></a>語法  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## <a name="arguments"></a>引數  
 *Member_Expression*  
 傳回成員的有效多維度運算式 (MDX) 運算式。  
  
 *Hierarchy_Expression*  
 傳回階層的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 建立事實資料表資料與階層產生關聯，當在階層未知時未知的成員。 未知的成員可位於以下其中一個層級：  
  
-   無法彙總之屬性階層的最上層。  
  
-   在第一個層級下面的**所有**自然階層的層級。  
  
-   非自然階層的任何層級。  
  
 如果指定成員運算式，則**UnknownMember**函式會傳回指定成員的未知的成員子系。 如果指定的成員不存在，此函數會傳回 Null。  
  
 如果指定了階層運算式， **UnknownMember**函式會傳回未知的成員在最上層，如果有的話。  
  
 如果不存在未知的成員，這是層級或成員， **UnknownMember**函式會建立 null 成員。  
  
> [!NOTE]  
>  如果階層或成員上沒有未知的成員存在，就會產生一個錯誤。  
  
## <a name="examples"></a>範例  
 下列範例會為 Measures 維度的所有成員傳回 Product 屬性階層中 All Products 成員的未知成員。  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 下列範例會為 Measures 維度的所有成員傳回 Product Categories 階層的未知成員。  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
