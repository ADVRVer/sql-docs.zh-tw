---
title: '! (邏輯 Not) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2199ea1bb78da37f309e59e7444aa77296a5a664
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437255"
---
# <a name="-logical-not-ssis-expression"></a>! (邏輯 Not) (SSIS 運算式)
  執行布林運算元的否定運算。  
  
> [!NOTE]  
>  ! 運算子不可搭配其他運算子使用。 例如，您不可以將 ! 及 > 運算子結合至 !>。 運算子。  
  
## <a name="syntax"></a>語法  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>引數  
 *boolean_expression*  
 是任何評估結果為布林的有效運算式。 如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。  
  
## <a name="result-types"></a>結果類型  
 DT_BOOL  
  
## <a name="remarks"></a>備註  
 下表顯示 ! 運算的結果 事件。  
  
|原始布林運算式|套用 ! 運算子之後|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>運算式範例  
 如果 **Color** 資料行的值為 「red」，則此範例會評估為 FALSE。  
  
```  
!(Color == "red")  
```  
  
 如果 **MonthNumber** 變數與代表目前月份的整數相同，則此範例的評估結果為 TRUE。 如需詳細資訊，請參閱 [MONTH &#40;SSIS 運算式&#41;](month-ssis-expression.md) 和 [GETDATE &#40;SSIS 運算式&#41;](getdate-ssis-expression.md)。  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序與關聯性](operator-precedence-and-associativity.md)   
 [運算子 &#40;SSIS 運算式&#41;](operators-ssis-expression.md)  
  
  
