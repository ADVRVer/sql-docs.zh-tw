---
title: MSSQLSERVER_8621 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2877d4021c636fdefb0b71ed4ae99cf6c2cd44e5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver8621"></a>MSSQLSERVER_8621
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|8621|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|OPTIMIZER_STACK_OVERFLOW_ERR|  
|訊息文字|查詢處理器在查詢最佳化期間已用完堆疊空間。 請簡化查詢。|  
  
## <a name="explanation"></a>說明  
展開的查詢大小是造成這項錯誤最有可能的原因。 展開的查詢會取代原始查詢中其參照的每個檢視、計算資料行、[!INCLUDE[tsql](../../includes/tsql-md.md)] 函數與一般資料表運算式的定義，以及串聯式動作，例如更新次要索引、檢視和觸發程序。  
  
最有可能的情況是查詢的某個維度很大；例如，檢視定義參考的資料表數目，或是純量運算式非常大。  
  
## <a name="user-action"></a>使用者動作  
依據最大的維度，將該查詢分割成多項查詢，藉以簡化查詢。 請先移除實際上不需要的任何查詢元素，然後嘗試新增暫存資料表，並將查詢分割成兩項查詢。  只將查詢的某個部分移到子查詢、函數或一般資料表運算式並不夠，因為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 編譯器會重新合併這些元素。  
  

