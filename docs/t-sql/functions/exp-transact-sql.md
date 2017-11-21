---
title: "EXP (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXP_TSQL
- EXP
dev_langs:
- TSQL
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 5a9b8c52-6fb6-4e33-8b02-a878785b2f51
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c50757291a8f1fc3d58d8a9a131c4a24aa79a008
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="exp-transact-sql"></a>EXP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回指定的指數值**float**運算式。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
EXP ( float_expression )  
```  
  
## <a name="arguments"></a>引數  
 *float_expression*  
 是[運算式](../../t-sql/language-elements/expressions-transact-sql.md)型別的**float**或可以隱含地轉換成的型別**float**。  
  
## <a name="return-types"></a>傳回類型  
 **float**  
  
## <a name="remarks"></a>備註  
 常數**e** (2.718281...) 是自然對數的基底。  
  
 數字的指數，是常數**e**的數字乘冪。 例如，EXP(1.0) = e^1.0 = 2.71828182845905 和 EXP(10) = e^10 = 22026.4657948067。  
  
 數字的自然對數的指數是數字本身： EXP (記錄檔 (*n*)) =  *n* 。 而指數的自然對數是該數值本身： 記錄檔 (EXP (*n*)) =  *n* 。  
  
## <a name="examples"></a>範例  
  
### <a name="a-finding-the-exponent-of-a-number"></a>A. 尋找數字的指數  
 下列範例會宣告一個變數，並且傳回該指定變數的指數值 (`10`) 以及文字描述。  
  
```  
DECLARE @var float  
SET @var = 10  
SELECT 'The EXP of the variable is: ' + CONVERT(varchar,EXP(@var))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------------------------------  
The EXP of the variable is: 22026.5  
(1 row(s) affected)  
```  
  
### <a name="b-finding-exponentials-and-natural-logarithms"></a>B. 尋找指數和自然對數  
 下列範例會傳回 `20` 之自然對數的指數值，以及 `20` 之指數的自然對數。 由於這些函數互為反向函數，因此傳回值都是 `20`。  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------------- ----------------------  
20                     20  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-finding-the-exponent-of-a-number"></a>C. 尋找數字的指數  
 下列範例會傳回指定值的指數值 (`10`)。  
  
```  
SELECT EXP(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------  
22026.4657948067  
```  
  
### <a name="d-finding-exponential-values-and-natural-logarithms"></a>D. 尋找指數值和自然對數  
 下列範例會傳回 `20` 之自然對數的指數值，以及 `20` 之指數的自然對數。 由於這些函數互為反向函數，因此傳回值都是 `20`。  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20));  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------- -----------------  
20                  20  
```  
  
## <a name="see-also"></a>另請參閱  
 [數學函數 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [記錄檔 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/log-transact-sql.md)   
 [LOG10 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  


