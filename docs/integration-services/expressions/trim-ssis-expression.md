---
title: "TRIM (SSIS 運算式) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- leading blanks
- TRIM function
- trailing blanks
ms.assetid: 7dd9081d-a3d4-483a-bf7e-bf2bd7692d39
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 48ed42d0e12ed6b3d80c61a392b50a529813899e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="trim-ssis-expression"></a>TRIM (SSIS 運算式)
  傳回移除開頭和尾端空白之後的字元運算式。  
  
> [!NOTE]  
>  TRIM 不會移除空白字元，例如 Tab 鍵或換行字元。 Unicode 會為許多不同類型的空格提供字碼指標，但此功能只會辨識 Unicode 字碼指標 0x0020。 當將雙位元組字集 (DBCS) 字串轉換為 Unicode 時，它們可以包括 0x0020 以外的空格字元，但此功能無法移除這些空格。 若要移除所有種類的空格，您可以在從「指令碼」元件執行的指令碼中使用 Microsoft Visual Basic .NET Trim 方法。  
  
## <a name="syntax"></a>語法  
  
```  
  
TRIM(character_expression)  
```  
  
## <a name="arguments"></a>引數  
 *character_expression*  
 要移除空白的字元運算式。  
  
## <a name="result-types"></a>結果類型  
 DT_WSTR  
  
## <a name="remarks"></a>備註  
 如果引數為 Null，則 TRIM 會傳回 Null 結果。  
  
 TRIM 只適用於 DT_WSTR 資料類型。 如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 TRIM 執行其作業前隱含轉換成 DT_WSTR 資料類型。 其他資料類型必須明確地轉換為 DT_WSTR 資料類型。 如需詳細資訊，請參閱 [Integration Services 資料類型](../../integration-services/data-flow/integration-services-data-types.md)和 [Cast &#40;SSIS 運算式&#41;](../../integration-services/expressions/cast-ssis-expression.md)。  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會移除字串常值開頭和尾端的空白。 傳回結果為「New York」。  
  
```  
TRIM("   New York   ")  
```  
  
 此範例會從串連 **FirstName** 和 **LastName** 資料行的結果中移除開頭和尾端的空白。 **FirstName** 和 **LastName** 之間的空白字串則不會移除。  
  
```  
TRIM(FirstName + " "+ LastName)  
```  
  
## <a name="see-also"></a>另請參閱  
 [LTRIM &#40;SSIS 運算式&#41;](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [RTRIM &#40;SSIS 運算式&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
