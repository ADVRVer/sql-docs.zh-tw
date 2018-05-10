---
title: 除 (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2fa7251d0b809f1c02885409a9cd9b08e6fd43ae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="divide-ssis-expression"></a>Divide (SSIS 運算式)
  將第一個數值運算式除以第二個數值運算式。  
  
## <a name="syntax"></a>語法  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>引數  
 *dividend*  
 要執行除法的數值運算式。 *dividend* 可以是任何有效的數值運算式。 如需詳細資訊，請參閱＜ [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)＞。  
  
 *divisor*  
 要除以被除數的數值運算式。 *divisor* 可以是任何有效的數值運算式 (零除外)。  
  
## <a name="result-types"></a>結果類型  
 由兩個引數的資料類型決定。 如需相關資訊，請參閱 [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md)。  
  
## <a name="remarks"></a>Remarks  
 如果任一個運算元為 Null，則結果為 Null。  
  
 除以零並不合法。 根據如何評估 *divisor* 子運算式而定，會發生下列其中一項錯誤：  
  
-   如果評估為零的 *divisor* 子運算式是常數，則會在設計階段出現錯誤，導致運算式驗證失敗。  
  
-   如果評估為零的 *divisor* 子運算式含有變數，但沒有輸入資料行，則在封裝執行之前發生的運算式所屬元件的前置執行驗證便會失敗。  
  
-   如果評估為零的 *divisor* 子運算式含有輸入資料行，則會在執行階段出現錯誤，並根據資料流程元件的錯誤流程規則處理該錯誤。  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會執行兩個數值常值的除法。  
  
```  
25 / 5  
```  
  
 此範例會將 **ListPrice** 資料行中的值除以 **StandardCost** 資料行中的值。  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序與關聯性](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [運算子 &#40;SSIS 運算式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
