---
title: "指派運算子 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], assignment
- assignment operators [Transact-SQL]
- headings [SQL Server columns]
- relationships [SQL Server], assignment operators
- column headings [SQL Server]
ms.assetid: c3040db6-21d6-40ac-a783-82c98ec006cc
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d10872712d1b7114655b5d95ab9b871709c55b14
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="assignment-operator-transact-sql"></a>指派運算子 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  等號 (=) 是唯一的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指派運算子。 下列範例會先建立 `@MyCounter` 變數，然後指派運算子再將 `@MyCounter` 設為運算式所傳回的值。  
  
```  
DECLARE @MyCounter INT;  
SET @MyCounter = 1;  
```  
  
 您也可以利用指派運算子來建立資料行標題和定義資料行值的運算式之間的關聯性。 下列範例會顯示資料行標題 `FirstColumnHeading` 和 `SecondColumnHeading`。 所有資料列的 `xyz` 資料行標題都會顯示 `FirstColumnHeading` 字串。 之後，`Product` 資料表中的每個產品識別碼都會列在 `SecondColumnHeading` 資料行標題中。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstColumnHeading = 'xyz',  
       SecondColumnHeading = ProductID  
FROM Production.Product;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算子 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
