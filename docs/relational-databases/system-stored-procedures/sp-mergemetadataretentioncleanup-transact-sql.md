---
description: sp_mergemetadataretentioncleanup (Transact-SQL)
title: sp_mergemetadataretentioncleanup (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergemetadataretentioncleanup
- sp_mergemetadataretentioncleanup_TSQL
helpviewer_keywords:
- sp_mergemetadataretentioncleanup
ms.assetid: 4e8d6343-2a38-421d-a3f3-c37d437a0f88
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6f18a4f9357e3af6d9b120195dd13e187de95fd3
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535105"
---
# <a name="sp_mergemetadataretentioncleanup-transact-sql"></a>sp_mergemetadataretentioncleanup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  在 [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)、 [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)、 [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)、 [MSmerge_past_partition_mappings](../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)和 [MSmerge_current_partition_mappings](../../relational-databases/system-tables/msmerge-current-partition-mappings.md) 系統資料表中，執行中繼資料的手動清除。 這個預存程序執行於拓撲中的每個發行者和訂閱者。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_mergemetadataretentioncleanup [ [ @num_genhistory_rows = ] num_genhistory_rows OUTPUT ]  
    [ , [ @num_contents_rows = ] num_contents_rows OUTPUT ]   
    [ , [ @num_tombstone_rows = ] num_tombstone_rows OUTPUT ]   
    [ , [ @aggressive_cleanup_only = ] aggressive_cleanup_only ]  
```  
  
## <a name="arguments"></a>引數  
`[ @num_genhistory_rows = ] num_genhistory_rows OUTPUT` 傳回 [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md) 資料表中已清除的資料列數。 *num_genhistory_rows* 是 **int**，預設值是 **0**。  
  
`[ @num_contents_rows = ] num_contents_rows OUTPUT` 傳回 [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) 資料表中已清除的資料列數。 *num_contents_rows* 是 **int**，預設值是 **0**。  
  
`[ @num_tombstone_rows = ] num_tombstone_rows OUTPUT` 傳回 [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) 資料表中已清除的資料列數。 *num_tombstone_rows* 是 **int**，預設值是 **0**。  
  
`[ @aggressive_cleanup_only = ] aggressive_cleanup_only` 僅供內部使用。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]  
>  如果資料庫上有多個發行集，而且任何一個發行集使用無限期的發行保留期限，則執行 **sp_mergemetadataretentioncleanup** 不會清除資料庫的合併式複寫變更追蹤中繼資料。 因此，在使用無限期的發行期限時，一定要特別小心。 若要判斷發行集是否有無限的保留期限，請在「發行者」端執行 [sp_helpmergepublication &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md) ，並記下結果集中的任何發行集值為 **0** 的發行集，以進行 **保留**。  
  
## <a name="permissions"></a>權限  
 只有 **db_owner** 固定資料庫角色的成員，或已發行資料庫之發行集存取清單中的使用者，才能夠執行 **sp_mergemetadataretentioncleanup**。  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
