---
title: "NULLIF (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 08/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NULLIF
- NULLIF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], equivalent expressions
- expressions [SQL Server], null values
- NULLIF function
- equivalent expressions [SQL Server]
ms.assetid: 44c7b67e-74c7-4bb9-93a4-7a3016bd2feb
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e07e3960466d782911c20ced9ce6d88a10406bc2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="nullif-transact-sql"></a>NULLIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  如果兩個指定的運算式相等，便傳回 Null 值。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
NULLIF ( expression , expression )  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 是任何有效的純量[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。  
  
## <a name="return-types"></a>傳回類型  
 傳回與第一個相同型別*運算式*。  
  
 NULLIF 會傳回第一個*運算式*兩個運算式是否不相等。 如果運算式相等，NULLIF 會傳回 null 值的第一個型別*運算式*。  
  
## <a name="remarks"></a>備註  
 NULLIF 相當於兩個運算式相等且產生的運算式為 NULL 的搜尋 CASE 運算式。  
  
 我們建議您不要在 NULLIF 函數中使用時間相依函數，例如 RAND()。 這可能會造成函式評估兩次，並從兩個引動過程傳回不同的結果。  
  
## <a name="examples"></a>範例  
  
### <a name="a-returning-budget-amounts-that-have-not-changed"></a>A. 傳回尚未變更的預算數量  
 下列範例會建立一份 `budgets` 資料表，來顯示部門 (`dept`) 及其目前預算 (`current_year`) 和前一年的預算 (`previous_year`)。 對今年而言，如果部門預算與前一年相同，就使用 `NULL`，如果預算仍未確定，就使用 `0`。 若只要知道收到預算之部門的平均值，且要併入前一年的預算值 (使用 `previous_year` 值，其中 `current_year` 是 `NULL`)，便將 `NULLIF` 和 `COALESCE` 函數組合起來。  
  
```sql  
CREATE TABLE dbo.budgets  
(  
   dept            tinyint   IDENTITY,  
   current_year      decimal   NULL,  
   previous_year   decimal   NULL  
);  
INSERT budgets VALUES(100000, 150000);  
INSERT budgets VALUES(NULL, 300000);  
INSERT budgets VALUES(0, 100000);  
INSERT budgets VALUES(NULL, 150000);  
INSERT budgets VALUES(300000, 250000);  
GO    
SET NOCOUNT OFF;  
SELECT AVG(NULLIF(COALESCE(current_year,  
   previous_year), 0.00)) AS 'Average Budget'  
FROM budgets;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Average Budget  
 --------------  
 212500.000000  
 (1 row(s) affected)
 ```  
  
### <a name="b-comparing-nullif-and-case"></a>B. 比較 NULLIF 和 CASE  
 下列查詢會評估 `NULLIF` 和 `CASE` 資料行中的值是否相同，以顯示 `MakeFlag` 和 `FinishedGoodsFlag` 之間的相似度。 第一個查詢使用 `NULLIF`。 第二個查詢則使用 `CASE` 運算式。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,   
   NULLIF(MakeFlag,FinishedGoodsFlag)AS 'Null if Equal'  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
  
SELECT ProductID, MakeFlag, FinishedGoodsFlag,'Null if Equal' =  
   CASE  
       WHEN MakeFlag = FinishedGoodsFlag THEN NULL  
       ELSE MakeFlag  
   END  
FROM Production.Product  
WHERE ProductID < 10;  
GO  
```  

### <a name="c-returning-budget-amounts-that-contain-no-data"></a>C： 傳回不包含資料的預算數量  
 下列範例會建立`budgets`資料表載入資料，並使用`NULLIF`傳回 null 值，如果沒有`current_year`也`previous_year`包含資料。  
  
```sql  
CREATE TABLE budgets (  
   dept           tinyint,  
   current_year   decimal(10,2),  
   previous_year  decimal(10,2)  
);  
  
INSERT INTO budgets VALUES(1, 100000, 150000);  
INSERT INTO budgets VALUES(2, NULL, 300000);  
INSERT INTO budgets VALUES(3, 0, 100000);  
INSERT INTO budgets VALUES(4, NULL, 150000);  
INSERT INTO budgets VALUES(5, 300000, 300000);  
  
SELECT dept, NULLIF(current_year,  
   previous_year) AS LastBudget  
FROM budgets;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 dept   LastBudget  
 ----   -----------  
 1      100000.00  
 2      null 
 3      0.00  
 4      null  
 5      null
 ```  
  
## <a name="see-also"></a>另請參閱  
 [案例 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [decimal 和 numeric &#40;TRANSACT-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [系統函數 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


