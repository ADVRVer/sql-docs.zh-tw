---
title: "NULL 和不明 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: "5"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c26004fdfa5f2607235ffe7dddb7826a77f38b31
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="null-and-unknown-transact-sql"></a>NULL 和不明 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL 表示是未知的值。 Null 值是從空白或零值不同。 兩個 Null 值永遠不會相等。 比較兩個 null 值，或 null 值與任何其他值之間傳回未知的因為每個 NULL 值是未知的。  
  
 Null 值通常表示資料是不明、 不適用，或稍後新增。 例如，客戶的稱謂在下訂單時可能是未知的。  
  
 請注意下列有關 null 值：  
  
-   若要在查詢中測試 Null 值，請在 WHERE 子句中使用 IS NULL 或 IS NOT NULL。  
  
-   Null 值都可以插入資料行明確陳述 NULL INSERT 或 UPDATE 陳述式中的，或離開從 INSERT 陳述式的資料行。  
  
-   Null 值不能做為區別在資料表中，例如主索引鍵，或用來散發資料列，例如散發索引鍵資訊的另一個資料列的資料表中的一個資料列所需的資訊。  
  
 當資料中包含 Null 值時，邏輯與比較運算子可能會傳回第三種結果 UNKNOWN，而非只有 TRUE 或 FALSE。 這種三重數值邏輯的需要是造成應用程式錯誤的來源。 除非運算子的結果不需依賴未知的運算式，包括突發情況的布林運算式中的邏輯運算子會傳回 UNKNOWN。 這些資料表會提供這種行為的範例。  
  
 下表顯示將 AND 運算子套用至兩個布林運算式的結果，其中一個運算式會傳回 UNKNOWN。  
  
|運算式 1|Expression 2|結果|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|UNKNOWN|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|FALSE|  
  
 下表顯示將 OR 運算子套用至兩個布林運算式的結果，其中一個運算式會傳回 UNKNOWN。  
  
|運算式 1|Expression 2|結果|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|TRUE|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|UNKNOWN|  
  
## <a name="see-also"></a>另請參閱  
 [和 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [或者 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [不 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [為 NULL &#40;TRANSACT-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  
