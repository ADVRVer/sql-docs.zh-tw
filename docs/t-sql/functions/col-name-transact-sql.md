---
title: COL_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COL_NAME
- COL_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- COL_NAME function
- column names [SQL Server]
- names [SQL Server], columns
ms.assetid: 214144ab-f2bc-4052-83cf-caf0a85c4cc6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 91e36569f32f75e5b5328974f0df870c7814f251
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064724"
---
# <a name="colname-transact-sql"></a>COL_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

此函式會根據資料表資料行的資料表識別碼和資料行識別碼值來傳回該資料表資料行的名稱。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
COL_NAME ( table_id , column_id )  
```  
  
## <a name="arguments"></a>引數  
*table_id*  
包含該資料行之資料表的識別碼。 *table_id* 引數具有 **int** 資料類型。
  
*column_id*  
資料行的識別碼。 *column_id* 引數具有 **int** 資料類型。
  
## <a name="return-types"></a>傳回類型
**sysname**
  
## <a name="exceptions"></a>例外狀況  
發生錯誤或呼叫端沒有檢視物件的正確權限時，會傳回 NULL。
  
在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，使用者只能檢視使用者擁有或被授與某些權限之安全性實體的中繼資料。 這表示，如果使用者沒有物件的正確權限，則發出中繼資料的內建函式 (例如 `COL_NAME`) 可能會傳回 NULL。 如需詳細資訊，請參閱[中繼資料可見性設定](../../relational-databases/security/metadata-visibility-configuration.md)。
  
## <a name="remarks"></a>Remarks  
*table_id* 和 *column_id* 參數會共同產生一個資料行名稱字串。
  
如需取得資料表和資料行識別碼的詳細資訊，請參閱 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)。
  
## <a name="examples"></a>範例  
此範例會傳回範例 `Employee` 資料表中第一個資料行的名稱。
  
```sql
-- Uses AdventureWorks  
  
SELECT COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 1) AS FirstColumnName,  
COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 2) AS SecondColumnName;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
ColumnName          
------------   
BusinessEntityID  
```  
  
## <a name="see-also"></a>另請參閱
[運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[中繼資料函式 &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)  
[COL_LENGTH &#40;Transact-SQL&#41;](../../t-sql/functions/col-length-transact-sql.md)
  
  

