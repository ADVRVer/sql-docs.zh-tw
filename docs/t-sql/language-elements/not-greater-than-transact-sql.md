---
title: "!&gt;（不大於）(TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- Not Greater
- Greater
- '!>_TSQL'
- '!>'
- Not Greater Than
dev_langs:
- TSQL
helpviewer_keywords:
- '!> (not greater than)'
- not greater than operator (!>)
ms.assetid: 71a413ed-64f1-4ab9-9c52-c5959a77d00f
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 61f574082f98aa61601035f44c73041275c386de
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="gt-not-greater-than-transact-sql"></a>!&gt;（不大於）(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  比較兩個運算式 (比較運算子)。 當您在比較非 Null 運算式時，如果左運算元的值不大於右運算元，則結果為 TRUE，否則結果就是 FALSE。 與 = (等於) 比較運算子不同的是，兩個 NULL 值的 !> 比較結果，不受到 ANSI_NULLS 設定的影響。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
expression !> expression  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 任何有效[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。 這兩個運算式的類型，都必須是可以隱含轉換的資料類型。 轉換的規則是根據[資料類型優先順序](../../t-sql/data-types/data-type-precedence-transact-sql.md)。  
  
## <a name="result-types"></a>結果類型  
 **布林**  
  
## <a name="see-also"></a>另請參閱  
 [資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [運算子 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

