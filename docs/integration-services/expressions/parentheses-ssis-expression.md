---
title: () (括號) (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 814be716ffeb0728f7a2682754f2325beb432191
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35329052"
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
 *expression*的資料類型。 如需詳細資訊，請參閱 [Integration Services 資料類型](../../integration-services/data-flow/integration-services-data-types.md)。  
  
## <a name="expression-examples"></a>運算式範例  
 此範例示範使用括號修改運算子之優先順序的方式。 第一個運算式評估為 100，而第二個運算式則評估為 31。  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序與關聯性](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [運算子 &#40;SSIS 運算式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
