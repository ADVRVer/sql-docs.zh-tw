---
title: TRY_CONVERT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRY_CONVERT_TSQL
- TRY_CONVERT
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_CONVERT function
ms.assetid: 3e6e7825-6482-4cb2-a8c2-9abc99e265a6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5fedc9777146d24cb04fb7652344f244babc8246
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2018
---
# <a name="tryconvert-transact-sql"></a>TRY_CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  如果轉換成功，則會傳回轉換為指定之資料類型的值，否則會傳回 Null。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
TRY_CONVERT ( data_type [ ( length ) ], expression [, style ] )  
```  
  
## <a name="arguments"></a>引數  
 *data_type [ ( length ) ]*  
 *運算式*轉換成的資料類型。  
  
 *expression*  
 要進行轉換的值。  
  
 *style*  
 這是指定 **TRY_CONVERT** 函數如何轉譯 *expression* 的選用性整數運算式。  
  
 *style* 接受與 **CONVERT** 函數的 *style* 參數相同的值。 如需詳細資訊，請參閱 [CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)。  
  
 可接受值的範圍由 *data_type* 值決定。 如果 *style* 是 Null，那麼 **TRY_CONVERT** 會傳回 Null。  
  
## <a name="return-types"></a>傳回類型  
 如果轉換成功，則會傳回轉換為指定之資料類型的值，否則會傳回 Null。  
  
## <a name="remarks"></a>Remarks  
 **TRY_CONVERT** 會採用傳遞給它的值，然後會嘗試將該值轉換為指定的 *data_type*。 如果轉換成功，**TRY_CONVERT** 會傳回當做指定之 *data_type* 的值；如果發生錯誤則會傳回 Null。 但是，若您要求明確不允許的轉換，則 **TRY_CONVERT** 會失敗並出現錯誤。  
  
 **TRY_CONVERT** 是在相容性層級 110 及更高層級中保留的關鍵字。  
  
 函數能以遠端方式在具有 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 及更高版本的伺服器上運作。 它在版本低於 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 的伺服器上無法以遠端方式運作。  
  
## <a name="examples"></a>範例  
  
### <a name="a-tryconvert-returns-null"></a>A. TRY_CONVERT 傳回 Null。  
 以下的範例證明當轉換失敗時，TRY_CONVERT 會傳回 null。  
  
```sql  
SELECT   
    CASE WHEN TRY_CONVERT(float, 'test') IS NULL   
    THEN 'Cast failed'  
    ELSE 'Cast succeeded'  
END AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
Cast failed  
  
(1 row(s) affected)  
```  
  
 下列範例示範運算式必須採用所需的格式。  
  
```sql  
SET DATEFORMAT dmy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-tryconvert-fails-with-an-error"></a>B. TRY_CONVERT 失敗並出現錯誤  
 以下的範例證明當明確不允許轉換時，TRY_CONVERT 會傳回錯誤。  
  
```sql  
SELECT TRY_CONVERT(xml, 4) AS Result;  
GO  
```  
  
 此陳述式的結果為錯誤，因為整數無法轉換為 xml 資料類型。  
  
```  
Explicit conversion from data type int to xml is not allowed.  
```  
  
### <a name="c-tryconvert-succeeds"></a>C. TRY_CONVERT 成功  
 這個範例示範運算式必須採用所需的格式。  
  
```  
SET DATEFORMAT mdy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------------------  
2010-12-31 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>另請參閱  
 [CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
