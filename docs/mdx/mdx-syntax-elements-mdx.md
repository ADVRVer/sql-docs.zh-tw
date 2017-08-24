---
title: "MDX 語法元素 (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], syntax
- MDX [Analysis Services], syntax
ms.assetid: f4c16e1a-cf1a-4be0-839a-db018430ff14
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 77aab8ddf130fc7f93cecfe762833bbda873c81a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-syntax-elements-mdx"></a>MDX 語法元素 (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  多維度運算式 (MDX) 有大多數陳述式使用或受其影響的幾個語法元素：  
  
|詞彙|定義|  
|----------|----------------|  
|[識別項](../mdx/identifiers-mdx.md)|識別碼是物件的名稱，例如 Cube、維度、成員及量值。|  
|**資料類型**|定義資料格、成員屬性及資料格屬性包含的資料類型。 MDX 只能支援 OLE VARIANT 資料類型。 如需強制型轉、轉換及操作 VARIANT 資料類型的詳細資訊，請參閱 Platform SDK 文件集中的＜VARIANT 與 VARIANTARG＞。|  
|[運算式 &#40;MDX &#41;](../mdx/expressions-mdx.md)|運算式是的語法單位的[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]可解析成單一 （純量） 值或物件。 運算式包括傳回單一值、集合運算式等等的函數。|  
|[運算子](../mdx/operators-mdx-syntax.md)|運算子是語法元素，可與一個或多個簡單 MDX 運算式一起使用，構成多個複雜 MDX 運算式。|  
|[函式](../mdx/functions-mdx-syntax.md)|函數是語法元素，可接受零個、一個或多個輸入值，然後傳回純量值或物件。 範例包括[總和](../mdx/sum-mdx.md)函式，將幾個數值，[成員](../mdx/members-set-mdx.md)維度或層級，從傳回一組成員函式等等。|  
|[註解](../mdx/comments-mdx-syntax.md)|註解是插入 MDX 陳述式中的文字或說明陳述式用途的指令碼。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]不會執行註解。|  
|[保留的關鍵字](../mdx/reserved-keywords-mdx-syntax.md)|保留關鍵字是保留起來以供 MDX 使用的單字，而且不應該在 MDX 陳述式中作為物件名稱使用。|  
|[成員、 Tuple 和集合](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)|成員、Tuple 及集合是多維度資料的核心概念，您必須先了解此概念，然後才能著手建立 MDX 查詢。|  
  
## <a name="see-also"></a>另請參閱  
 [多維度運算式 &#40;MDX &#41;參考](../mdx/multidimensional-expressions-mdx-reference.md)  
  
  

