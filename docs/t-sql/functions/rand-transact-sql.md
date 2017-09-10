---
title: "RAND (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RAND
- RAND_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RAND function
- values [SQL Server], random float
- random float value
ms.assetid: 363c84d6-b9fa-49ba-9a75-e44f27535ff6
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1d358122487d3568167021ac3a296e1eb2d1974
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  傳回虛擬隨機**float**從 0 到 1，不含值。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
RAND ( [ seed ] )  
```  
  
## <a name="arguments"></a>引數  
 *種子*  
 是一個整數[運算式](../../t-sql/language-elements/expressions-transact-sql.md)(**tinyint**， **smallint**，或**int**) 提供的種子值。 如果*種子*未指定，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]會隨機指派一個初始值。 只要指定初始值之後，傳回的結果一律相同。  
  
## <a name="return-types"></a>傳回類型  
 **float**  
  
## <a name="remarks"></a>備註  
 以同樣的初始值反覆呼叫 RAND()，傳回的結果都是一樣的。  
  
 在一個連接中，如果 RAND() 是以指定的初始值呼叫，則後續所有對 RAND() 的呼叫，都會根據初始的 RAND() 呼叫而產生結果。 例如，下面這個查詢一定會傳回同樣順序的號碼。  
  
```  
SELECT RAND(100), RAND(), RAND()   
```  
  
## <a name="examples"></a>範例  
 在下列範例中，RAND 函數會產生四個不同的隨機號碼。  
  
```  
DECLARE @counter smallint;  
SET @counter = 1;  
WHILE @counter < 5  
   BEGIN  
      SELECT RAND() Random_Number  
      SET @counter = @counter + 1  
   END;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [數學函數 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
