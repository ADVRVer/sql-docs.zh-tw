---
title: "CalculationCurrentPass (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CALCULATIONCURRENTPASS
dev_langs:
- kbMDX
helpviewer_keywords:
- CalculationCurrentPass function
ms.assetid: 7069f7a0-8ec8-4293-8db3-b35b9327f437
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f2510f0db6f5a2895ce00514595306ac4849b357
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="calculationcurrentpass-mdx"></a>CalculationCurrentPass (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回 Cube 目前的計算行程 (給特定的查詢內容)。  
  
## <a name="syntax"></a>語法  
  
```  
  
CalculationCurrentPass()  
```  
  
## <a name="remarks"></a>備註  
 **CalculationCurrentPass**函式會傳回目前查詢內容的計算行程的以零為起始的索引。 使用自動遞迴解析功能[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，此函式具有不具實用性。  
  
## <a name="see-also"></a>另請參閱  
 [CalculationPassValue &#40;MDX &#41;](../mdx/calculationpassvalue-mdx.md)   
 [IIf &#40;MDX &#41;](../mdx/iif-mdx.md)   
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

