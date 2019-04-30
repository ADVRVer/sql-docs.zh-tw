---
title: 用於檢查資料的範例資料錄集 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bfae67a14fb312f1b396cfc60f69e8cbe8babdf7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63063084"
---
# <a name="sample-recordset-for-examining-data"></a>用於檢查資料的範例資料錄集
首先，讓我們看看**資料錄集**物件傳回使用下列 SQL 查詢，針對 Microsoft SQL Server 中的基底的 Northwind 範例資料執行。  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 結果**資料錄集**物件包含下表所示的資料庫中的所有會產生。  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|得以 Bob 有機曬的梨子|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle Sauerkraut|45.6000|  
|51|柳乾蘋果|53.0000|  
|74|長壽豆腐|10.0000|  
  
 如果您想要自行取得這些結果，請嘗試下列 JScript 範例：  
  
-   [若要傳回的資料錄集的 JScript 範例](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
