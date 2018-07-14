---
title: SQRT (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e9e871242572df1f66faa1cbf19c948e0be6f1c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271484"
---
# <a name="sqrt-ssis-expression"></a>SQRT (SSIS 運算式)
  傳回數值運算式的平方根。  
  
## <a name="syntax"></a>語法  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a>引數  
 *numeric_expression*  
 任何數值資料類型的數值運算式。 如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。  
  
## <a name="result-types"></a>結果類型  
 DT_R8  
  
## <a name="remarks"></a>備註  
 如果引數為 Null，則 SQRT 會傳回 Null 結果。  
  
 如果引數是負值，SQRT 將會失敗。  
  
 引數會在進行平方根運算之前，轉換成 DT_R8 資料類型。  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會傳回數值常值的平方根。 傳回結果為 12。  
  
```  
SQRT(144)  
```  
  
 此範例會傳回運算式的平方根，亦即 **Value1** 和 **Value2** 資料行中的值相減的結果。  
  
```  
SQRT(Value1 - Value2)  
```  
  
 此範例會將 SQUARE 函數套用至兩個變數，然後計算其總和的平方根，藉此傳回直角三角形第三邊的長度。 如果 **Side1** 包含 3，而 **Side2** 包含 4，SQRT 函數就會傳回 5。  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  在運算式中，變數名稱會固定包含 @ 前置字元。  
  
## <a name="see-also"></a>另請參閱  
 [函式&#40;SSIS 運算式&#41;](functions-ssis-expression.md)  
  
  
