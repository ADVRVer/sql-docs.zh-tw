---
title: FLOOR (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f419fa11c27f912f9e020c83ec8c2164a7b4b13f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65725402"
---
# <a name="floor-ssis-expression"></a>FLOOR (SSIS 運算式)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  傳回小於或等於數值運算式的最大整數。  
  
## <a name="syntax"></a>語法  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>引數  
 *numeric_expression*  
 有效的數值運算式。  
  
## <a name="result-types"></a>結果類型  
 引數運算式的數值資料類型。 結果是計算值的整數部分，與 *numeric_expression*具有相同的資料類型。  
  
## <a name="remarks"></a>Remarks  
 如果引數為 Null，則 FLOOR 會傳回 Null 結果。  
  
## <a name="expression-examples"></a>運算式範例  
 這些範例會將 FLOOR 函數套用至正值、負值和零值。  
  
```  
FLOOR(123.45)  
```  
  
 傳回 123.00  
  
```  
FLOOR(-123.45)  
```  
  
 傳回 -124.00  
  
```  
FLOOR(0.00)  
```  
  
 傳回 0.00  
  
## <a name="see-also"></a>另請參閱  
 [CEILING &#40;SSIS 運算式&#41;](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
