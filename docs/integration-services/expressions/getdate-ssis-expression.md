---
title: GETDATE (SSIS 運算式) | Microsoft Docs
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
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 29c3f28f3efa22a1691cc47e105300e7dd92543e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="getdate-ssis-expression"></a>GETDATE (SSIS 運算式)
  以 DT_DBTIMESTAMP 格式傳回目前的系統日期。 GETDATE 函數不採用引數。  
  
> [!NOTE]  
>  從 GETDATE 函數傳回結果的長度為 29 個字元。  
  
## <a name="syntax"></a>語法  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>引數  
 無  
  
## <a name="result-types"></a>結果類型  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會傳回目前日期的年。  
  
```  
DATEPART("year",GETDATE())  
```  
  
 此範例會傳回 **ModifiedDate** 資料行中日期與目前日期之間的天數。  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 此範例會對目前日期加上三個月。  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>另請參閱  
 [GETUTCDATE &#40;SSIS 運算式&#41;](../../integration-services/expressions/getutcdate-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
