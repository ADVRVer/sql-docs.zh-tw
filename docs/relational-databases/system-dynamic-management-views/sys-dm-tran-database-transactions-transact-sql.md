---
title: sys.dm_tran_database_transactions (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_tran_database_transactions
- sys.dm_tran_database_transactions_TSQL
- dm_tran_database_transactions_TSQL
- sys.dm_tran_database_transactions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_database_transactions dynamic management view
ms.assetid: 82a44295-4cbc-4a5b-891a-8ebaf307b8f5
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 311dcb091fe7198bc52794b3a7212ed3d8e812c7
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmtrandatabasetransactions-transact-sql"></a>sys.dm_tran_database_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回有關資料庫層級之交易的資訊。  
  
> [!NOTE]  
>  若要呼叫從這個 DMV[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名稱**sys.dm_pdw_nodes_tran_database_transactions**。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|transaction_id|**bigint**|執行個體層級 (而非資料庫層級) 的交易識別碼。 它只有在一個執行個體的所有資料庫才是唯一的，在所有的伺服器執行個體則不是。|  
|database_id|**int**|與交易相關聯的資料庫識別碼。|  
|database_transaction_begin_time|**datetime**|資料庫變成與交易有關的時間。 尤其，它是資料庫中針對交易的第一筆記錄的時間。|  
|database_transaction_type|**int**|1 = 讀取/寫入交易<br /><br /> 2 = 唯讀交易<br /><br /> 3 = 系統交易|  
|database_transaction_state|**int**|1 = 交易未初始化。<br /><br /> 3 = 交易已初始化，但未產生任何記錄。<br /><br /> 4 = 交易已產生記錄。<br /><br /> 5 = 已準備交易。<br /><br /> 10 = 已認可交易。<br /><br /> 11 = 已回復交易。<br /><br /> 12 = 正在認可交易。 （在記錄檔記錄正在產生，但尚未具體化或保存。）|  
|database_transaction_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|database_transaction_status2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|database_transaction_log_record_count|**bigint**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 在資料庫中針對交易產生的記錄數。|  
|database_transaction_replicate_record_count|**int**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 在資料庫中的交易都會複寫產生的記錄檔記錄數目。|  
|database_transaction_log_bytes_used|**bigint**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 到目前為止在資料庫記錄中針對交易所使用的位元組數。|  
|database_transaction_log_bytes_reserved|**bigint**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 在資料庫記錄中針對交易所使用而保留的位元組數。|  
|database_transaction_log_bytes_used_system|**int**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 到目前為止在資料庫記錄中針對代表交易之系統交易所使用的位元組數。|  
|database_transaction_log_bytes_reserved_system|**int**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 在資料庫記錄中針對代表交易之系統交易所使用而保留的位元組數。|  
|database_transaction_begin_lsn|**numeric(25,0)**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 資料庫記錄中交易之開始記錄的記錄序號 (LSN)。|  
|database_transaction_last_lsn|**numeric(25,0)**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 資料庫記錄中交易之最近記錄的 LSN。|  
|database_transaction_most_recent_savepoint_lsn|**numeric(25,0)**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 資料庫記錄中交易之最近儲存點的 LSN。|  
|database_transaction_commit_lsn|**numeric(25,0)**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 資料庫記錄中交易之認可記錄的 LSN。|  
|database_transaction_last_rollback_lsn|**numeric(25,0)**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 最近回復的 LSN。 如果有不發生任何復原，值會是 MaxLSN。|  
|database_transaction_next_undo_lsn|**numeric(25,0)**|**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 要恢復之下一筆記錄的 LSN。|  
|pdw_node_id|**int**|**適用於**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此發行版本上的節點識別碼。|  
  
## <a name="permissions"></a>Permissions

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`資料庫的權限。   

## <a name="see-also"></a>另請參閱  
 [sys.dm_tran_active_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-transactions-transact-sql.md)   
 [sys.dm_tran_session_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-session-transactions-transact-sql.md)   
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [交易相關的動態管理檢視和函數 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


