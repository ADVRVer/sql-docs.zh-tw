---
title: "sys.dm_db_fts_index_physical_stats (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_fts_index_physical_stats_TSQL
- dm_db_fts_index_physical_stats
- dm_db_fts_index_physical_stats_TSQL
- sys.dm_db_fts_index_physical_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_fts_index_physical_stats dynamic management view
ms.assetid: 997c3278-3630-47f6-ada3-190b6c16ce0e
caps.latest.revision: "9"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 75bc9243e9867e7a3a27a78bac1361af9a099e84
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbftsindexphysicalstats-transact-sql"></a>sys.dm_db_fts_index_physical_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  針對具有相關聯全文檢索或語意索引的資料表中的每一個全文檢索或語意索引，各傳回一個資料列。  
  
||  
|-|  
|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|  
  
||||  
|-|-|-|  
|**資料行名稱**|**型別**|**說明**|  
|**object_id**|int|包含索引之資料表的物件識別碼。|  
|**fulltext_index_page_count**|**bigint**|擷取的邏輯大小 (索引頁數)。|  
|**keyphrase_index_page_count**|**bigint**|擷取的邏輯大小 (索引頁數)。|  
|**similarity_index_page_count**|**bigint**|擷取的邏輯大小 (索引頁數)。|  
  
## <a name="general-remarks"></a>一般備註  
 如需詳細資訊，請參閱[管理及監視語意搜尋](../../relational-databases/search/manage-and-monitor-semantic-search.md)。  
  
## <a name="metadata"></a>中繼資料  
 如需有關語意索引狀態的詳細資訊，請查詢下列動態管理檢視：  
  
-   [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="permissions"></a>Permissions  
在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]Premium 層需要`VIEW DATABASE STATE`資料庫的權限。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]標準和基本層，需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。  

  
## <a name="examples"></a>範例  
 下列範例示範如何針對每個有相關全文檢索或語意索引的資料表，查詢每個全文檢索或語意索引的邏輯大小：  
  
```  
SELECT * FROM sys.dm_db_fts_index_physical_stats;  
GO  
```  
  
## <a name="see-also"></a>請參閱＜  
 [管理及監視語意搜尋](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
