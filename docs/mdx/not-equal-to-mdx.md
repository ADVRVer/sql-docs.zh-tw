---
title: "&lt;&gt;（不等於）(MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <>
dev_langs: kbMDX
helpviewer_keywords:
- not equal to operator (<>)
- <> (not equal to operator)
ms.assetid: b4eb3f1c-8b68-4530-a8f3-e3b8414ac789
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 36e366f4dc72b540ce3ba70e12fadc6d9a99aadf
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt;（不等於）(MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  執行比對作業，判定某個多維度運算式 (MDX) 運算式的值是否不等於另一個 MDX 運算式的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
MDX_Expression <> MDX_Expression  
```  
  
#### <a name="parameters"></a>參數  
 *MDX_Expression*  
 有效的 MDX 運算式。  
  
## <a name="return-value"></a>傳回值  
 布林值根據以下條件而定：  
  
-   **true**如果這兩個參數都為非 null，而且第一個參數不等於第二個參數。  
  
-   **false**如果這兩個參數都為非 null，而且第一個參數等於第二個參數。  
  
-   Null，如果有一個參數或兩個參數都評估為 Null 值。  
  
## <a name="see-also"></a>請參閱＜  
 [MDX 運算子參考 &#40;MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
