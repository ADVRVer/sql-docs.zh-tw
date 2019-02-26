---
title: IF...ELSE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1209760f3594a0820da651ea4b9cdc21b536b6fd
ms.sourcegitcommit: a13256f484eee2f52c812646cc989eb0ce6cf6aa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2019
ms.locfileid: "56801032"
---
# <a name="ifelse-transact-sql"></a>IF...ELSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的執行上強加條件。 如果 IF 關鍵字的條件獲得滿足，就會執行在 IF 關鍵字及其條件之後的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：布林運算式會傳回 TRUE。 選擇性的 ELSE 關鍵字導入了另一個在 IF 條件未獲滿足時所執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：布林運算式會傳回 FALSE。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
IF Boolean_expression   
     { sql_statement | statement_block }   
[ ELSE   
     { sql_statement | statement_block } ]   
```  
  
## <a name="arguments"></a>引數  
 *Boolean_expression*  
 這是傳回 TRUE 或 FALSE 的運算式。 如果布林運算式包含 SELECT 陳述式，則這個 SELECT 陳述式必須括在括號中。  
  
 { *sql_statement*| *statement_block* }  
 這是藉由使用陳述式區塊加以定義的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或陳述式分組。 除非使用陳述式區塊，否則，IF 或 ELSE 條件只會影響一個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的效能。  
  
 若要定義陳述式區塊，請使用流程控制關鍵字 BEGIN 和 END。  
  
## <a name="remarks"></a>Remarks  
 您可以在批次、預存程序和隨選查詢中使用 IF...ELSE 建構。 當在預存程序中使用這個建構時，經常會測試某個參數是否存在。  
  
 您可以在 IF 或 ELSE 之後，進行巢狀的 IF 測試。 巢狀層級數目的限制，會隨著可用的記憶體而不同。  
  
## <a name="example"></a>範例  
  
```  
IF DATENAME(weekday, GETDATE()) IN (N'Saturday', N'Sunday')
       SELECT 'Weekend';
ELSE 
       SELECT 'Weekday';
```  
  
 如需詳細資訊，請參閱 [ELSE &#40;IF...ELSE&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/else-if-else-transact-sql.md)。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下列範例使用 `IF...ELSE`，以根據 `DimProduct` 資料表中項目的權數，來判斷要向使用者顯示兩個回應中的哪一個。  
  
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
 [BEGIN...END &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [END &#40;BEGIN...END&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)   
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [流程控制語言 &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md) [ELSE &#40;IF...ELSE&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/else-if-else-transact-sql.md) 
  
  



