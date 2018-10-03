---
title: 資料類型優先順序 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- precedence [SQL Server]
- data types [SQL Server], converting
- data types [SQL Server], precedence
- converting data types [SQL Server], precedence
- precedence [SQL Server], data types
ms.assetid: f4c804ab-ed3f-43b1-a024-c9ac6944b66b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 10a397014df751c7e6946f8ec9cb251bc9a1cf3f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765206"
---
# <a name="data-type-precedence-transact-sql"></a>資料類型優先順序 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

當一個運算子結合兩個不同資料類型的運算式時，資料類型優先順序的規則，會指定將低優先順序的資料類型，轉換為高優先順序的資料類型。 如果轉換不是支援的隱含轉換，就會傳回錯誤。 如果這兩個運算元運算式的資料類型相同，則作業結果就含有該資料類型。
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用下列資料類型優先順序：
  
1.  使用者自訂資料類型 (最高)  
1.  **sql_variant**  
1.  **xml**  
1.  **datetimeoffset**  
1.  **datetime2**  
1.  **datetime**  
1.  **smalldatetime**  
1.  **date**  
1. **time**  
1. **float**  
1. **real**  
1. **decimal**  
1. **money**  
1. **smallmoney**  
1. **bigint**  
1. **int**  
1. **smallint**  
1. **tinyint**  
1. **bit**  
1. **ntext**  
1. **text**  
1. **image**  
1. **timestamp**  
1. **uniqueidentifier**  
1. **nvarchar** (包含 **nvarchar(max)**)  
1. **nchar**  
1. **varchar** (包含 **varchar(max)**)  
1. **char**  
1. **varbinary** (包含 **varbinary(max)**)  
1. **binary** (最低)  
  
## <a name="see-also"></a>另請參閱
[資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
