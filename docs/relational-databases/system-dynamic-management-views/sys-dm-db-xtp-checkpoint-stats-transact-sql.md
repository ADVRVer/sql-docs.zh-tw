---
title: sys.databases dm_db_xtp_checkpoint_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_checkpoint_stats
- dm_db_xtp_checkpoint_stats_TSQL
- sys.dm_db_xtp_checkpoint_stats
- sys.dm_db_xtp_checkpoint_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_checkpoint_stats dynamic management view
ms.assetid: 8d0b18ca-db4d-4376-9905-3e4457727c46
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 84cbfafdba3bca9b06f250ed9996f0a87e71a18c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68026863"
---
# <a name="sysdm_db_xtp_checkpoint_stats-transact-sql"></a>sys.dm_db_xtp_checkpoint_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  傳回有關目前資料庫的記憶體中 OLTP 檢查點作業的統計資料。 如果資料庫沒有記憶體中 OLTP 物件，則傳回空的結果集。  
  
 如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  
```  
USE In_Memory_db_name
SELECT * FROM sys.dm_db_xtp_checkpoint_stats;  
```  
  
**[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]與較新的版本截然不同，並在[SQL Server 2014](#bkmk_2014)的主題中加以討論。**
  
## <a name="sssql15-and-later"></a>[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 及更新版本  
 下表描述中`sys.dm_db_xtp_checkpoint_stats`的資料行，從開始**[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]**。  
  
|資料行名稱|類型|描述|  
|-----------------|----------|-----------------|  
|last_lsn_processed|**bigint**|控制器看到的最後一個 LSN。|  
|end_of_log_lsn|**數位（38）**|記錄結尾的 LSN。|  
|bytes_to_end_of_log|**bigint**|控制器未處理的記錄檔位元組，對應于和`last_lsn_processed` `end_of_log_lsn`之間的位元組。|  
|log_consumption_rate|**bigint**|控制器的交易記錄耗用量速率（KB/秒）。|  
|active_scan_time_in_ms|**bigint**|控制器在主動掃描交易記錄時所花費的時間。|  
|total_wait_time_in_ms|**bigint**|控制器的累計等候時間，而不是掃描記錄檔。|  
|waits_for_io|**bigint**|控制器執行緒所產生之記錄 IO 的等候次數。|  
|io_wait_time_in_ms|**bigint**|控制器執行緒在等候記錄 IO 時所花費的累計時間。|  
|waits_for_new_log_count|**bigint**|控制器執行緒為產生新記錄而產生的等候次數。|  
|new_log_wait_time_in_ms|**bigint**|控制器執行緒等候新記錄檔所花費的累計時間。|  
|idle_attempts_count|**bigint**|控制器轉換成閒置狀態的次數。|  
|tx_segments_dispatched|**bigint**|控制器所看到並分派至序列化程式的區段數目。 區段是記錄的連續部分，可形成序列化的單位。 它目前的大小為 1 MB，但未來可能會變更。|  
|segment_bytes_dispatched|**bigint**|資料庫重新開機之後，由控制器發送至序列化程式的位元組總數。|  
|bytes_serialized|**bigint**|自資料庫重新開機後序列化的位元組總數。|  
|serializer_user_time_in_ms|**bigint**|序列化程式在使用者模式中所花費的時間。|  
|serializer_kernel_time_in_ms|**bigint**|序列化程式在核心模式中花費的時間。|  
|xtp_log_bytes_consumed|**bigint**|自資料庫重新開機後所耗用的記錄位元組總數。|  
|checkpoints_closed|**bigint**|自資料庫重新開機之後關閉的檢查點計數。|  
|last_closed_checkpoint_ts|**bigint**|最後關閉的檢查點的時間戳記。|  
|hardened_recovery_lsn|**數位（38）**|復原將會從這個 LSN 開始。|  
|hardened_root_file_guid|**uniqueidentifier**|因最後一個完成的檢查點而強化之根檔案的 GUID。|  
|hardened_root_file_watermark|**bigint**|**僅供內部**之用。 讀取根檔案的有效程度（這只是與內部相關的類型，稱為 BSN）。|  
|hardened_truncation_lsn|**數位（38）**|截中斷點的 LSN。|  
|log_bytes_since_last_close|**bigint**|從最後接近記錄結尾的位元組。|  
|time_since_last_close_in_ms|**bigint**|上次關閉檢查點之後的時間。|  
|current_checkpoint_id|**bigint**|目前正在將新的區段指派至此檢查點。 檢查點系統是管線。 目前的檢查點是要從中指派記錄的區段。 一旦達到限制，檢查點就會由控制器釋放，而新的則會建立為目前的。|  
|current_checkpoint_segment_count|**bigint**|目前檢查點中的區段計數。|  
|recovery_lsn_candidate|**bigint**|**僅限內部**。 當 current_checkpoint_id 關閉時，要挑選為 recoverylsn 的候選。|  
|outstanding_checkpoint_count|**bigint**|管線中等待關閉的檢查點數目。|  
|closing_checkpoint_id|**bigint**|結束檢查點的識別碼。<br /><br /> 序列化程式會以平行方式運作，因此一旦完成後，檢查點就會成為關閉執行緒所要關閉的候選。 但是關閉執行緒只能一次關閉一個，而且它必須是順序的，因此關閉的檢查點就是一個正則執行緒正在處理的。|  
|recovery_checkpoint_id|**bigint**|要在復原中使用的檢查點識別碼。|  
|recovery_checkpoint_ts|**bigint**|修復檢查點的時間戳記。|  
|bootstrap_recovery_lsn|**數位（38）**|啟動程式的復原 LSN。|  
|bootstrap_root_file_guid|**uniqueidentifier**|啟動程式之根檔案的 GUID。|  
|internal_error_code|**bigint**|任何控制器、序列化程式、關閉和合併執行緒所見到的錯誤。|
|bytes_of_large_data_serialized|**bigint**|已序列化的資料量。 |  
  
##  <a name="sssql14"></a><a name="bkmk_2014"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 下表描述中`sys.dm_db_xtp_checkpoint_stats`的資料行，適用**[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** 于。  
  
|資料行名稱|類型|描述|  
|-----------------|----------|-----------------|  
|log_to_process_in_bytes|**bigint**|執行緒目前的記錄序號 (LSN) 和記錄檔結束之間的記錄位元組數目。|  
|total_log_blocks_processed|**bigint**|伺服器啟動後處理的記錄區塊總數。|  
|total_log_records_processed|**bigint**|伺服器啟動後處理的記錄檔記錄總數。|  
|xtp_log_records_processed|**bigint**|伺服器啟動後已處理的記憶體中 OLTP 記錄檔記錄的總數。|  
|total_wait_time_in_ms|**bigint**|累計等候時間 (毫秒)。|  
|waits_for_io|**bigint**|記錄 IO 等候的數目。|  
|io_wait_time_in_ms|**bigint**|花在等候記錄 IO 的累計時間。|  
|waits_for_new_log|**bigint**|等候新記錄產生的數目。|  
|new_log_wait_time_in_ms|**bigint**|花在等候新記錄的累計時間。|  
|log_generated_since_last_checkpoint_in_bytes|**bigint**|自從上次記憶體中 OLTP 檢查點之後產生的記錄檔數量。|  
|ms_since_last_checkpoint|**bigint**|自從上次記憶體中 OLTP 檢查點之後的時間量 (以毫秒為單位)。|  
|checkpoint_lsn|**數值（38）**|與最後完成的記憶體中 OLTP 檢查點相關聯的復原記錄序號 (LSN)。|  
|current_lsn|**數值（38）**|目前正在處理的記錄檔記錄 LSN。|  
|end_of_log_lsn|**數值（38）**|記錄檔結束的 LSN。|  
|task_address|**varbinary(8)**|SOS_Task 的位址。 聯結 sys.dm_os_tasks 以尋找其他資訊。|  
  
## <a name="permissions"></a>權限  
 需要伺服器的 `VIEW DATABASE STATE` 權限。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體最佳化的資料表動態管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
