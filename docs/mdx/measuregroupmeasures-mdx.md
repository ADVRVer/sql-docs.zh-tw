---
description: MeasureGroupMeasures (MDX)
title: MeasureGroupMeasures (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3adb11cd39e5a85e498f9b04ac714385d944c48a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483831"
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)


  傳回屬於指定量值群組的量值集合。  
  
## <a name="syntax"></a>語法  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>引數  
 *MeasureGroupName*  
 包含量值群組名稱的有效字串運算式，可從中擷取量值集合。  
  
## <a name="remarks"></a>備註  
 指定的字串必須完全符合量值群組名稱。 含空格的量值群組名稱不需要方括號。  
  
## <a name="example"></a>範例  
 下列範例會傳回 Adventure Works Cube 中 Internet Sales 量值群組的所有量值。  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
