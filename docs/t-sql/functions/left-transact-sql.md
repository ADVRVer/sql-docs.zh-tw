---
title: LEFT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- LEFT
- LEFT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- character strings [SQL Server], LEFT
- characters [SQL Server], leftmost
- LEFT function
- leftmost character of expression
ms.assetid: 44a8c71b-63d8-458b-8b5d-99d570067c3c
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 361059daeb60402f564caa09837046117804ba6c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "68059917"
---
# <a name="left-transact-sql"></a>LEFT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回字元字串含指定字元數的左側部分。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
LEFT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>引數  
 *character_expression*  
 這是字元或二進位資料的[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。 *character_expression* 可以是常數、變數或資料行。 *character_expression* 可以是除了 **text** 或 **ntext** 之外的任何資料類型，可隱含地轉換為 **varchar** 或 **nvarchar**。 否則，請使用 [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) 函數來明確轉換 *character_expression*。  
  
 *integer_expression*  
 這是一個指定將傳回的 *character_expression* 字元數的正整數。 如果 *integer_expression* 是負數，則會傳回錯誤。 如果 *integer_expression* 是 **bigint** 類型且包含大數值，則 *character_expression* 必須屬於大型資料類型，例如 **varchar(max)** 。  
  
 *integer_expression* 參數會將 UTF-16 代理字元視為一個字元。  
  
## <a name="return-types"></a>傳回型別  
 當 **character_expression** 是非 Unicode 字元資料類型時，則傳回 *varchar*。  
  
 當 **character_expression** 是 Unicode 字元資料類型時，則傳回 *nvarchar*。  
  
## <a name="remarks"></a>備註  
 當使用 SC 定序時，*integer_expression* 參數會將 UTF-16 代理字組視為一個字元。 如需詳細資訊，請參閱 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-left-with-a-column"></a>A. 使用 LEFT 搭配資料行  
 下列範例會傳回 `Product` 資料庫的 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料表中，每個產品名稱最左邊的五個字元。  
  
```  
SELECT LEFT(Name, 5)   
FROM Production.Product  
ORDER BY ProductID;  
GO  
```  
  
### <a name="b-using-left-with-a-character-string"></a>B. 使用 LEFT 搭配字元字串  
 下列範例會利用 `LEFT` 來傳回字元字串 `abcdefg` 最左側兩個字元。  
  
```  
SELECT LEFT('abcdefg',2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab   
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-left-with-a-column"></a>C. 使用 LEFT 搭配資料行  
 下列範例會傳回每個產品名稱的最左側五個字元。  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT(EnglishProductName, 5)   
FROM dbo.DimProduct  
ORDER BY ProductKey;  
```  
  
### <a name="d-using-left-with-a-character-string"></a>D. 使用 LEFT 搭配字元字串  
 下列範例會利用 `LEFT` 來傳回字元字串 `abcdefg` 最左側兩個字元。  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab  
```  
  
## <a name="see-also"></a>另請參閱  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)  
 [CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [字串函數 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

