---
title: ABS (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0c6b28d311a3330bff063aa88f5a353186a9d1c1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437305"
---
# <a name="abs-ssis-expression"></a>ABS (SSIS 運算式)
  傳回數值運算式的絕對正數值。  
  
## <a name="syntax"></a>語法  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>引數  
 *numeric_expression*  
 是帶正負號或不帶正負號的數值運算式。  
  
## <a name="result-types"></a>結果類型  
 提交至函數之數值運算式的資料類型。  
  
## <a name="remarks"></a>備註  
 如果引數為 Null，則 ABS 會傳回 Null 結果。  
  
## <a name="expression-examples"></a>運算式範例  
 這些範例會將 ABS 函數套用至正數或負數。 兩者都傳回 1.23。  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 此範例會將 ABS 函數套用至減去 **HighTemperature** 和 **LowTempature**變數值的運算式。  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>另請參閱  
 [函數 &#40;SSIS 運算式&#41;](functions-ssis-expression.md)  
  
  
