---
title: sp_estimated_rowsize_reduction_for_vardecimal (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- sp_estimated_rowsize_reduction_for_vardecimal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- decimal data type, compressing
- numeric data type, compressing
- estimate decimal compression
- table compression [SQL Server]
ms.assetid: 0fe45983-f9f2-4c7f-938a-0fd96e1cbe8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90de7b95febdf2f1a25a5e584b2ca77bb67f93d4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124505"
---
# <a name="spestimatedrowsizereductionforvardecimal-transact-sql"></a>sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  預估資料列平均大小的縮減 (如果資料表上已啟用 Vardecimal 儲存格式的話)。 您可以使用這個數字來預估資料表大小的整體縮減。 由於統計資料取樣是用來計算資料列大小的平均縮減，所以請將它當做預估就好。 在少數情況下，當您啟用 Vardecimal 儲存格式之後，資料列大小可能會增加。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 請改用 ROW 和 PAGE 壓縮。 如需詳細資訊，請參閱 [Data Compression](../../relational-databases/data-compression/data-compression.md)。 壓縮的資料表和索引大小的效果，請參閱 < [sp_estimate_data_compression_savings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_estimated_rowsize_reduction_for_vardecimal [ [ @table_name = ] 'table'] [;]  
```  
  
## <a name="arguments"></a>引數  
`[ @table = ] 'table'` 是三部分名稱的變更儲存格式的資料表。 *表格*已**nvarchar(776)** 。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 系統會傳回下列結果集，以便提供目前和預估的資料表大小資訊。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**avg_rowlen_fixed_format**|**十進位 （12，2）**|以自動設定小數點儲存格式表示資料列的長度。|  
|**avg_rowlen_vardecimal_format**|**十進位 （12，2）**|表示使用 Vardecimal 儲存格式時的平均資料列大小。|  
|**row_count**|**int**|資料表中的資料列數。|  
  
## <a name="remarks"></a>備註  
 使用**sp_estimated_rowsize_reduction_for_vardecimal**來預估，因此，如果您啟用 vardecimal 儲存格式資料表產生的節省程度。 例如，如果資料列的平均大小可縮減 40%，您就可能會將資料表的大小縮減 40%。 根據填滿因數和資料列的大小而定，您可能無法節省空間。 例如，如果您有一個長度為 8000 個位元組的資料列，而且將它的大小縮減 40%，則仍然只能在資料頁面上容納一個資料列，而不會節省任何空間。  
  
 如果結果**sp_estimated_rowsize_reduction_for_vardecimal**指示資料表將會成長，這表示在資料表中的多個資料列，使用幾乎完整有效位數 decimal 資料類型，並加入這個微小vardecimal 儲存格式所需的額外負荷會比 vardecimal 儲存格式的空間節省更大。 在這種少數情況下，請勿啟用 Vardecimal 儲存格式。  
  
 如果資料表已啟用 vardecimal 儲存格式，使用**sp_estimated_rowsize_reduction_for_vardecimal**來估計的資料列平均大小，如果已停用 vardecimal 儲存格式。  
  
## <a name="permissions"></a>Permissions  
 需要資料表的 CONTROL 權限。  
  
## <a name="examples"></a>範例  
 下列範例會預估資料列大小縮減 (如果 `Production.WorkOrderRouting` 資料庫中的 `AdventureWorks2012` 資料表進行壓縮的話)。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimated_rowsize_reduction_for_vardecimal 'Production.WorkOrderRouting' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_db_vardecimal_storage_format &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)   
 [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
