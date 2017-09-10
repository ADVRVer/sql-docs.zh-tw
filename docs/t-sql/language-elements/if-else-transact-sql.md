---
title: "如果...其他 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 07/11/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IF_TSQL
- IF
dev_langs:
- TSQL
helpviewer_keywords:
- IF...ELSE keyword
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 676c881f-dee1-417a-bc51-55da62398e81
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ea7d020bc637ff2dda4ba0540de8385e99170cd
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="ifelse-transact-sql"></a>IF...ELSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的執行上強加條件。 如果 IF 關鍵字的條件獲得滿足，就會執行在 IF 關鍵字及其條件之後的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：布林運算式會傳回 TRUE。 選擇性的 ELSE 關鍵字導入了另一個在 IF 條件未獲滿足時所執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：布林運算式會傳回 FALSE。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
IF Boolean_expression   
     { sql_statement | statement_block }   
[ ELSE   
     { sql_statement | statement_block } ]   
```  
  
## <a name="arguments"></a>引數  
 *Boolean_expression*  
 這是傳回 TRUE 或 FALSE 的運算式。 如果布林運算式包含 SELECT 陳述式，則這個 SELECT 陳述式必須括在括號中。  
  
 { *q*| *statement_block* }  
 這是藉由使用陳述式區塊加以定義的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或陳述式分組。 除非使用陳述式區塊，否則，IF 或 ELSE 條件只會影響一個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的效能。  
  
 若要定義陳述式區塊，請使用流程控制關鍵字 BEGIN 和 END。  
  
## <a name="remarks"></a>備註  
 您可以在批次、預存程序和隨選查詢中使用 IF...ELSE 建構。 當在預存程序中使用這個建構時，經常會測試某個參數是否存在。  
  
 您可以在 IF 或 ELSE 之後，進行巢狀的 IF 測試。 巢狀層級數目的限制，會隨著可用的記憶體而不同。  
  
## <a name="example"></a>範例  
  
```  
IF DATENAME(weekday, GETDATE()) IN (N'Saturday', N'Sunday')
       SELECT 'Weekend';
ELSE 
       SELECT 'Weekday';
```  
  
 如需其他範例，請參閱[ELSE &#40; 如果...其他 &#41;&#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/else-if-else-transact-sql.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下列範例會使用`IF…ELSE`判斷這兩個回應，讓使用者，根據中項目的權數`DimProduct`資料表。  
  
```  
-- Uses AdventureWorksDW  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct 
                  WHERE ProductKey = @productKey)   
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is too heavy to ship and is only available for pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
ELSE  
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is available for shipping or pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
```  
  
## <a name="see-also"></a>另請參閱  
 [開始...結束 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [結束 &#40;開始...結束 &#41;&#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [雖然 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/while-transact-sql.md)   
 [案例 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [流程控制語言 &#40;TRANSACT-SQL &#41;](~/t-sql/language-elements/control-of-flow.md) [ELSE &#40; 如果...其他 &#41;&#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/else-if-else-transact-sql.md) 
  
  




