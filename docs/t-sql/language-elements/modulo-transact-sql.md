---
title: '% (模數) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- modulo
- modulus
- '% (Modulo)'
- '% (Modulus)'
- MOD_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- '% (modulo operator)'
- '% (modulus operator)'
- remainder of division operation
- modulo operator (%)
- modulus operator (%)
ms.assetid: f93c662e-f405-486e-bf23-a2d03907b5bd
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fd3f08c6c62b0cec436e86556679b87e5ca3b9a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="-modulus-transact-sql"></a>% (模數) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回某個數值除以另一個數值的餘數。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>引數  
 *dividend*  
 要執行除法的數值運算式。 *dividend* 必須是整數與貨幣資料類型類別目錄中任何一個資料類型，或是 **numeric** 資料類型的有效[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。  
  
 *divisor*  
 要除以被除數的數值運算式。 *divisor* 必須是整數與貨幣資料類型類別目錄中任何一個資料類型，或是 **numeric** 資料類型的任何有效運算式。  
  
## <a name="result-types"></a>結果類型  
 由兩個引數的資料類型決定。  
  
## <a name="remarks"></a>Remarks  
 您可以在 SELECT 陳述式的選取清單中使用模數算術運算子，搭配資料行名稱、數值常數，或是任何整數和貨幣資料類型類別目錄或 **numeric** 資料類型之有效運算式的任何組合。  
  
## <a name="examples"></a>範例  
  
### <a name="a-simple-example"></a>A. 簡單範例  
 下列範例會將 38 這個數字除以 5。 結果中會產生 7 的整數部分，並示範模數如何傳回餘數 3。  
  
```  
SELECT 38 / 5 AS Integer, 38 % 5 AS Remainder ;  
  
```  
  
### <a name="b-example-using-columns-in-a-table"></a>B. 在資料表中使用資料行的範例  
 下列範例會傳回產品識別碼、產品單價以及將每個產品價格 (轉換為整數值) 除以訂購產品數的模數 (餘數)。  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(100)ProductID, UnitPrice, OrderQty,  
   CAST((UnitPrice) AS int) % OrderQty AS Modulo  
FROM Sales.SalesOrderDetail;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example"></a>C：簡單範例  
 下列範例示範 3 除以 2 時，`%` 運算子所傳回的結果。  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) 3%2 FROM dimEmployee;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
1         
```  
  
## <a name="see-also"></a>另請參閱  
 [內建函數 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [運算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [%= &#40;模數指派&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/modulo-equals-transact-sql.md)   
 [複合運算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


