---
title: "() (括號) (SSIS 運算式) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ae024cc0a4d8a492175ac992ed82eed34956848
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="-parentheses-ssis-expression"></a>() (括號) (SSIS 運算式)
  識別運算式的評估順序。 加上括號的運算式擁有最高的評估優先順序。 加上括號的巢狀運算式會以由內向外的順序評估。  
  
 括號還可用來讓複雜的運算式更易於了解。  
  
## <a name="syntax"></a>語法  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 任何有效的運算式。  
  
## <a name="result-types"></a>結果類型  
 *expression*的資料類型。 如需相關資訊，請參閱 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)。  
  
## <a name="expression-examples"></a>運算式範例  
 此範例示範使用括號修改運算子之優先順序的方式。 第一個運算式評估為 100，而第二個運算式則評估為 31。  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序與關聯性](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [運算子 &#40;SSIS 運算式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
