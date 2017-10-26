---
title: "DATEADD （SSIS 運算式） |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 77230956969fb2fd2d27a1dec42140dd91a5cbd5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/28/2017

---
# <a name="dateadd-ssis-expression"></a>DATEADD (SSIS 運算式)
  在日期的指定之日期部分加上代表日期或時間間隔的數字之後，傳回新的 DT_DBTIMESTAMP 值。 number 參數必須評估為整數，date 參數必須評估為有效的日期。  
  
## <a name="syntax"></a>語法  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a>引數  
 *日期部份*  
 是指定要加入數字之日期部份的參數。  
  
 *number*  
 這是用來遞增 *datepart*的值。 值必須是剖析運算式時已知的整數值。  
  
 *date*  
 傳回有效日期或日期格式字串的運算式。  
  
## <a name="result-types"></a>結果類型  
 DT_DBTIMESTAMP  
  
## <a name="remarks"></a>備註  
 下表列出運算式評估工具所辨識的日期部份與縮寫。 日期部份的名稱不區分大小寫。  
  
|日期部份|縮寫|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|Day|dd, d|  
|週|wk, ww|  
|Weekday|dw, w|  
|Hour|Hh|  
|Minute|mi, n|  
|第二個|ss, s|  
|Millisecond|Ms|  
  
 *number* 引數必須在剖析運算式時提供。 這個引數可以是常數或變數。 您不可使用資料行的值，因為這些值在剖析運算式時並非已知。  
  
 *datepart* 引數必須加上引號。  
  
 日期常值必須明確轉換為日期資料類型之一。 如需詳細資訊，請參閱＜ [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)＞。  
  
 如果引數為 Null，則 DATEADD 會傳回 Null 結果。  
  
 如果日期無效、日期或時間單位不是字串，或累加不是靜態整數，則會發生錯誤。  
  
## <a name="ssis-expression-examples"></a>SSIS 運算式範例  
 此範例會對目前日期加上一個月。  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 此範例會對 **ModifiedDate** 資料行中的日期加上 21 天。  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 此範例會對常值日期加上 2 年。  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a>另請參閱  
 [DATEDIFF &#40;SSIS 運算式&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS 運算式 &#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [日 &#40;SSIS 運算式 &#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [月份 &#40;SSIS 運算式 &#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [年份 &#40;SSIS 運算式 &#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

