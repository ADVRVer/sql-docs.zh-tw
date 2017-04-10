---
title: "ABS (SSIS 運算式) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ABS 函數"
  - "正絕對值"
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# ABS (SSIS 運算式)
  傳回數值運算式的絕對正數值。  
  
## 語法  
  
```  
  
ABS(numeric_expression)  
```  
  
## 引數  
 *numeric_expression*  
 是帶正負號或不帶正負號的數值運算式。  
  
## 結果類型  
 提交至函數之數值運算式的資料類型。  
  
## 備註  
 如果引數為 Null，則 ABS 會傳回 Null 結果。  
  
## 運算式範例  
 這些範例會將 ABS 函數套用至正數或負數。 兩者都傳回 1.23。  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 此範例會將 ABS 函數套用至減去 **HighTemperature** 和 **LowTempature**變數值的運算式。  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## 請參閱＜  
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  