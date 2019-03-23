---
title: DAY (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 47140db35618143522ad217f5eda2aa3d4b7507b
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58384466"
---
# <a name="day-ssis-expression"></a>DAY (SSIS 運算式)
  傳回代表日期之日部分的整數。  
  
## <a name="syntax"></a>語法  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a>引數  
 *date*  
 傳回有效日期或日期格式字串的運算式。  
  
## <a name="result-types"></a>結果類型  
 DT_I4  
  
## <a name="remarks"></a>備註  
 如果引數為 Null，則 DAY 會傳回 Null 結果。  
  
 日期常值必須明確轉換為日期資料類型之一。 如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。  
  
> [!NOTE]  
>  運算式將會失敗時的日期常值明確轉換成其中一個日期資料類型驗證：DT_DBTIMESTAMPOFFSET 和 DT_DBTIMESTAMP2。  
  
 使用 DAY 函數較為簡潔，但相當於使用 DATEPART("Day", date)。  
  
## <a name="expression-examples"></a>運算式範例  
 這個範例會傳回日期常值的日數。 如果日期格式為「mm/dd/yyyy」，則這個範例會傳回 23。  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 這個範例會傳回 **ModifiedDate** 資料行中，代表天的整數。  
  
```  
DAY(ModifiedDate)  
```  
  
 這個範例會傳回代表目前日期之日子的整數。  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a>另請參閱  
 [DATEADD &#40;SSIS 運算式&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS 運算式&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS 運算式&#41;](datepart-ssis-expression.md)   
 [MONTH &#40;SSIS 運算式&#41;](month-ssis-expression.md)   
 [YEAR &#40;SSIS 運算式&#41;](year-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](functions-ssis-expression.md)  
  
  
