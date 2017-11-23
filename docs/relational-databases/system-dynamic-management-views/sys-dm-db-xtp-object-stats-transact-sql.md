---
title: "sys.dm_db_xtp_object_stats (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 08/29/2016
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
- dm_db_xtp_object_stats_TSQL
- sys.dm_db_xtp_object_stats
- dm_db_xtp_object_stats
- sys.dm_db_xtp_object_stats_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_xtp_object_stats dynamic management view
ms.assetid: 07300b59-3cab-4d3e-8138-5ea8f584f88f
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b07eb152c42c2f9c991d99ff6e3256b62d1cef8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbxtpobjectstats-transact-sql"></a>sys.dm_db_xtp_object_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  報告自從上一次資料庫重新啟動之後，受到每個 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 物件上的作業所影響的資料列數。 不論交易是否認可還是已經回復，執行此作業時都會更新統計資料。  
  
 sys.dm_db_xtp_object_stats 可幫助您識別哪些記憶體最佳化資料表有最大的改變。 您可能會決定移除資料表上未使用或不常使用的索引，因為每個索引都會影響效能。 如果有雜湊索引，您應該定期重新評估貯體計數。 如需詳細資訊，請參閱[判斷雜湊索引的正確值區計數](http://msdn.microsoft.com/library/6d1ac280-87db-4bd8-ad43-54353647d8b5)。  
  
 sys.dm_db_xtp_object_stats 可幫助您識別哪些記憶體最佳化資料表導致了寫入-寫入衝突，這些衝突可能會影響應用程式的效能。 例如，如果您有交易重試邏輯，相同的陳述式可能必須執行一次以上。 此外，您可以使用這項資訊來識別需要處理寫入-寫入錯誤的資料表 (以及商務邏輯)。  
  
 此檢視表會針對資料庫中每個記憶體最佳化的資料表，各包含一個資料列。  
  
 如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  
||  
|-|  
|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。|  
  
|資料行名稱|資料類型|說明|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|物件的識別碼。|  
|row_insert_attempts|**bigint**|上一次資料庫重新啟動之後，由認可和中止的交易插入資料表中的資料列數。|  
|row_update_attempts|**bigint**|上一次資料庫重新啟動之後，由認可和中止的交易在資料表中更新的資料列數。|  
|row_delete_attempts|**bigint**|上一次資料庫重新啟動之後，由認可和中止的交易從資料表中刪除的資料列數。|  
|write_conflicts|**bigint**|上一次資料庫重新啟動之後發生的寫入衝突數目。|  
|unique_constraint_violations|**bigint**|上一次資料庫重新啟動之後發生的唯一條件約束違規數目。|  
|object_address|**varbinary （8)**|僅供內部使用。|  
  
## <a name="permissions"></a>Permissions  
 需要目前資料庫的 VIEW DATABASE STATE 權限。  
  
## <a name="see-also"></a>請參閱＜  
 [記憶體最佳化的資料表動態管理檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
