---
title: "CEILING (SSIS 運算式) | Microsoft Docs"
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
  - "大於或等於運算式的最小整數"
  - "CEILING 函數 [SSIS]"
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# CEILING (SSIS 運算式)
  傳回大於或等於數值運算式的最小整數。  
  
## 語法  
  
```  
  
CEILING(numeric_expression)  
```  
  
## 引數  
 *numeric_expression*  
 有效的數值運算式。  
  
## 結果類型  
 提交至函數之數值運算式的資料類型。  
  
## 備註  
 如果引數為 Null，則 CEILING 會傳回 Null 結果。  
  
## 運算式範例  
 這些範例會將 CEILING 函數套用至正值、負值和零值。  
  
```  
CEILING(123.74)  
```  
  
 傳回 124.00  
  
```  
CEILING(-124.27)  
```  
  
 傳回 -124.00  
  
```  
CEILING(0.00)  
```  
  
 傳回 0.00  
  
## 請參閱＜  
 [FLOOR &#40;SSIS 運算式&#41;](../../integration-services/expressions/floor-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  