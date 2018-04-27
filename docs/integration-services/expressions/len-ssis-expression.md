---
title: LEN (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31ae12cd8c17a436a4d5f8e023ea6efeda8a0898
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="len-ssis-expression"></a>LEN (SSIS 運算式)
  傳回字元運算式中的字元數。 如果字串包含開頭和尾端空白，則函數會將它們加入計數中。 LEN 會針對單位元組和雙位元組字元的相同字串傳回完全相同的值。  
  
## <a name="syntax"></a>語法  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a>引數  
 *character_expression*  
 是要評估的運算式。  
  
## <a name="result-types"></a>結果類型  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 *character_expression* 引數可以是 DT_WSTR、DT_TEXT、DT_NTEXT 或 DT_IMAGE 資料類型。 如需相關資訊，請參閱 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)。  
  
 如果 *character_expression* 是字串常值或具有 DT_STR 資料類型的資料行，則它會在 LEN 執行其作業前隱含轉換成 DT_WSTR 資料類型。 其他資料類型必須明確地轉換為 DT_WSTR 資料類型。 如需詳細資訊，請參閱 [Cast &#40;SSIS 運算式&#41;](../../integration-services/expressions/cast-ssis-expression.md)。  
  
 如果傳遞至 LEN 函數的引數資料類型為「二進位大型物件區塊」(Binary Large Object Block，BLOB)，例如 DT_TEXT、DT_NTEXT 或 DT_IMAGE，則函數會傳回位元組計數。  
  
 如果引數為 Null，則 LEN 會傳回 Null 結果。  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會傳回字串常值的長度。 傳回結果為 12。  
  
```  
LEN("Ball Bearing")  
```  
  
 此範例會傳回 **FirstName** 和 **LastName** 資料行中各值長度之間的差異。  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 使用「系統」變數 **MachineName**傳回電腦名稱的長度。  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a>另請參閱  
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
