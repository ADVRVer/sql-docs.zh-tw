---
title: "LookupCube (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: LOOKUPCUBE
dev_langs: kbMDX
helpviewer_keywords: LookupCube function
ms.assetid: 243fa101-328a-4016-86e0-d8b5977e15a9
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ecd1810908dfda4d3e9f4e8c36d4c35ba6e37185
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="lookupcube-mdx"></a>LookupCube (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在評估過相同資料庫中其他指定的 Cube 之後，傳回多維度運算式 (MDX) 運算式的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
Numeric expression syntax  
LookupCube(Cube_Name, Numeric_Expression )  
  
String expression syntax  
LookupCube(Cube_Name, String_Expression )  
```  
  
## <a name="arguments"></a>引數  
 *Cube_Name*  
 指定 Cube 名稱的有效字串運算式。  
  
 *Numeric_Expression*  
 有效的數值運算式，這通常是傳回數字之資料格座標的多維度運算式 (MDX) 運算式。  
  
 *String_Expression*  
 有效的字串運算式，這通常是傳回字串之資料格座標的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 如果指定數值運算式， **LookupCube**函式評估指定的數值運算式所指定 cube 中，並傳回結果的數值。  
  
 如果指定的字串運算式，則**LookupCube**函式評估指定的 cube 中的指定的字串運算式，並傳回結果的字串值。  
  
 **LookupCube**函數所在之 MDX 查詢的來源 cube 包含適用於在相同資料庫內的 cube 上**LookupCube**函式的執行。  
  
> [!IMPORTANT]  
>  您必須在數值或字串運算式中提供任何必要的目前成員，因為目前查詢的內容不會延續至所查詢的 Cube。  
  
 任何計算使用**LookupCube**函式都可能會發生效能不彰。 請考慮重新設計方案，讓所有必要資料出現在一個 Cube 中，而不要使用這個函數。  
  
## <a name="examples"></a>範例  
 下列查詢會示範 LookupCube 的使用：  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>請參閱＜  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
