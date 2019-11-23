---
title: sys.databases dm_os_wait_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 05/16/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_wait_stats_TSQL
- dm_os_wait_stats
- sys.dm_os_wait_stats
- sys.dm_os_wait_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_wait_stats dynamic management view
ms.assetid: 568d89ed-2c96-4795-8a0c-2f3e375081da
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e274375177859d456592a6e1879d7f528d1cb724
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983087"
---
# <a name="sysdm_os_wait_stats-transact-sql"></a>sys.dm_os_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

傳回執行中之執行緒所遇到之所有等候的相關資訊。 您可以使用這份彙總檢視來診斷 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的效能問題，以及特定查詢和批次的效能問題。 [dm_exec_session_wait_stats &#40;transact-sql&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-session-wait-stats-transact-sql.md)依會話提供類似的資訊。  
  
> [!NOTE] 
> 若要從 **[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 或 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]** 呼叫此，請使用**dm_pdw_nodes_os_wait_stats**的名稱。  
  
|資料行名稱|[名稱]|描述|  
|-----------------|---------------|-----------------|  
|wait_type|**nvarchar(60)**|等候類型的名稱。 如需詳細資訊，請參閱本主題稍後的[等候類型](#WaitTypes)。|  
|waiting_tasks_count|**bigint**|這個等候類型的等候次數。 這個計數器是從每次開始等候時逐量遞增計算。|  
|wait_time_ms|**bigint**|這個等候類型的總等候時間 (以毫秒為單位)。 這個時間包括 signal_wait_time_ms 在內。|  
|max_wait_time_ms|**bigint**|這個等候類型的等候時間上限。|  
|signal_wait_time_ms|**bigint**|從等候執行緒接獲訊號到開始執行的時間。|  
|pdw_node_id|**int**|此散發所在節點的識別碼。 <br/> **適用于**： [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] |  
  
## <a name="permissions"></a>Permissions

在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上，需要 `VIEW SERVER STATE` 許可權。   
在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 高階層級上，需要資料庫中的 `VIEW DATABASE STATE` 許可權。 在 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 標準和基本層上，需要**伺服器管理員**或 Azure Active Directory 的系統**管理員**帳戶。   

##  <a name="WaitTypes"></a>等候的類型  
 **資源等候**當背景工作要求存取無法使用的資源時，就會發生資源等候，因為資源正由某個其他背景工作角色使用，或是尚未提供。 鎖定、閂鎖、網路和磁碟 I/O 等候，都是資源等候的範例。 鎖定和閂鎖等候是同步處理物件的等候。  
  
**佇列等候**  
 佇列等候發生在工作者因為等候指派工作而閒置時。 佇列等候大部分都是在進行系統背景工作 (例如，監視死結和刪除記錄清除工作) 時發生。 這些工作會等候工作要求被置於工作佇列。 即使沒有新的封包置於佇列中，佇列等候也可能會定期變成使用中狀態。  
  
 **外部等候**  
 外部等候是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作者正在等候外部事件 (例如，擴充預存程序呼叫或連結伺服器查詢) 完成時發生。 記住，當您診斷封鎖問題時，外部等候不會一直暗示工作者正在閒置，因為工作者可能很積極的在執行一些外部程式碼。  
  
 `sys.dm_os_wait_stats` 顯示已完成等候的時間。 此動態管理檢視不會顯示目前的等候。  
  
 在下列任何一種情況下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作者執行緒都不算是在等候中：  
  
-   資源可以使用。  
  
-   佇列不是空的。  
  
-   外部處理序完成。  
  
 雖然執行緒已經不在等候中，執行緒也不必立即開始執行。 因為這類執行緒會先置於可執行之工作者的佇列上，而且必須等候排程器執行某個配量才行。  
  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，等候時間計數器是**Bigint**值，因此不像舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的對等計數器一樣容易計數器變換。  
  
 在執行查詢時，特定類型的等候時間可以指出查詢中的瓶頸或拋錨點。 同樣地，等候時間很長或伺服器等候計數很大，也代表伺服器執行個體中互動查詢互動的瓶頸或熱點。 例如，鎖定等候表示查詢在競爭資料；資料頁 IO 閂鎖等候表示 IO 回應時間很慢；資料頁閂鎖更新等候表示檔案配置不正確。  
  
 您可以執行下列命令，重設這份動態管理檢視的內容：  
  
```sql  
DBCC SQLPERF ('sys.dm_os_wait_stats', CLEAR);  
GO  
```  
  
這個命令會將所有的計數器重設為 0。  
  
> [!NOTE]
> 這些統計資料在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新啟動之後都不會保存下來，而且所有的資料都是從上次統計資料重設或伺服器啟動之後開始累加計算。  
  
 下表列出工作會遇到的等候類型。  

|類型 |描述| 
|-------------------------- |--------------------------| 
|ABR |僅供參考之用。 不支援。 我們無法保證未來的相容性。| | 
|AM_INDBUILD_ALLOCATION |僅供內部使用。 <br />**適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|AM_SCHEMAMGR_UNSHARED_CACHE |僅供內部使用。 <br />**適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|ASSEMBLY_FILTER_HASHTABLE |僅供內部使用。 <br />**適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|ASSEMBLY_LOAD |在組件載入的獨佔存取期間發生。| 
|ASYNC_DISKPOOL_LOCK |在同步處理執行建立檔案，或者檔案初始化等工作的平行執行緒時發生。| 
|ASYNC_IO_COMPLETION |在工作等候 I/O 完成時發生。| 
|ASYNC_NETWORK_IO |當工作被封鎖在網路後面時，進行網路寫入就會發生這種情形。 請確認用戶端正在處理來自伺服器的資料。| 
|ASYNC_OP_COMPLETION |僅供內部使用。 <br />**適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|ASYNC_OP_CONTEXT_READ |僅供內部使用。 <br />**適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|ASYNC_OP_CONTEXT_WRITE |僅供內部使用。 <br />**適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|ASYNC_SOCKETDUP_IO |僅供內部使用。 <br />**適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|AUDIT_GROUPCACHE_LOCK |當控制特殊快取之存取權的鎖定上存在等候時發生。 此快取包含哪些稽核要用來稽核每個稽核動作群組的相關資訊。| 
|AUDIT_LOGINCACHE_LOCK |當控制特殊快取之存取權的鎖定上存在等候時發生。 此快取包含哪些稽核要用來稽核登入稽核動作群組的相關資訊。| 
|AUDIT_ON_DEMAND_TARGET_LOCK |當用來確保稽核相關「擴充事件」目標之單一初始化的鎖定上存在等候時發生。| 
|AUDIT_XE_SESSION_MGR |當用來同步處理稽核相關「擴充事件」工作階段之啟動和停止的鎖定上存在等候時發生。| 
|BACKUP |當工作被當做備份處理的一部分而加以封鎖時發生。| 
|BACKUP_OPERATOR |在工作等候磁帶掛載時發生。 若要查看磁帶狀態，請查詢 sys.databases dm_io_backup_tapes。 如果掛載作業沒有暫止，這個等候類型可能就表示磁帶機發生硬體問題。| 
|BACKUPBUFFER |當備份工作正在等候資料，或者等候儲存資料的緩衝區時發生。 除非當工作正在等候磁帶掛載，否則這個類型並非標準類型。| 
|BACKUPIO |當備份工作正在等候資料，或者等候儲存資料的緩衝區時發生。 除非當工作正在等候磁帶掛載，否則這個類型並非標準類型。| 
|BACKUPTHREAD |在工作等候備份工作完成時發生。 等候時間可能會很長，從幾分鐘到數小時都可能。 如果等候的工作是在 I/O 處理序中，這個類型就不表示發生問題。| 
|BAD_PAGE_PROCESS |當背景可疑頁面記錄器想要避免執行間隔超過每 5 秒一次時發生。 可疑頁面過多將導致記錄器經常執行。| 
|BLOB_METADATA |僅供內部使用。 <br />**適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|BMPALLOCATION |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br />**適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|BMPBUILD |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br />**適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|BMPREPARTITION |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|BMPREPLICATION |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|BPSORT |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|BROKER_CONNECTION_RECEIVE_TASK |在連接端點上等候接收訊息的存取權時發生。 端點的接收存取是序列化的。| 
|BROKER_DISPATCHER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|BROKER_ENDPOINT_STATE_MUTEX |當有爭用存取 Service Broker 連接端點的狀態時發生。 存取變更的狀態是序列化的。| 
|BROKER_EVENTHANDLER |當工作在 Service Broker 的主要事件處理常式中等候時發生。 發生的時間相當短暫。| 
|BROKER_FORWARDER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|BROKER_INIT |在每個使用中資料庫中初始化 Service Broker 時發生。 這種情況不常發生。| 
|BROKER_MASTERSTART |當工作在等候 Service Broker 的主要事件處理常式啟動時發生。 發生的時間相當短暫。| 
|BROKER_RECEIVE_WAITFOR |當 RECEIVE WAITFOR 在等候時發生。 這可能表示未準備好在佇列中接收任何訊息，或鎖定爭用導致無法接收來自佇列的訊息。| 
|BROKER_REGISTERALLENDPOINTS |在初始化 Service Broker 連接端點時發生。 發生的時間相當短暫。| 
|BROKER_SERVICE |當與目標服務相關聯的 Service Broker 目的地清單已更新或重新設定優先權時發生。| 
|BROKER_SHUTDOWN |Service Broker 計畫關閉時發生。 即使發生，時間也相當短暫。| 
|BROKER_START |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|BROKER_TASK_SHUTDOWN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|BROKER_TASK_STOP |Service Broker 佇列工作處理常式嘗試關閉工作時發生。 狀態檢查會序化列，而且必須事先處於執行中狀態。| 
|BROKER_TASK_SUBMIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|BROKER_TO_FLUSH |Service Broker lazy 清除器清除將記憶體中的傳輸物件排清至工作資料表時發生。| 
|BROKER_TRANSMISSION_OBJECT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|BROKER_TRANSMISSION_TABLE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|BROKER_TRANSMISSION_WORK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|BROKER_TRANSMITTER |當 Service Broker 發送器正在等候工作時發生。 Service Broker 有一個稱為「傳輸器」的元件，可將來自多個對話的訊息，排程在一或多個連接端點上透過網路傳送。 傳輸器有2個專門的執行緒可用於此用途。 當這些發送器執行緒正在等候對話訊息使用傳輸連接來傳送時，就會收取此等候類型的費用。 此等候類型的 waiting_tasks_count 的高值指向這些發送器執行緒的間歇性工作，而且不會指出任何效能問題。 如果完全沒有使用 service broker，waiting_tasks_count 應該是2（針對2個發送器執行緒），而 wait_time_ms 應該是實例啟動後的兩倍。 請參閱[Service broker 等候統計](https://blogs.msdn.microsoft.com/sql_service_broker/2008/12/01/service-broker-wait-types)資料。|
|BUILTIN_HASHKEY_MUTEX |可能在啟動執行個體之後，而內部資料結構正在初始化時發生。 資料結構初始化之後就不會再次發生。| 
|CHANGE_TRACKING_WAITFORCHANGES |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|CHECK_PRINT_RECORD |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|CHECK_SCANNER_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|CHECK_TABLES_INITIALIZATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|CHECK_TABLES_SINGLE_SCAN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|CHECK_TABLES_THREAD_BARRIER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|CHECKPOINT_QUEUE |當檢查點工作在等候下一個檢查點要求時發生。| 
|CHKPT |在伺服器啟動時發生，目的在告知檢查點執行緒，它可以啟動了。| 
|CLEAR_DB |在變更資料庫狀態的作業期間發生，例如開啟或關閉資料庫。| 
|CLR_AUTO_EVENT |當工作目前在執行 Common Language Runtime (CLR) 執行，以及在等候特定自動事件起始時發生。 等候時間長是正常情況，並不表示發生任何問題。| 
|CLR_CRST |當工作目前正在執行 CLR 執行，以及正在等候進入目前正被另一個工作使用中之工作的重要區段時發生。| 
|CLR_JOIN |當工作目前正在執行 CLR 執行，以及正在等候另一個工作結束時發生。 這個等候狀態是在工作之間有聯結時發生。| 
|CLR_MANUAL_EVENT |當工作目前正在執行 CLR 執行，以及正在等候特定的手動事件起始時發生。| 
|CLR_MEMORY_SPY |在用來記錄來自 CLR 之所有虛擬記憶體配置的資料結構等候取得鎖定期間發生。 如果存在平行存取，資料結構就會鎖定，以便維持其完整性。| 
|CLR_MONITOR |當工作目前正在執行 CLR 執行，以及正在等候取得監視器鎖定時發生。| 
|CLR_RWLOCK_READER |當工作目前正在執行 CLR 執行，以及正在等候讀取器鎖定時發生。| 
|CLR_RWLOCK_WRITER |當工作目前正在執行 CLR 執行，以及正在等候寫入器鎖定時發生。| 
|CLR_SEMAPHORE |當工作目前正在執行 CLR 執行，以及正在等候信號時發生。| 
|CLR_TASK_START |在等候 CLR 工作完成啟動時發生。| 
|CLRHOST_STATE_ACCESS |在等候取得 CLR 主控資料結構之獨佔存取權的情況下發生。 這種等候類型會在設定或終止 CLR 執行階段時發生。| 
|CMEMPARTITIONED |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|CMEMTHREAD |當工作在安全執行緒記憶體物件待命時發生。 如果有多個工作嘗試從同一個記憶體物件配置記憶體而導致競爭情形時，等候時間可能會增加。| 
|COLUMNSTORE_BUILD_THROTTLE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|COLUMNSTORE_COLUMNDATASET_SESSION_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|COMMIT_TABLE |僅供內部使用。| 
|CONNECTION_ENDPOINT_LOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|COUNTRECOVERYMGR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|CREATE_DATINISERVICE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|CXCONSUMER |當取用者執行緒等候生產者執行緒傳送資料列時，會發生平行查詢計劃。 這是平行查詢執行的正常部分。 <br /> **適用于**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] （從 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 開始，[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3），[!INCLUDE[ssSDS](../../includes/sssds-md.md)]|
|CXPACKET |在同步處理查詢處理器交換反覆運算器，以及產生和取用資料列時，會發生平行查詢計劃。 如果等候時間過長，而且無法透過微調查詢 (例如加入索引) 來縮短，請考慮調整平行處理原則的成本臨界值，或降低平行處理原則的程度。<br /> **注意：** 從 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2、[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 和 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]開始，CXPACKET 只是指同步處理查詢處理器交換反覆運算器，並為取用者執行緒產生資料列。 取用者執行緒會在 CXCONSUMER 等候類型中分開追蹤。| 
|CXROWSET_SYNC |在平行範圍掃描期間發生。| 
|DAC_INIT |當專用管理員連接正在初始化時發生。| 
|DBCC_SCALE_OUT_EXPR_CACHE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|DBMIRROR_DBM_EVENT |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|DBMIRROR_DBM_MUTEX |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|DBMIRROR_EVENTS_QUEUE |當資料庫鏡像在等候處理事件時發生。| 
|DBMIRROR_SEND |當工作在網路層等候通訊積存清除，以傳送訊息時發生。 它指出通訊層已經開始多載，並影響到資料庫鏡像資料輸送量。| 
|DBMIRROR_WORKER_QUEUE |指出資料庫鏡像工作者工作正在等候其他工作。| 
|DBMIRRORING_CMD |當工作在等候記錄排清到磁碟時發生。 這個等候狀態預期會保留一段很長的時間。| 
|DBSEEDING_FLOWCONTROL |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|DBSEEDING_OPERATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|DEADLOCK_ENUM_MUTEX |當鎖死監視器和 sys dm_os_waiting_tasks 嘗試確定 SQL Server 不會同時執行多個鎖死搜尋時發生。| 
|DEADLOCK_TASK_SEARCH |在此資源上的等候時間如果很長，表示伺服器正在 sys.dm_os_waiting_tasks 之上執行查詢，而這些查詢則造成死結監視器無法執行死結搜尋。 只有死結監視器才會使用這種等候類型。 在 sys.dm_os_waiting_tasks 之上的查詢會使用 DEADLOCK_ENUM_MUTEX。| 
|DEBUG |在 Transact-sql 和 CLR 偵錯工具進行內部同步處理時發生。| 
|DIRECTLOGCONSUMER_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|DIRTY_PAGE_POLL |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|DIRTY_PAGE_SYNC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|DIRTY_PAGE_TABLE_LOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|DISABLE_VERSIONING |當 SQL Server 輪詢版本交易管理員，查看最早使用中交易的時間戳記是否晚于狀態開始變更時的時間戳記時，就會發生。 如果是這樣，則表示所有在 ALTER DATABASE 陳述式執行之前所啟動的快照集交易，已經全部完成了。 當 SQL Server 使用 ALTER DATABASE 語句來停用版本控制時，就會使用這個等候狀態。| 
|DISKIO_SUSPEND |當外部備份在使用中時，工作正在等候存取檔案時發生。 這是針對每個等候中的使用者處理序所報告。 如果超過每個使用者處理序五次時，可能表示外部備份花了太多時間才完成。| 
|DISPATCHER_PRIORITY_QUEUE_SEMAPHORE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|DISPATCHER_QUEUE_SEMAPHORE |當發送器集區的執行緒正在等候處理其他工作時發生。 這種等候類型的等候時間應該會在發送器閒置時增加。| 
|DLL_LOADING_MUTEX |在等候 XML 剖析器 DLL 載入時發生一次。| 
|DPT_ENTRY_LOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|DROP_DATABASE_TIMER_TASK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|DROPTEMP |卸除暫存物件時，如果前一次的嘗試失敗，就會在兩次嘗試之間發生這種等候類型。 等候持續時間將以指數方式，隨著每一次的卸除嘗試失敗而增加。| 
|DTC |當工作在服務管理狀態轉移所用的事件時發生。 此狀態控制在收到 MS DTC 服務無法使用的通知 SQL Server 之後，Microsoft 分散式交易協調器（MS DTC）交易的復原時機。| 
|DTC_ABORT_REQUEST |當工作階段在等候接收 MS DTC 交易的擁有權時，在 MS DTC 工作者工作階段發生。 MS DTC 擁有交易之後，工作階段就可以回復該交易。 通常，工作階段會等候另一個使用該交易的工作階段。| 
|DTC_RESOLVE |當復原工作在等候跨資料庫交易中的 master 資料庫，讓工作得以查詢交易結果時發生。| 
|DTC_STATE |當工作在保護您對內部 MS DTC 全域狀態物件所做變更的事件待命時發生。 這個狀態的保留時間很短。| 
|DTC_TMDOWN_REQUEST |當 SQL Server 收到 MS DTC 服務無法使用的通知時，在 MS DTC 背景工作會話中發生。 首先，工作者會等候 MS DTC 復原處理序啟動。 接著，工作者會等候取得他所處理的分散式交易結果。 除非與 MS DTC 服務的連接已經重新建立，否則這項作業會繼續進行。| 
|DTC_WAITFOR_OUTCOME |當復原工作在等候 MS DTC 開始解析準備交易時發生。| 
|DTCNEW_ENLIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|DTCNEW_PREPARE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|DTCNEW_RECOVERY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|DTCNEW_TM |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|DTCNEW_TRANSACTION_ENLISTMENT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|DTCPNTSYNC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|DUMP_LOG_COORDINATOR |當主要工作正在等候子工作產生資料時發生。 這個狀態通常不會發生。 如果等候時間很長，就表示發生了非預期的封鎖。 您最好調查一下子工作。| 
|DUMP_LOG_COORDINATOR_QUEUE |僅供內部使用。| 
|DUMPTRIGGER |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|EC |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|EE_PMOLOCK |在陳述式執行期間同步處理某些類型的記憶體配置時發生。| 
|EE_SPECPROC_MAP_INIT |在同步處理內部程序雜湊表的建立時發生。 只有在 SQL Server 實例啟動之後，初始存取雜湊資料表時，才會發生這種等候。| 
|ENABLE_EMPTY_VERSIONING |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|ENABLE_VERSIONING |當 SQL Server 等候這個資料庫中的所有更新交易完成，然後才宣告資料庫準備好轉換成快照隔離允許狀態時，就會發生這種情況。 當 SQL Server 使用 ALTER DATABASE 語句來啟用快照集隔離時，會使用此狀態。| 
|ERROR_REPORTING_MANAGER |在同步處理多個並行錯誤記錄檔的初始化時發生。| 
|EXCHANGE |在平行查詢期間同步處理查詢處理器交換重複時發生。| 
|EXECSYNC |平行查詢期間在與交換重複無關之區域的查詢處理器中進行同步處理時發生。 這類區域的範例包括點陣圖、大型二進位物件 (LOB) 和多工緩衝處理重複。 LOB 可能會經常使用這個等候狀態。| 
|EXECUTION_PIPE_EVENT_INTERNAL |在透過連接內容傳送的批次執行產生者與取用者部分之間同步處理期間發生。| 
|EXTERNAL_RG_UPDATE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|EXTERNAL_SCRIPT_NETWORK_IO |僅供內部使用。 <br /> **適用**于：透過 current [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]。| 
|EXTERNAL_SCRIPT_PREPARE_SERVICE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|EXTERNAL_SCRIPT_SHUTDOWN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|EXTERNAL_WAIT_ON_LAUNCHER、 |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|FABRIC_HADR_TRANSPORT_CONNECTION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|FABRIC_REPLICA_CONTROLLER_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|FABRIC_REPLICA_CONTROLLER_STATE_AND_CONFIG |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|FABRIC_REPLICA_PUBLISHER_EVENT_PUBLISH |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|FABRIC_REPLICA_PUBLISHER_SUBSCRIBER_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|FABRIC_WAIT_FOR_BUILD_REPLICA_EVENT_PROCESSING |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|FAILPOINT |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|FCB_REPLICA_READ |在同步處理快照集 (或 DBCC 所建立的暫時快照集) 疏鬆檔案的讀取作業時發生。| 
|FCB_REPLICA_WRITE |在同步處理將資料頁發送或提取到快照集 (或 DBCC 所建立的暫時快照集) 疏鬆檔案時發生。| 
|FEATURE_SWITCHES_UPDATE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|FFT_NSO_DB_KILL_FLAG |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_NSO_DB_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_NSO_FCB |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_NSO_FCB_FIND |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_NSO_FCB_PARENT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_NSO_FCB_RELEASE_CACHED_ENTRIES |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_NSO_FCB_STATE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|FFT_NSO_FILEOBJECT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_NSO_TABLE_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_NTFS_STORE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_RECOVERY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_RSFX_COMM |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_RSFX_WAIT_FOR_MEMORY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_STARTUP_SHUTDOWN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_STORE_DB |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_STORE_ROWSET_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FFT_STORE_TABLE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FILE_VALIDATION_THREADS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|FILESTREAM_CACHE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FILESTREAM_CHUNKER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FILESTREAM_CHUNKER_INIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FILESTREAM_FCB |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FILESTREAM_FILE_OBJECT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FILESTREAM_WORKITEM_QUEUE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FILETABLE_SHUTDOWN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FOREIGN_REDO |僅供內部使用。 <br /> **適用**于：透過 current [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]。| 
|FORWARDER_TRANSITION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|FS_FC_RWLOCK |當 FILESTREAM 記憶體回收行程等候進行下列其中一項作業時發生：| 
|FS_GARBAGE_COLLECTOR_SHUTDOWN |當 FILESTREAM 記憶體回收行程正在等候清除工作完成時發生。| 
|FS_HEADER_RWLOCK |當系統等候取得 FILESTREAM 資料容器之 FILESTREAM 標頭的存取權來讀取或更新 FILESTREAM 標頭檔 (Filestream.hdr) 內容時發生。| 
|FS_LOGTRUNC_RWLOCK |當系統等候取得 FILESTREAM 記錄截斷的存取權來進行下列其中一項作業時發生：| 
|FSA_FORCE_OWN_XACT |當 FILESTREAM 檔案 I/O 作業需要繫結至相關聯的交易，但是此交易目前由其他工作階段所擁有時發生。| 
|FSAGENT |當 FILESTREAM 檔案 I/O 作業正在等候其他檔案 I/O 作業所使用的 FILESTREAM 代理程式資源時發生。| 
|FSTR_CONFIG_MUTEX |當系統等候其他 FILESTREAM 功能重新設定完成時發生。| 
|FSTR_CONFIG_RWLOCK |當系統等候序列化 FILESTREAM 組態參數的存取權時發生。| 
|FT_COMPROWSET_RWLOCK |全文檢索正在等候片段中繼資料作業。 記載僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|FT_IFTS_RWLOCK |全文檢索正在等候內部的同步處理。 記載僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|FT_IFTS_SCHEDULER_IDLE_WAIT |全文檢索排程器睡眠等候類型。 排程器閒置中。| 
|FT_IFTSHC_MUTEX |全文檢索正在等候 fdhost 控制項作業。 記載僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|FT_IFTSISM_MUTEX |全文檢索正在等候通訊作業。 記載僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|FT_MASTER_MERGE |全文檢索正在等候主要合併作業。 記載僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|FT_MASTER_MERGE_COORDINATOR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FT_METADATA_MUTEX |記載僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|FT_PROPERTYLIST_CACHE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|FT_RESTART_CRAWL |在全文檢索搜耙必須從最後一個已知的恰當起點重新啟動以便從暫時性失敗中復原時發生。 等候可讓目前正在處理該母體擴展的工作者工作得以完成或結束目前的步驟。| 
|FULLTEXT GATHERER |在同步處理全文檢索作業時發生。| 
|GDMA_GET_RESOURCE_OWNER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|GHOSTCLEANUP_UPDATE_STATS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|GHOSTCLEANUPSYNCMGR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|GLOBAL_QUERY_CANCEL |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|GLOBAL_QUERY_CLOSE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|GLOBAL_QUERY_CONSUMER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|GLOBAL_QUERY_PRODUCER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|GLOBAL_TRAN_CREATE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|GLOBAL_TRAN_UCS_SESSION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|GUARDIAN |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|HADR_AG_MUTEX |在 Always On DDL 語句或 Windows Server 容錯移轉叢集命令等候可用性群組的設定獨佔讀取/寫入權限時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_AR_CRITICAL_SECTION_ENTRY |在 Always On DDL 語句或 Windows Server 容錯移轉叢集命令等候關聯可用性群組的本機複本之執行時間狀態的獨佔讀取/寫入存取時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_AR_MANAGER_MUTEX |在可用性複本關閉等候啟動完成或者可用性複本啟動等候關閉完成時發生。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_AR_UNLOAD_COMPLETED |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_ARCONTROLLER_NOTIFICATIONS_SUBSCRIBER_LIST |可用性複本事件 (例如狀態變更或組態變更) 的發行者正在等候事件訂閱者清單的獨佔讀取/寫入存取權。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_BACKUP_BULK_LOCK |Always On 主資料庫收到來自次要資料庫的備份要求，而且正在等候背景執行緒完成取得或釋放 BulkOp 鎖定的要求處理。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_BACKUP_QUEUE |Always On 主資料庫的備份背景執行緒正在等候來自次要資料庫的新工作要求。 （一般而言，當主資料庫持有 BulkOp 記錄，而且正在等候次要資料庫指出主資料庫可以釋放鎖定）時，就會發生這種情況。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_CLUSAPI_CALL |SQL Server 執行緒正在等候從非先占式模式（由 SQL Server 排程）切換為先占式模式（由作業系統排程），以便叫用 Windows Server 容錯移轉叢集 Api。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_COMPRESSED_CACHE_SYNC |等待存取壓縮記錄檔區塊的快取，以避免對傳送至多個次要資料庫的記錄區塊進行重複的壓縮。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_CONNECTIVITY_INFO |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DATABASE_FLOW_CONTROL |在已達佇列訊息的數目上限時，等候要傳送至夥伴的訊息。 表示記錄掃描的執行速度比網路傳送的速度要快。 只有當網路傳送速度比預期慢時，才會發生此問題。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DATABASE_VERSIONING_STATE |在 Always On 次要資料庫的版本設定狀態變更時發生。 這種等候適用于內部資料結構，而且通常非常短，而且不會直接影響資料存取。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DATABASE_WAIT_FOR_RECOVERY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_DATABASE_WAIT_FOR_RESTART |正在等候資料庫在 Always On 可用性群組控制之下重新開機。 在正常情況下，這不是客戶問題，因為這裡應該會有等待。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DATABASE_WAIT_FOR_TRANSITION_TO_VERSIONING |當次要複本已啟用讀取工作負載時，資料列版本設定會封鎖在 Always On 可用性群組之可讀取的次要資料庫中，對物件進行的查詢。 這種等候類型保證在快照集隔離下執行查詢之前，可以使用資料列版本。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DB_COMMAND |等候交談訊息的回應（這需要另一端的明確回應，使用 Always On 對話訊息基礎結構）。 有數種不同的訊息類型會使用這種等候類型。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DB_OP_COMPLETION_SYNC |等候交談訊息的回應（這需要另一端的明確回應，使用 Always On 對話訊息基礎結構）。 有數種不同的訊息類型會使用這種等候類型。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DB_OP_START_SYNC |Always On DDL 語句或 Windows Server 容錯移轉叢集命令正在等候可用性資料庫及其執行時間狀態的序列化存取。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DBR_SUBSCRIBER |可用性複本事件 (例如狀態變更或組態變更) 的發行者正在等候對應至可用性資料庫之事件訂閱者執行階段狀態的獨佔讀取/寫入存取權。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DBR_SUBSCRIBER_FILTER_LIST |可用性複本事件 (例如狀態變更或組態變更) 的發行者正在等候對應至可用性資料庫之事件訂閱者清單的獨佔讀取/寫入存取權。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_DBSEEDING |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|HADR_DBSEEDING_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|HADR_DBSTATECHANGE_SYNC |並行控制等候更新資料庫複本的內部狀態。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_FABRIC_CALLBACK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|HADR_FILESTREAM_BLOCK_FLUSH |FILESTREAM Always On 傳輸管理員正在等候，直到記錄區塊的處理完成為止。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_FILESTREAM_FILE_CLOSE |FILESTREAM Always On 傳輸管理員正在等候，直到下一個 FILESTREAM 檔案處理完畢，且其控制碼已關閉為止。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_FILESTREAM_FILE_REQUEST |Always On 次要複本正在等候主要複本在復原期間傳送所有要求的 FILESTREAM 檔案。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_FILESTREAM_IOMGR |FILESTREAM Always On 傳輸管理員正在等候 R/W 鎖定，以便在啟動或關閉期間保護 FILESTREAM Always On i/o 管理員。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_FILESTREAM_IOMGR_IOCOMPLETION |FILESTREAM Always On i/o 管理員正在等候 i/o 完成。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_FILESTREAM_MANAGER |FILESTREAM Always On 傳輸管理員正在等候 R/W 鎖定，以便在啟動或關閉期間保護 FILESTREAM Always On 傳輸管理員。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_FILESTREAM_PREPROC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_GROUP_COMMIT |交易認可處理正在等候允許群組認可，以便將多個認可記錄檔記錄放入單一記錄檔區塊中。 這種等候是將記錄檔 i/o、capture 和 send 作業優化的預期條件。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_LOGCAPTURE_SYNC |有關建立或終結掃描時記錄擷取或套用物件的並行控制。 當合作夥伴變更狀態或連接狀態時，這是預期的等候。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_LOGCAPTURE_WAIT |等候記錄檔記錄變成可用。 如果讀取不在快取中的記錄，等候連接產生新的記錄檔記錄或 I/O 完成時就可能會發生這種狀況。 這是預期的等候，如果記錄檔掃描直到記錄檔的結尾或正在從磁片讀取。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_LOGPROGRESS_SYNC |更新資料庫複本的記錄進度狀態時，並行控制等候。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_NOTIFICATION_DEQUEUE |處理 Windows Server 容錯移轉叢集通知的背景工作正在等候下一個通知。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_NOTIFICATION_WORKER_EXCLUSIVE_ACCESS |Always On 可用性複本管理員正在等候處理 Windows Server 容錯移轉叢集通知之背景工作執行時間狀態的序列化存取。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_NOTIFICATION_WORKER_STARTUP_SYNC |背景工作正在等候處理 Windows Server 容錯移轉叢集通知的背景工作啟動完成。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_NOTIFICATION_WORKER_TERMINATION_SYNC |背景工作正在等候處理 Windows Server 容錯移轉叢集通知的背景工作終止。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_PARTNER_SYNC |夥伴清單上的並行控制等候。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_READ_ALL_NETWORKS |等候取得 WSFC 網路清單的讀取或寫入存取權。 僅供內部使用。 注意：引擎會保留用於動態管理檢視中的 WSFC 網路清單（例如 sys. dm_hadr_cluster_networks），或用來驗證參考 WSFC 網路資訊的 Always On Transact-sql 語句。 這份清單會在引擎啟動、WSFC 相關的通知和內部 Always On 重新開機（例如，失去和重新取得 WSFC 仲裁）時更新。 當該清單的更新正在進行時，通常會封鎖工作。 , <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_RECOVERY_WAIT_FOR_CONNECTION |等候次要資料庫在執行復原之前連接到主要資料庫。 這是預期的等候，如果與主要複本的連線速度很慢，則可能會延長。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_RECOVERY_WAIT_FOR_UNDO |資料庫復原正在等候次要資料庫完成還原和初始化階段，以便讓它返回與主要資料庫相同的記錄點。 這是在容錯移轉之後預期的等候。您可以透過 Windows 系統監視器（perfmon）和動態管理檢視來追蹤復原進度。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_REPLICAINFO_SYNC |正在等候並行存取控制更新目前的複本狀態。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_SEEDING_CANCELLATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_SEEDING_FILE_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_SEEDING_LIMIT_BACKUPS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_SEEDING_SYNC_COMPLETION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_SEEDING_TIMEOUT_TASK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_SEEDING_WAIT_FOR_COMPLETION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_SYNC_COMMIT |等候已同步處理之次要資料庫的交易認可處理強行寫入記錄。 Transaction Delay 效能計數器也會反映這項等候。 同步處理的可用性群組必須要有這種等候類型，並指出傳送、寫入和認可記錄到次要資料庫的時間。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_SYNCHRONIZING_THROTTLE |等候交易認可處理允許同步處理中的次要資料庫趕上主要記錄結尾，以便轉換成已同步處理的狀態。 當次要資料庫即將趕上時，這是預期的等候。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_TDS_LISTENER_SYNC |內部 Always On 系統或 WSFC 叢集會要求接聽程式已啟動或停止。 這項要求的處理方式一律為非同步，而且具有移除重複要求的機制。 此外，這個處理序有時候會由於組態變更而暫停。 與此接聽程式同步處理機制相關的所有等候都會使用此等候類型。 僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_TDS_LISTENER_SYNC_PROCESSING |在需要啟動和/或停止可用性群組接聽程式的 Always On Transact-sql 語句的結尾處使用。 由於啟動/停止作業是以非同步方式完成，使用者執行緒將會封鎖使用此等候類型，直到知道接聽程式的情況為止。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_THROTTLE_LOG_RATE_GOVERNOR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HADR_THROTTLE_LOG_RATE_MISMATCHED_SLO | 當異地複寫次要資料庫的計算大小（較低的 SLO）設定為低於主要複本時發生。 主資料庫因為次要的延遲記錄耗用量而受到節流。 這是因為次要資料庫的計算容量不足，而無法跟上主資料庫的變更率。 <br /> **適用**于： Azure SQL Database| 
|HADR_THROTTLE_LOG_RATE_LOG_SIZE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|HADR_THROTTLE_LOG_RATE_SEEDING |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|HADR_THROTTLE_LOG_RATE_SEND_RECV_QUEUE_SIZE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|HADR_TIMER_TASK |等候取得計時器工作物件的鎖定，而且也會用於工作執行間隔的實際等候。 例如，對於每隔10秒執行一次的工作，Always On 可用性群組會等待約10秒來重新排程工作，並在此包含等候。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_TRANSPORT_DBRLIST |等候傳輸層之資料庫複本清單的存取權。 用於授與存取權的 spinlock。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_TRANSPORT_FLOW_CONTROL |等待未完成的未認可 Always On 訊息數目超過輸出流量控制閾值時。 這是基於可用性複本到複本的基礎（不是以資料庫到資料庫為基礎）。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_TRANSPORT_SESSION |Always On 可用性群組正在等待變更或存取基礎傳輸狀態。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_WORK_POOL |並行控制等候 Always On 可用性群組背景工作物件。， <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_WORK_QUEUE |Always On 可用性群組背景工作者執行緒，等待指派新工作。 當備妥的工作者等待新工作（也就是正常狀態）時，這是預期的等候。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HADR_XRF_STACK_ACCESS |存取（查閱、加入和刪除） Always On 可用性資料庫的擴充復原分支堆疊。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HCCO_CACHE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HK_RESTORE_FILEMAP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HKCS_PARALLEL_MIGRATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HKCS_PARALLEL_RECOVERY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|HTBUILD |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HTDELETE |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|HTMEMO |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|HTREINIT |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|HTREPARTITION |在同步處理在批次模式運算子內輸入不同處理階段的執行緒時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|HTTP_ENUMERATION |在啟動以列舉 HTTP 端點來啟動 HTTP 時發生。| 
|HTTP_START |在連接等候 HTTP 完成初始化時發生。| 
|HTTP_STORAGE_CONNECTION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|IMPPROV_IOWAIT |當 SQL Server 等候 bulkload i/o 完成時發生。| 
|INSTANCE_LOG_RATE_GOVERNOR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|INTERNAL_TESTING |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|IO_AUDIT_MUTEX |在同步處理追蹤事件緩衝區時發生。| 
|IO_COMPLETION |在等候 I/O 作業完成時發生。 這種等候類型通常代表非資料頁面 I/O。 資料頁面 i/o 完成等候會顯示為 PAGEIOLATCH\_\* 等待。| 
|IO_QUEUE_LIMIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|IO_RETRY |當讀取或寫入磁碟等 I/O 作業由於資源不足而失敗，然後重試時發生。| 
|IOAFF_RANGE_QUEUE |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|KSOURCE_WAKEUP |供服務控制工作在等候來自服務控制管理員的要求時使用。 等候時間長是正常情況，並不表示發生任何問題。| 
|KTM_ENLISTMENT |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|KTM_RECOVERY_MANAGER |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|KTM_RECOVERY_RESOLUTION |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|LATCH_DT |在等候 DT (終結) 閂鎖時發生。 其中不包括緩衝區閂鎖或交易標示閂鎖。 \* 等候的閂鎖\_清單可在 sys.databases 中取得。 dm_os_latch_stats。 請注意，sys.dm_os_latch_stats 會將 LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX 和 LATCH_DT 等候分組在一起。| 
|LATCH_EX |在等候 EX (獨佔) 閂鎖時發生。 其中不包括緩衝區閂鎖或交易標示閂鎖。 \* 等候的閂鎖\_清單可在 sys.databases 中取得。 dm_os_latch_stats。 請注意，sys.dm_os_latch_stats 會將 LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX 和 LATCH_DT 等候分組在一起。| 
|LATCH_KP |在等候 KP (保留) 閂鎖時發生。 其中不包括緩衝區閂鎖或交易標示閂鎖。 \* 等候的閂鎖\_清單可在 sys.databases 中取得。 dm_os_latch_stats。 請注意，sys.dm_os_latch_stats 會將 LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX 和 LATCH_DT 等候分組在一起。| 
|LATCH_NL |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|LATCH_SH |在等候 SH (共用) 閂鎖時發生。 其中不包括緩衝區閂鎖或交易標示閂鎖。 \* 等候的閂鎖\_清單可在 sys.databases 中取得。 dm_os_latch_stats。 請注意，sys.dm_os_latch_stats 會將 LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX 和 LATCH_DT 等候分組在一起。| 
|LATCH_UP |在等候 UP (更新) 閂鎖時發生。 其中不包括緩衝區閂鎖或交易標示閂鎖。 \* 等候的閂鎖\_清單可在 sys.databases 中取得。 dm_os_latch_stats。 請注意，sys.dm_os_latch_stats 會將 LATCH_NL、LATCH_SH、LATCH_UP、LATCH_EX 和 LATCH_DT 等候分組在一起。| 
|LAZYWRITER_SLEEP |當延遲寫入器工作暫止時發生。 這是等候中的背景工作所花的時間。 如果您要尋找使用者拋錨點，就不要考慮這個狀態。| 
|LCK_M_BU |當工作在等候取得大量更新 (BU) 鎖定時發生。| 
|LCK_M_BU_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的大量更新 (BU) 鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_BU_LOW_PRIORITY |當工作在等候取得低優先順序的大量更新 (BU) 鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_IS |當工作在等候取得意圖共用 (IS) 鎖定時發生。| 
|LCK_M_IS_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的意圖共用 (IS) 鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_IS_LOW_PRIORITY |當工作在等候取得低優先順序的意圖共用 (IS) 鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_IU |當工作在等候取得意圖更新 (IU) 鎖定時發生。| 
|LCK_M_IU_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的意圖更新 (IU) 鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_IU_LOW_PRIORITY |當工作在等候取得低優先順序的意圖更新 (IU) 鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_IX |當工作在等候取得意圖獨佔 (IX) 鎖定時發生。| 
|LCK_M_IX_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的意圖獨佔 (IX) 鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_IX_LOW_PRIORITY |當工作在等候取得低優先順序的意圖獨佔 (IX) 鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RIn_NL |當工作在等候取得目前索引鍵值的 NULL 鎖定，以及目前索引鍵和前一個索引鍵之間的插入範圍鎖定時發生。 索引鍵的 NULL 鎖定是一個立即釋放鎖定。| 
|LCK_M_RIn_NL_ABORT_BLOCKERS |當工作在等候取得目前索引鍵值的具有中止封鎖器的 NULL 鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的插入範圍鎖定時發生。 索引鍵的 NULL 鎖定是一個立即釋放鎖定。 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RIn_NL_LOW_PRIORITY |當工作在等候取得目前索引鍵值的低優先順序的 NULL 鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的插入範圍鎖定時發生。 索引鍵的 NULL 鎖定是一個立即釋放鎖定。 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RIn_S |當工作在等候取得目前索引鍵值的共用鎖定，以及目前索引鍵和前一個索引鍵之間的插入範圍鎖定時發生。| 
|LCK_M_RIn_S_ABORT_BLOCKERS |當工作在等候取得目前索引鍵值的具有中止封鎖器的共用鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的插入範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RIn_S_LOW_PRIORITY |當工作在等候取得目前索引鍵值的低優先順序的共用鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的插入範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RIn_U |工作在等候取得目前索引鍵值的更新鎖定，以及目前索引鍵和前一個索引鍵之間的插入範圍鎖定。| 
|LCK_M_RIn_U_ABORT_BLOCKERS |工作在等候取得目前索引鍵值的具有中止封鎖器的更新鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的插入範圍鎖定 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RIn_U_LOW_PRIORITY |工作在等候取得目前索引鍵值的低優先順序的更新鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的插入範圍鎖定 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RIn_X |當工作在等候取得目前索引鍵值的獨佔鎖定，以及目前索引鍵和前一個索引鍵之間的插入範圍鎖定時發生。| 
|LCK_M_RIn_X_ABORT_BLOCKERS |當工作在等候取得目前索引鍵值的具有中止封鎖器的獨佔鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的插入範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RIn_X_LOW_PRIORITY |當工作在等候取得目前索引鍵值的低優先順序的獨佔鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的插入範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RS_S |當工作在等候取得目前索引鍵值的共用鎖定，以及目前索引鍵和前一個索引鍵之間的共用範圍鎖定時發生。| 
|LCK_M_RS_S_ABORT_BLOCKERS |當工作在等候取得目前索引鍵值的具有中止封鎖器的共用鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的共用範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RS_S_LOW_PRIORITY |當工作在等候取得目前索引鍵值的低優先順序的共用鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的共用範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RS_U |當工作在等候取得目前索引鍵值的更新鎖定，以及目前索引鍵和前一個索引鍵之間的更新範圍鎖定時發生。| 
|LCK_M_RS_U_ABORT_BLOCKERS |當工作在等候取得目前索引鍵值的具有中止封鎖器的更新鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的更新範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RS_U_LOW_PRIORITY |當工作在等候取得目前索引鍵值的低優先順序的更新鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的更新範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RX_S |當工作在等候取得目前索引鍵值的共用鎖定，以及目前索引鍵和前一個索引鍵之間的獨佔範圍鎖定時發生。| 
|LCK_M_RX_S_ABORT_BLOCKERS |當工作在等候取得目前索引鍵值的具有中止封鎖器的共用鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的獨佔範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RX_S_LOW_PRIORITY |當工作在等候取得目前索引鍵值的低優先順序的共用鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的獨佔範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RX_U |當工作在等候取得目前索引鍵值的更新鎖定，以及目前索引鍵和前一個索引鍵之間的獨佔範圍鎖定時發生。| 
|LCK_M_RX_U_ABORT_BLOCKERS |當工作在等候取得目前索引鍵值的具有中止封鎖器的更新鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的獨佔範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RX_U_LOW_PRIORITY |當工作在等候取得目前索引鍵值的低優先順序的更新鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的獨佔範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RX_X |當工作在等候取得目前索引鍵值的獨佔鎖定，以及目前索引鍵和前一個索引鍵之間的獨佔範圍鎖定時發生。| 
|LCK_M_RX_X_ABORT_BLOCKERS |當工作在等候取得目前索引鍵值的具有中止封鎖器的獨佔鎖定，以及目前索引鍵和前一個索引鍵之間具有中止封鎖器的獨佔範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_RX_X_LOW_PRIORITY |當工作在等候取得目前索引鍵值的低優先順序的獨佔鎖定，以及目前索引鍵和前一個索引鍵之間低優先順序的獨佔範圍鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_S |當工作在等候取得共用鎖定時發生。| 
|LCK_M_S_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的共用鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_S_LOW_PRIORITY |當工作在等候取得低優先順序的共用鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_SCH_M |當工作在等候取得結構描述修改鎖定時發生。| 
|LCK_M_SCH_M_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的結構描述修改鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_SCH_M_LOW_PRIORITY |當工作在等候取得低優先順序的結構描述修改鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_SCH_S |當工作在等候取得結構描述共用鎖定時發生。| 
|LCK_M_SCH_S_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的結構描述共用鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_SCH_S_LOW_PRIORITY |當工作在等候取得低優先順序的結構描述共用鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_SIU |當工作在等候取得共用意圖更新鎖定時發生。| 
|LCK_M_SIU_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的共用意圖更新鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_SIU_LOW_PRIORITY |當工作在等候取得低優先順序的共用意圖更新鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_SIX |當工作在等候取得共用意圖獨佔鎖定時發生。| 
|LCK_M_SIX_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的共用意圖獨佔鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_SIX_LOW_PRIORITY |當工作在等候取得低優先順序的共用意圖獨佔鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_U |當工作在等候取得更新鎖定時發生。| 
|LCK_M_U_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的更新鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_U_LOW_PRIORITY |當工作在等候取得低優先順序的更新鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_UIX |當工作在等候取得更新意圖獨佔鎖定時發生。| 
|LCK_M_UIX_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的更新意圖獨佔鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_UIX_LOW_PRIORITY |當工作在等候取得低優先順序的更新意圖獨佔鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_X |當工作在等候取得獨佔鎖定時發生。| 
|LCK_M_X_ABORT_BLOCKERS |當工作在等候取得具有中止封鎖器的獨佔鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LCK_M_X_LOW_PRIORITY |當工作在等候取得低優先順序的獨佔鎖定時發生 （與 ALTER TABLE 和 ALTER INDEX 的低優先順序等候選項有關）。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|LOG_POOL_SCAN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|LOG_RATE_GOVERNOR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|LOGBUFFER |當工作在等候記錄緩衝區的空間來儲存記錄時發生。 如果這個值一直居高不下，可能表示記錄裝置趕不上伺服器產生的記錄量。| 
|LOGCAPTURE_LOGPOOLTRUNCPOINT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|LOGGENERATION |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|LOGMGR |當工作在關閉資料庫時，於關閉記錄之前等候任何未完成的記錄 I/O 完成時發生。| 
|LOGMGR_FLUSH |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|LOGMGR_PMM_LOG |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|LOGMGR_QUEUE |在記錄寫入器工作等候工作要求時發生。| 
|LOGMGR_RESERVE_APPEND |當工作在等候記錄截斷清出記錄空間，讓工作寫入新記錄時發生。 請考慮增加受影響之資料庫的記錄檔案大小，以縮短這個等候時間。| 
|LOGPOOL_CACHESIZE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|LOGPOOL_CONSUMER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|LOGPOOL_CONSUMERSET |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|LOGPOOL_FREEPOOLS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|LOGPOOL_MGRSET |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|LOGPOOL_REPLACEMENTSET |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|LOGPOOLREFCOUNTEDOBJECT_REFDONE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|LOWFAIL_MEMMGR_QUEUE |在等候記憶體變成可供使用的狀態時發生。| 
|MD_AGENT_YIELD |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|MD_LAZYCACHE_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|MEMORY_ALLOCATION_EXT |從內部 SQL Server 記憶體集區或作業系統配置記憶體時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|MEMORY_GRANT_UPDATE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|METADATA_LAZYCACHE_RWLOCK |僅供內部使用。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|MIGRATIONBUFFER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|MISCELLANEOUS |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|MISCELLANEOUS |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|MSQL_DQ |在工作等候分散式查詢作業完成時發生。 這種等候類型可用來偵測潛在的 Multiple Active Result Set (MARS) 應用程式死結。 等候會隨著分散式查詢呼叫的完成而結束。| 
|MSQL_XACT_MGR_MUTEX |當工作在等候取得工作階段交易管理員的擁有權，以執行工作階段層級交易作業時發生。| 
|MSQL_XACT_MUTEX |在同步處理交易使用量時發生。 要求必須先取得 Mutex，才能使用交易。| 
|MSQL_XP |當工作在等候擴充預存程序結束時發生。 SQL Server 使用此等候狀態來偵測潛在的 MARS 應用程式鎖死。 這個等候會隨著擴充預存程序呼叫的結束而停止。| 
|MSSEARCH |在使用全文檢索搜尋呼叫時發生。 這個等候會隨著全文檢索作業的完成而結束。 這並不表示發生競爭情況，而是指出全文檢索作業的持續時間。| 
|NET_WAITFOR_PACKET |當連接在網路讀取期間等候網路封包時發生。| 
|NETWORKSXMLMGRLOAD |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|NODE_CACHE_MUTEX |僅供內部使用。| 
|OLEDB |當 SQL Server 呼叫 SQL Server Native Client OLE DB 提供者時發生。 這個等候類型不用於同步處理， 而會指出呼叫 OLE DB 提供者的持續時間。| 
|ONDEMAND_TASK_QUEUE |在背景工作等候高優先權的系統工作要求時發生。 如果等候時間很長，表示沒有高優先權的要求需要處理，而且應該不會造成任何問題。| 
|PAGEIOLATCH_DT |當工作在位於 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是終結模式。 如果等候時間很長，表示磁碟子系統有問題。| 
|PAGEIOLATCH_EX |當工作在位於 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是獨佔模式。 如果等候時間很長，表示磁碟子系統有問題。| 
|PAGEIOLATCH_KP |當工作在位於 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是保留模式。 如果等候時間很長，表示磁碟子系統有問題。| 
|PAGEIOLATCH_NL |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|PAGEIOLATCH_SH |當工作在位於 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是共用模式。 如果等候時間很長，表示磁碟子系統有問題。| 
|PAGEIOLATCH_UP |當工作在位於 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是更新模式。 如果等候時間很長，表示磁碟子系統有問題。| 
|PAGELATCH_DT |當工作不是在 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是終結模式。| 
|PAGELATCH_EX |當工作不是在 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是獨佔模式。| 
|PAGELATCH_KP |當工作不是在 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是保留模式。| 
|PAGELATCH_NL |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|PAGELATCH_SH |當工作不是在 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是共用模式。| 
|PAGELATCH_UP |當工作不是在 I/O 要求中的緩衝區閂鎖待命時發生。 閂鎖要求是更新模式。| 
|PARALLEL_BACKUP_QUEUE |在序列化 RESTORE HEADERONLY、RESTORE FILELISTONLY 或 RESTORE LABELONLY 所產生的輸出時發生。| 
|PARALLEL_REDO_DRAIN_WORKER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PARALLEL_REDO_FLOW_CONTROL |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PARALLEL_REDO_LOG_CACHE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PARALLEL_REDO_TRAN_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PARALLEL_REDO_TRAN_TURN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PARALLEL_REDO_WORKER_SYNC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PARALLEL_REDO_WORKER_WAIT_WORK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PERFORMANCE_COUNTERS_RWLOCK |僅供內部使用。| 
|PHYSICAL_SEEDING_DMV |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|POOL_LOG_RATE_GOVERNOR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PREEMPTIVE_ABR |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|PREEMPTIVE_AUDIT_ACCESS_EVENTLOG |在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 作業系統 (SQLOS) 排程器切換到先佔式模式，以便將稽核事件寫入 Windows 事件記錄檔時發生。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|PREEMPTIVE_AUDIT_ACCESS_SECLOG |當 SQLOS 排程器切換到先佔式模式，以便將稽核事件寫入 Windows 安全性記錄檔時發生。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|PREEMPTIVE_CLOSEBACKUPMEDIA |當 SQLOS 排程器切換到先佔式模式，以便關閉備份媒體時發生。| 
|PREEMPTIVE_CLOSEBACKUPTAPE |當 SQLOS 排程器切換到先佔式模式，以便關閉磁帶備份裝置時發生。| 
|PREEMPTIVE_CLOSEBACKUPVDIDEVICE |當 SQLOS 排程器切換到先佔式模式，以便關閉虛擬備份裝置時發生。| 
|PREEMPTIVE_CLUSAPI_CLUSTERRESOURCECONTROL |當 SQLOS 排程器切換到先佔式模式，以便執行 Windows 容錯移轉叢集作業時發生。| 
|PREEMPTIVE_COM_COCREATEINSTANCE |當 SQLOS 排程器切換到先佔式模式，以便建立 COM 物件時發生。| 
|PREEMPTIVE_COM_COGETCLASSOBJECT |僅供內部使用。| 
|PREEMPTIVE_COM_CREATEACCESSOR |僅供內部使用。| 
|PREEMPTIVE_COM_DELETEROWS |僅供內部使用。| 
|PREEMPTIVE_COM_GETCOMMANDTEXT |僅供內部使用。| 
|PREEMPTIVE_COM_GETDATA |僅供內部使用。| 
|PREEMPTIVE_COM_GETNEXTROWS |僅供內部使用。| 
|PREEMPTIVE_COM_GETRESULT |僅供內部使用。| 
|PREEMPTIVE_COM_GETROWSBYBOOKMARK |僅供內部使用。| 
|PREEMPTIVE_COM_LBFLUSH |僅供內部使用。| 
|PREEMPTIVE_COM_LBLOCKREGION |僅供內部使用。| 
|PREEMPTIVE_COM_LBREADAT |僅供內部使用。| 
|PREEMPTIVE_COM_LBSETSIZE |僅供內部使用。| 
|PREEMPTIVE_COM_LBSTAT |僅供內部使用。| 
|PREEMPTIVE_COM_LBUNLOCKREGION |僅供內部使用。| 
|PREEMPTIVE_COM_LBWRITEAT |僅供內部使用。| 
|PREEMPTIVE_COM_QUERYINTERFACE |僅供內部使用。| 
|PREEMPTIVE_COM_RELEASE |僅供內部使用。| 
|PREEMPTIVE_COM_RELEASEACCESSOR |僅供內部使用。| 
|PREEMPTIVE_COM_RELEASEROWS |僅供內部使用。| 
|PREEMPTIVE_COM_RELEASESESSION |僅供內部使用。| 
|PREEMPTIVE_COM_RESTARTPOSITION |僅供內部使用。| 
|PREEMPTIVE_COM_SEQSTRMREAD |僅供內部使用。| 
|PREEMPTIVE_COM_SEQSTRMREADANDWRITE |僅供內部使用。| 
|PREEMPTIVE_COM_SETDATAFAILURE |僅供內部使用。| 
|PREEMPTIVE_COM_SETPARAMETERINFO |僅供內部使用。| 
|PREEMPTIVE_COM_SETPARAMETERPROPERTIES |僅供內部使用。| 
|PREEMPTIVE_COM_STRMLOCKREGION |僅供內部使用。| 
|PREEMPTIVE_COM_STRMSEEKANDREAD |僅供內部使用。| 
|PREEMPTIVE_COM_STRMSEEKANDWRITE |僅供內部使用。| 
|PREEMPTIVE_COM_STRMSETSIZE |僅供內部使用。| 
|PREEMPTIVE_COM_STRMSTAT |僅供內部使用。| 
|PREEMPTIVE_COM_STRMUNLOCKREGION |僅供內部使用。| 
|PREEMPTIVE_CONSOLEWRITE |僅供內部使用。| 
|PREEMPTIVE_CREATEPARAM |僅供內部使用。| 
|PREEMPTIVE_DEBUG |僅供內部使用。| 
|PREEMPTIVE_DFSADDLINK |僅供內部使用。| 
|PREEMPTIVE_DFSLINKEXISTCHECK |僅供內部使用。| 
|PREEMPTIVE_DFSLINKHEALTHCHECK |僅供內部使用。| 
|PREEMPTIVE_DFSREMOVELINK |僅供內部使用。| 
|PREEMPTIVE_DFSREMOVEROOT |僅供內部使用。| 
|PREEMPTIVE_DFSROOTFOLDERCHECK |僅供內部使用。| 
|PREEMPTIVE_DFSROOTINIT |僅供內部使用。| 
|PREEMPTIVE_DFSROOTSHARECHECK |僅供內部使用。| 
|PREEMPTIVE_DTC_ABORT |僅供內部使用。| 
|PREEMPTIVE_DTC_ABORTREQUESTDONE |僅供內部使用。| 
|PREEMPTIVE_DTC_BEGINTRANSACTION |僅供內部使用。| 
|PREEMPTIVE_DTC_COMMITREQUESTDONE |僅供內部使用。| 
|PREEMPTIVE_DTC_ENLIST |僅供內部使用。| 
|PREEMPTIVE_DTC_PREPAREREQUESTDONE |僅供內部使用。| 
|PREEMPTIVE_FILESIZEGET |僅供內部使用。| 
|PREEMPTIVE_FSAOLEDB_ABORTTRANSACTION |僅供內部使用。| 
|PREEMPTIVE_FSAOLEDB_COMMITTRANSACTION |僅供內部使用。| 
|PREEMPTIVE_FSAOLEDB_STARTTRANSACTION |僅供內部使用。| 
|PREEMPTIVE_FSRECOVER_UNCONDITIONALUNDO |僅供內部使用。| 
|PREEMPTIVE_GETRMINFO |僅供內部使用。| 
|PREEMPTIVE_HADR_LEASE_MECHANISM |Microsoft 支援服務診斷的 Always On 可用性群組租用管理員排程。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PREEMPTIVE_HTTP_EVENT_WAIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PREEMPTIVE_HTTP_REQUEST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PREEMPTIVE_LOCKMONITOR |僅供內部使用。| 
|PREEMPTIVE_MSS_RELEASE |僅供內部使用。| 
|PREEMPTIVE_ODBCOPS |僅供內部使用。| 
|PREEMPTIVE_OLE_UNINIT |僅供內部使用。| 
|PREEMPTIVE_OLEDB_ABORTORCOMMITTRAN |僅供內部使用。| 
|PREEMPTIVE_OLEDB_ABORTTRAN |僅供內部使用。| 
|PREEMPTIVE_OLEDB_GETDATASOURCE |僅供內部使用。| 
|PREEMPTIVE_OLEDB_GETLITERALINFO |僅供內部使用。| 
|PREEMPTIVE_OLEDB_GETPROPERTIES |僅供內部使用。| 
|PREEMPTIVE_OLEDB_GETPROPERTYINFO |僅供內部使用。| 
|PREEMPTIVE_OLEDB_GETSCHEMALOCK |僅供內部使用。| 
|PREEMPTIVE_OLEDB_JOINTRANSACTION |僅供內部使用。| 
|PREEMPTIVE_OLEDB_RELEASE |僅供內部使用。| 
|PREEMPTIVE_OLEDB_SETPROPERTIES |僅供內部使用。| 
|PREEMPTIVE_OLEDBOPS |僅供內部使用。| 
|PREEMPTIVE_OS_ACCEPTSECURITYCONTEXT |僅供內部使用。| 
|PREEMPTIVE_OS_ACQUIRECREDENTIALSHANDLE |僅供內部使用。| 
|PREEMPTIVE_OS_AUTHENTICATIONOPS |僅供內部使用。| 
|PREEMPTIVE_OS_AUTHORIZATIONOPS |僅供內部使用。| 
|PREEMPTIVE_OS_AUTHZGETINFORMATIONFROMCONTEXT |僅供內部使用。| 
|PREEMPTIVE_OS_AUTHZINITIALIZECONTEXTFROMSID |僅供內部使用。| 
|PREEMPTIVE_OS_AUTHZINITIALIZERESOURCEMANAGER |僅供內部使用。| 
|PREEMPTIVE_OS_BACKUPREAD |僅供內部使用。| 
|PREEMPTIVE_OS_CLOSEHANDLE |僅供內部使用。| 
|PREEMPTIVE_OS_CLUSTEROPS |僅供內部使用。| 
|PREEMPTIVE_OS_COMOPS |僅供內部使用。| 
|PREEMPTIVE_OS_COMPLETEAUTHTOKEN |僅供內部使用。| 
|PREEMPTIVE_OS_COPYFILE |僅供內部使用。| 
|PREEMPTIVE_OS_CREATEDIRECTORY |僅供內部使用。| 
|PREEMPTIVE_OS_CREATEFILE |僅供內部使用。| 
|PREEMPTIVE_OS_CRYPTACQUIRECONTEXT |僅供內部使用。| 
|PREEMPTIVE_OS_CRYPTIMPORTKEY |僅供內部使用。| 
|PREEMPTIVE_OS_CRYPTOPS |僅供內部使用。| 
|PREEMPTIVE_OS_DECRYPTMESSAGE |僅供內部使用。| 
|PREEMPTIVE_OS_DELETEFILE |僅供內部使用。| 
|PREEMPTIVE_OS_DELETESECURITYCONTEXT |僅供內部使用。| 
|PREEMPTIVE_OS_DEVICEIOCONTROL |僅供內部使用。| 
|PREEMPTIVE_OS_DEVICEOPS |僅供內部使用。| 
|PREEMPTIVE_OS_DIRSVC_NETWORKOPS |僅供內部使用。| 
|PREEMPTIVE_OS_DISCONNECTNAMEDPIPE |僅供內部使用。| 
|PREEMPTIVE_OS_DOMAINSERVICESOPS |僅供內部使用。| 
|PREEMPTIVE_OS_DSGETDCNAME |僅供內部使用。| 
|PREEMPTIVE_OS_DTCOPS |僅供內部使用。| 
|PREEMPTIVE_OS_ENCRYPTMESSAGE |僅供內部使用。| 
|PREEMPTIVE_OS_FILEOPS |僅供內部使用。| 
|PREEMPTIVE_OS_FINDFILE |僅供內部使用。| 
|PREEMPTIVE_OS_FLUSHFILEBUFFERS |僅供內部使用。| 
|PREEMPTIVE_OS_FORMATMESSAGE |僅供內部使用。| 
|PREEMPTIVE_OS_FREECREDENTIALSHANDLE |僅供內部使用。| 
|PREEMPTIVE_OS_FREELIBRARY |僅供內部使用。| 
|PREEMPTIVE_OS_GENERICOPS |僅供內部使用。| 
|PREEMPTIVE_OS_GETADDRINFO |僅供內部使用。| 
|PREEMPTIVE_OS_GETCOMPRESSEDFILESIZE |僅供內部使用。| 
|PREEMPTIVE_OS_GETDISKFREESPACE |僅供內部使用。| 
|PREEMPTIVE_OS_GETFILEATTRIBUTES |僅供內部使用。| 
|PREEMPTIVE_OS_GETFILESIZE |僅供內部使用。| 
|PREEMPTIVE_OS_GETFINALFILEPATHBYHANDLE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PREEMPTIVE_OS_GETLONGPATHNAME |僅供內部使用。| 
|PREEMPTIVE_OS_GETPROCADDRESS |僅供內部使用。| 
|PREEMPTIVE_OS_GETVOLUMENAMEFORVOLUMEMOUNTPOINT |僅供內部使用。| 
|PREEMPTIVE_OS_GETVOLUMEPATHNAME |僅供內部使用。| 
|PREEMPTIVE_OS_INITIALIZESECURITYCONTEXT |僅供內部使用。| 
|PREEMPTIVE_OS_LIBRARYOPS |僅供內部使用。| 
|PREEMPTIVE_OS_LOADLIBRARY |僅供內部使用。| 
|PREEMPTIVE_OS_LOGONUSER |僅供內部使用。| 
|PREEMPTIVE_OS_LOOKUPACCOUNTSID |僅供內部使用。| 
|PREEMPTIVE_OS_MESSAGEQUEUEOPS |僅供內部使用。| 
|PREEMPTIVE_OS_MOVEFILE |僅供內部使用。| 
|PREEMPTIVE_OS_NETGROUPGETUSERS |僅供內部使用。| 
|PREEMPTIVE_OS_NETLOCALGROUPGETMEMBERS |僅供內部使用。| 
|PREEMPTIVE_OS_NETUSERGETGROUPS |僅供內部使用。| 
|PREEMPTIVE_OS_NETUSERGETLOCALGROUPS |僅供內部使用。| 
|PREEMPTIVE_OS_NETUSERMODALSGET |僅供內部使用。| 
|PREEMPTIVE_OS_NETVALIDATEPASSWORDPOLICY |僅供內部使用。| 
|PREEMPTIVE_OS_NETVALIDATEPASSWORDPOLICYFREE |僅供內部使用。| 
|PREEMPTIVE_OS_OPENDIRECTORY |僅供內部使用。| 
|PREEMPTIVE_OS_PDH_WMI_INIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PREEMPTIVE_OS_PIPEOPS |僅供內部使用。| 
|PREEMPTIVE_OS_PROCESSOPS |僅供內部使用。| 
|PREEMPTIVE_OS_QUERYCONTEXTATTRIBUTES |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PREEMPTIVE_OS_QUERYREGISTRY |僅供內部使用。| 
|PREEMPTIVE_OS_QUERYSECURITYCONTEXTTOKEN |僅供內部使用。| 
|PREEMPTIVE_OS_REMOVEDIRECTORY |僅供內部使用。| 
|PREEMPTIVE_OS_REPORTEVENT |僅供內部使用。| 
|PREEMPTIVE_OS_REVERTTOSELF |僅供內部使用。| 
|PREEMPTIVE_OS_RSFXDEVICEOPS |僅供內部使用。| 
|PREEMPTIVE_OS_SECURITYOPS |僅供內部使用。| 
|PREEMPTIVE_OS_SERVICEOPS |僅供內部使用。| 
|PREEMPTIVE_OS_SETENDOFFILE |僅供內部使用。| 
|PREEMPTIVE_OS_SETFILEPOINTER |僅供內部使用。| 
|PREEMPTIVE_OS_SETFILEVALIDDATA |僅供內部使用。| 
|PREEMPTIVE_OS_SETNAMEDSECURITYINFO |僅供內部使用。| 
|PREEMPTIVE_OS_SQLCLROPS |僅供內部使用。| 
|PREEMPTIVE_OS_SQMLAUNCH |僅供內部使用。 <br /> **適用於**： [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)] 至 [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]。 |  
|PREEMPTIVE_OS_VERIFYSIGNATURE |僅供內部使用。| 
|PREEMPTIVE_OS_VERIFYTRUST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PREEMPTIVE_OS_VSSOPS |僅供內部使用。| 
|PREEMPTIVE_OS_WAITFORSINGLEOBJECT |僅供內部使用。| 
|PREEMPTIVE_OS_WINSOCKOPS |僅供內部使用。| 
|PREEMPTIVE_OS_WRITEFILE |僅供內部使用。| 
|PREEMPTIVE_OS_WRITEFILEGATHER |僅供內部使用。| 
|PREEMPTIVE_OS_WSASETLASTERROR |僅供內部使用。| 
|PREEMPTIVE_REENLIST |僅供內部使用。| 
|PREEMPTIVE_RESIZELOG |僅供內部使用。| 
|PREEMPTIVE_ROLLFORWARDREDO |僅供內部使用。| 
|PREEMPTIVE_ROLLFORWARDUNDO |僅供內部使用。| 
|PREEMPTIVE_SB_STOPENDPOINT |僅供內部使用。| 
|PREEMPTIVE_SERVER_STARTUP |僅供內部使用。| 
|PREEMPTIVE_SETRMINFO |僅供內部使用。| 
|PREEMPTIVE_SHAREDMEM_GETDATA |僅供內部使用。| 
|PREEMPTIVE_SNIOPEN |僅供內部使用。| 
|PREEMPTIVE_SOSHOST |僅供內部使用。| 
|PREEMPTIVE_SOSTESTING |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|PREEMPTIVE_SP_SERVER_DIAGNOSTICS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PREEMPTIVE_STARTRM |僅供內部使用。| 
|PREEMPTIVE_STREAMFCB_CHECKPOINT |僅供內部使用。| 
|PREEMPTIVE_STREAMFCB_RECOVER |僅供內部使用。| 
|PREEMPTIVE_STRESSDRIVER |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|PREEMPTIVE_TESTING |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|PREEMPTIVE_TRANSIMPORT |僅供內部使用。| 
|PREEMPTIVE_UNMARSHALPROPAGATIONTOKEN |僅供內部使用。| 
|PREEMPTIVE_VSS_CREATESNAPSHOT |僅供內部使用。| 
|PREEMPTIVE_VSS_CREATEVOLUMESNAPSHOT |僅供內部使用。| 
|PREEMPTIVE_XE_CALLBACKEXECUTE |僅供內部使用。| 
|PREEMPTIVE_XE_CX_FILE_OPEN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|PREEMPTIVE_XE_CX_HTTP_CALL |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|PREEMPTIVE_XE_DISPATCHER |僅供內部使用。| 
|PREEMPTIVE_XE_ENGINEINIT |僅供內部使用。| 
|PREEMPTIVE_XE_GETTARGETSTATE |僅供內部使用。| 
|PREEMPTIVE_XE_SESSIONCOMMIT |僅供內部使用。| 
|PREEMPTIVE_XE_TARGETFINALIZE |僅供內部使用。| 
|PREEMPTIVE_XE_TARGETINIT |僅供內部使用。| 
|PREEMPTIVE_XE_TIMERRUN |僅供內部使用。| 
|PREEMPTIVE_XETESTING |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|PRINT_ROLLBACK_PROGRESS |用於使用者處理序在已經使用 ALTER DATABASE 終止子句加以轉換的資料庫中結束時等候。 如需詳細資訊，請參閱 ALTER DATABASE （Transact-sql）。| 
|PRU_ROLLBACK_DEFERRED |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_ALL_COMPONENTS_INITIALIZED |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_COOP_SCAN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_DIRECTLOGCONSUMER_GETNEXT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PWAIT_EVENT_SESSION_INIT_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_FABRIC_REPLICA_CONTROLLER_DATA_LOSS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PWAIT_HADR_ACTION_COMPLETED |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADR_CHANGE_NOTIFIER_TERMINATION_SYNC |當背景工作正在等候接收（經由輪詢） Windows Server 容錯移轉叢集通知的背景工作終止時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADR_CLUSTER_INTEGRATION |[附加]、[取代] 和/或 [移除] 作業正在等候抓取 Always On 內部清單（例如網路、網路位址或可用性群組接聽程式的清單）的寫入鎖定。 僅供內部使用， <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADR_FAILOVER_COMPLETED |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADR_JOIN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|PWAIT_HADR_OFFLINE_COMPLETED |Always On drop 可用性群組作業正在等候目標可用性群組離線，然後再終結 Windows Server 容錯移轉叢集物件。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADR_ONLINE_COMPLETED |Always On 建立或容錯移轉可用性群組作業正在等候目標可用性群組上線。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADR_POST_ONLINE_COMPLETED |Always On drop 可用性群組作業正在等候先前命令中排程的任何背景工作終止。 例如，可能會存在將可用性資料庫轉換成主要角色的背景工作。 DROP AVAILABILITY GROUP DDL 必須等候此背景工作終止，才能避免競爭情形。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADR_SERVER_READY_CONNECTIONS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADR_WORKITEM_COMPLETED |等候非同步工作完成之執行緒的內部等候。 這是預期的等候，而且適用于 CSS。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_HADRSIM |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|PWAIT_LOG_CONSOLIDATION_IO |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|PWAIT_LOG_CONSOLIDATION_POLL |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|PWAIT_MD_LOGIN_STATS |在內部同步處理登入統計資料的中繼資料時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_MD_RELATION_CACHE |在內部同步處理資料表或索引上的中繼資料時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_MD_SERVER_CACHE |在連結伺服器的中繼資料內部同步處理期間發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_MD_UPGRADE_CONFIG |在升級伺服器範圍設定的內部同步處理期間發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_PREEMPTIVE_APP_USAGE_TIMER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|PWAIT_PREEMPTIVE_AUDIT_ACCESS_WINDOWSLOG |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_QRY_BPMEMORY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_REPLICA_ONLINE_INIT_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_RESOURCE_SEMAPHORE_FT_PARALLEL_QUERY_SYNC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|PWAIT_SBS_FILE_OPERATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|PWAIT_XTP_FSSTORAGE_MAINTENANCE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|PWAIT_XTP_HOST_STORAGE_WAIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_ASYNC_CHECK_CONSISTENCY_TASK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_ASYNC_PERSIST_TASK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_ASYNC_PERSIST_TASK_START |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_ASYNC_QUEUE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|QDS_BCKG_TASK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_BLOOM_FILTER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|QDS_CLEANUP_STALE_QUERIES_TASK_MAIN_LOOP_SLEEP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_CTXS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_DB_DISK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_DYN_VECTOR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_EXCLUSIVE_ACCESS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|QDS_HOST_INIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|QDS_LOADDB |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_PERSIST_TASK_MAIN_LOOP_SLEEP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_QDS_CAPTURE_INIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|QDS_SHUTDOWN_QUEUE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_STMT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_STMT_DISK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_TASK_SHUTDOWN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QDS_TASK_START |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QE_WARN_LIST_SYNC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|QPJOB_KILL |指出非同步自動統計資料更新開始執行時，已被 KILL 的呼叫所取消。 終止執行緒已經暫停，正在等候它開始接聽 KILL 命令。 其值最好少於一秒。| 
|QPJOB_WAITFOR_ABORT |指出非同步自動統計資料更新在執行時，已被 KILL 的呼叫所取消。 雖然這項更新已經完成了，但卻被暫停到終止執行緒訊息協調完成為止。 這種狀態雖然很平常，卻很少見，而且為時甚短。 其值最好少於一秒。| 
|QRY_MEM_GRANT_INFO_MUTEX |當查詢執行記憶體管理試圖控制靜態授與資訊清單的存取時發生。 這個狀態會列出目前已授與和等候中之記憶體要求的相關資訊。 這個狀態是一種簡單的存取控制狀態。 這個狀態應該不會有長時間的等候。 如果沒有釋出這個 Mutex，所有新的記憶體使用查詢都會停止回應。| 
|QRY_PARALLEL_THREAD_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|QRY_PROFILE_LIST_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|QUERY_ERRHDL_SERVICE_DONE |僅供參考之用。 不支援。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|QUERY_WAIT_ERRHDL_SERVICE |僅供參考之用。  不支援。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。  |  
|QUERY_EXECUTION_INDEX_SORT_EVENT_OPEN |在離線建立索引建置平行執行時，以及排序中的不同工作者執行緒同步處理排序檔存取作業時的某些情況中發生。| 
|QUERY_NOTIFICATION_MGR_MUTEX |在同步處理查詢通知管理員中的記憶體回收佇列時發生。| 
|QUERY_NOTIFICATION_SUBSCRIPTION_MUTEX |在同步處理查詢通知中交易的狀態時發生。| 
|QUERY_NOTIFICATION_TABLE_MGR_MUTEX |在查詢通知管理員內執行內部同步處理時發生。| 
|QUERY_NOTIFICATION_UNITTEST_MUTEX |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|QUERY_OPTIMIZER_PRINT_MUTEX |在同步處理查詢最佳化工具診斷輸出生產作業時發生。 只有在 Microsoft 產品支援的方向已啟用診斷設定時，才會發生這種等候類型。| 
|QUERY_TASK_ENQUEUE_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|QUERY_TRACEOUT |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|RBIO_WAIT_VLF |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|RBIO_RG_STORAGE |當超大規模資料庫資料庫計算節點因為頁面伺服器上延遲的記錄耗用量而受到節流時發生。 <br /> **適用**于： Azure SQL Database 超大規模資料庫。|
|RBIO_RG_DESTAGE |當超大規模資料庫資料庫計算節點因為長期記錄儲存體的延遲記錄耗用量而受到節流時發生。 <br /> **適用**于： Azure SQL Database 超大規模資料庫。|
|RBIO_RG_REPLICA |當超大規模資料庫資料庫計算節點因為可讀取的次要複本節點而延遲記錄耗用量而進行節流時發生。 <br /> **適用**于： Azure SQL Database 超大規模資料庫。|
|RBIO_RG_LOCALDESTAGE |當超大規模資料庫資料庫計算節點因為記錄服務而延遲記錄耗用量而進行節流時發生。 <br /> **適用**于： Azure SQL Database 超大規模資料庫。|
|RECOVER_CHANGEDB |在同步處理暖待命資料庫中的資料庫狀態時發生。| 
|RECOVERY_MGR_LOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|REDO_THREAD_PENDING_WORK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|REDO_THREAD_SYNC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|REMOTE_BLOCK_IO |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|REMOTE_DATA_ARCHIVE_MIGRATION_DMV |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|REMOTE_DATA_ARCHIVE_SCHEMA_DMV |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|REMOTE_DATA_ARCHIVE_SCHEMA_TASK_QUEUE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|REPL_CACHE_ACCESS |在複寫發行項快取上進行同步處理時發生。 在這些等候期間，複寫記錄讀取器將會暫停，而已發行資料表上的資料定義語言 (DDL) 陳述式也會遭到封鎖。| 
|REPL_HISTORYCACHE_ACCESS |僅供內部使用。| 
|REPL_SCHEMA_ACCESS |在同步處理複寫結構描述版本資訊時發生。 在已複寫物件上執行 DDL 陳述式時，以及當記錄讀取器依據 DDL 出現位置來建立或取用版本化結構描述時，都會出現這種狀態。 如果您在具有異動複寫的單一發行者上有許多已發行的資料庫，而且已發行的資料庫非常活躍，則可以在這種等候類型上看到爭用。| 
|REPL_TRANFSINFO_ACCESS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|REPL_TRANHASHTABLE_ACCESS |僅供內部使用。| 
|REPL_TRANTEXTINFO_ACCESS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|REPLICA_WRITES |在工作等候頁面寫入資料庫快照集或 DBCC 複本完成時發生。| 
|REQUEST_DISPENSER_PAUSE |當工作在等候所有未處理 I/O 完成，使其可凍結檔案 I/O 以供快照集備份時發生。| 
|REQUEST_FOR_DEADLOCK_SEARCH |在死結監視器等候開始下個死結搜尋時發生。 這個等候應該在兩次死結偵測之間發生，在此資源上的等候時間如果很長，並不表示發生任何問題。| 
|RESERVED_MEMORY_ALLOCATION_EXT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|RESMGR_THROTTLED |當新的要求送入，然後根據 GROUP_MAX_REQUESTS 設定降低速度。| 
|RESOURCE_GOVERNOR_IDLE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|RESOURCE_QUEUE |在同步處理各種內部資源佇列時發生。| 
|RESOURCE_SEMAPHORE |在其他並行查詢導致查詢記憶體要求無法立即取得授權時發生。 如果等候頻率很高且等候時間很長，可能表示並行查詢數目過多、重複編譯，或是記憶體要求量過大。| 
|RESOURCE_SEMAPHORE_MUTEX |在查詢等候系統滿足其執行緒保留要求時發生。 同步處理查詢編譯與記憶體授權要求時也會發生這種等候類型。| 
|RESOURCE_SEMAPHORE_QUERY_COMPILE |當並行查詢編譯數目達到調整流速上限時發生。 如果等候頻率很高且等候時間很長，可能表示編譯數目過多，或是計畫無法快取。| 
|RESOURCE_SEMAPHORE_SMALL_QUERY |在其他並行查詢導致小型查詢之記憶體要求無法立即取得授權時發生。 等候時間應該不會超過幾秒鐘，因為如果伺服器無法在幾秒鐘內授權使用要求的記憶體，它就會將要求傳送到主要查詢記憶體集區。 如果等候頻率很高，可能表示並行的小型查詢數目過多，而主要記憶體集區則受到等候中的查詢所封鎖。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|RESTORE_FILEHANDLECACHE_ENTRYLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|RESTORE_FILEHANDLECACHE_LOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|RG_RECONFIG |僅供內部使用。| 
|ROWGROUP_OP_STATS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|ROWGROUP_VERSION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|RTDATA_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|SATELLITE_CARGO |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SATELLITE_SERVICE_SETUP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SATELLITE_TASK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SBS_DISPATCH |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|SBS_RECEIVE_TRANSPORT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|SBS_TRANSPORT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|SCAN_CHAR_HASH_ARRAY_INITIALIZATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SEC_DROP_TEMP_KEY |在嘗試卸除暫時安全性金鑰失敗之後，再次重試之前發生。| 
|SECURITY_CNG_PROVIDER_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|SECURITY_CRYPTO_CONTEXT_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SECURITY_DBE_STATE_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SECURITY_KEYRING_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SECURITY_MUTEX |當系統等候控制可延伸金鑰管理 (EKM) 密碼編譯提供者之全域清單和 EKM 工作階段之工作階段範圍清單存取權的 Mutex 時發生。| 
|SECURITY_RULETABLE_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SEMPLAT_DSI_BUILD |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SEQUENCE_GENERATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SEQUENTIAL_GUID |正在取得新的循序 GUID 時發生。| 
|SERVER_IDLE_CHECK |當資源監視器嘗試將 SQL Server 實例宣告為閒置或嘗試喚醒時，在同步處理 SQL Server 實例閒置狀態時發生。| 
|SERVER_RECONFIGURE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SESSION_WAIT_STATS_CHILDREN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SHARED_DELTASTORE_CREATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SHUTDOWN |在關機陳述式等候使用中的連接結束時發生。| 
|SLEEP_BPOOL_FLUSH |在檢查點調整流速發出新 I/O 之流速以避免磁碟子系統爆滿時發生。| 
|SLEEP_BUFFERPOOL_HELPLW |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SLEEP_DBSTARTUP |在啟動資料庫期間等候所有資料庫復原時發生。| 
|SLEEP_DCOMSTARTUP |在等候 DCOM 初始化完成的 SQL Server 實例啟動期間，最多會發生一次。| 
|SLEEP_MASTERDBREADY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SLEEP_MASTERMDREADY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SLEEP_MASTERUPGRADED |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SLEEP_MEMORYPOOL_ALLOCATEPAGES |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SLEEP_MSDBSTARTUP |在 SQL 追蹤等候 msdb 資料庫啟動完成時發生。| 
|SLEEP_RETRY_VIRTUALALLOC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SLEEP_SYSTEMTASK |在啟動背景工作期間等候 tempdb 啟動完成時發生。| 
|SLEEP_TASK |當工作在等候一般事件發生期間進入休眠時發生。| 
|SLEEP_TEMPDBSTARTUP |在工作等候 tempdb 完成啟動時發生。| 
|SLEEP_WORKSPACE_ALLOCATEPAGE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SLO_UPDATE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|SMSYNC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SNI_CONN_DUP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|SNI_CRITICAL_SECTION |在 SQL Server 網路元件內的內部同步處理期間發生。| 
|SNI_HTTP_WAITFOR_0_DISCON |在 SQL Server 關閉期間，等候未處理的 HTTP 連接結束時發生。| 
|SNI_LISTENER_ACCESS |等候非統一記憶體存取 (NUMA) 節點更新狀態變更時發生。 狀態變更的存取權是序列化的。| 
|SNI_TASK_COMPLETION |當系統在 NUMA 節點狀態變更期間等候所有工作完成時發生。| 
|SNI_WRITE_ASYNC |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|SOAP_READ |在等候 HTTP 網路讀取動作完成時發生。| 
|SOAP_WRITE |在等候 HTTP 網路寫入動作完成時發生。| 
|SOCKETDUPLICATEQUEUE_CLEANUP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|SOS_CALLBACK_REMOVAL |在回撥清單上執行同步處理以移除回撥時發生。 在伺服器初始化完成之後，此計數器不應該變更。| 
|SOS_DISPATCHER_MUTEX |在發送器集區的內部同步處理期間發生。 這包括正在調整集區時。| 
|SOS_LOCALALLOCATORLIST |在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 記憶體管理員中執行內部同步處理時發生。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|SOS_MEMORY_TOPLEVELBLOCKALLOCATOR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SOS_MEMORY_USAGE_ADJUSTMENT |調整集區之間的記憶體使用量時發生。| 
|SOS_OBJECT_STORE_DESTROY_MUTEX |在記憶體集區中執行內部同步處理期間從集區終結物件時發生。| 
|SOS_PHYS_PAGE_CACHE |表示執行緒等候取得 Mutex 的時間，執行緒必須取得 Mutex，才能配置實體頁面，或將這些頁面傳回作業系統。 只有當 SQL Server 的實例使用 AWE 記憶體時，才會出現此類型的等候。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SOS_PROCESS_AFFINITY_MUTEX |在同步處理程序相似性設定的存取作業時發生。| 
|SOS_RESERVEDMEMBLOCKLIST |在 SQL Server 記憶體管理員的內部同步處理期間發生。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|SOS_SCHEDULER_YIELD |在工作主動產生排程器以供其他工作執行時發生。 在這段等候期間，該工作將等候系統更新其配量。| 
|SOS_SMALL_PAGE_ALLOC |在配置和釋放某些記憶體物件所管理的記憶體期間發生。| 
|SOS_STACKSTORE_INIT_MUTEX |在同步處理內部存放區初始化時發生。| 
|SOS_SYNC_TASK_ENQUEUE_EVENT |在以同步的方式啟動工作時發生。 SQL Server 中的大部分工作都是以非同步方式啟動，在工作要求放在工作佇列之後，控制項會立即回到起始處。| 
|SOS_VIRTUALMEMORY_LOW |在記憶體配置等候資源管理員釋放虛擬記憶體時發生。| 
|SOSHOST_EVENT |在主控的元件（例如 CLR）等候 SQL Server 事件同步處理物件時發生。| 
|SOSHOST_INTERNAL |在同步處理主控元件 (例如 CLR) 使用的記憶體管理員回撥時發生。| 
|SOSHOST_MUTEX |當主控的元件（例如 CLR）等候 SQL Server 的 mutex 同步處理物件時發生。| 
|SOSHOST_RWLOCK |在主控的元件（例如 CLR）等候 SQL Server 讀取器寫入器同步處理物件時發生。| 
|SOSHOST_SEMAPHORE |當主控的元件（例如 CLR）等候 SQL Server 信號同步處理物件時發生。| 
|SOSHOST_SLEEP |當主控的工作在等候一般事件發生期間進入休眠時發生。 主控的工作是供主控的元件 (例如 CLR) 使用。| 
|SOSHOST_TRACELOCK |在同步處理追蹤資料流的存取作業時發生。| 
|SOSHOST_WAITFORDONE |在主控的元件 (例如 CLR) 等候工作完成時發生。| 
|SP_PREEMPTIVE_SERVER_DIAGNOSTICS_SLEEP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SP_SERVER_DIAGNOSTICS_BUFFER_ACCESS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SP_SERVER_DIAGNOSTICS_INIT_MUTEX |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SP_SERVER_DIAGNOSTICS_SLEEP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SQLCLR_APPDOMAIN |在 CLR 等候應用程式網域完成啟動時發生。| 
|SQLCLR_ASSEMBLY |在等候存取 appdomain 中已載入的組件清單時發生。| 
|SQLCLR_DEADLOCK_DETECTION |在 CLR 等候死結偵測完成時發生。| 
|SQLCLR_QUANTUM_PUNISHMENT |在 CLR 工作由於本身已超過其執行配量而進行調整流速時發生。 執行這項調整流速的目的是為了降低這個大量使用資源的工作對其他工作所造成的影響。| 
|SQLSORT_NORMMUTEX |在內部同步處理期間初始化內部排序結構時發生。| 
|SQLSORT_SORTMUTEX |在內部同步處理期間初始化內部排序結構時發生。| 
|SQLTRACE_BUFFER_FLUSH |當工作在等候背景工作每四秒將追蹤緩衝區排清到磁碟時發生。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|SQLTRACE_FILE_BUFFER |在檔案追蹤期間同步處理追蹤緩衝區時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SQLTRACE_FILE_READ_IO_COMPLETION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SQLTRACE_FILE_WRITE_IO_COMPLETION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SQLTRACE_INCREMENTAL_FLUSH_SLEEP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SQLTRACE_LOCK |僅供內部使用。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|SQLTRACE_PENDING_BUFFER_WRITERS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|SQLTRACE_SHUTDOWN |在追蹤關機等候未處理的追蹤事件完成時發生。| 
|SQLTRACE_WAIT_ENTRIES |在 SQL 追蹤事件佇列等候封包到達佇列時發生。| 
|SRVPROC_SHUTDOWN |在關機處理序等候內部資源釋出以完整關機時發生。| 
|STARTUP_DEPENDENCY_MANAGER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|TDS_BANDWIDTH_STATE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|TDS_INIT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|TDS_PROXY_CONTAINER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|TEMPOBJ |在已同步處理暫存物件卸除時發生。 這種等候很罕見，只有在工作已要求 temp 資料表卸除的獨佔存取權時才會發生。| 
|TEMPORAL_BACKGROUND_PROCEED_CLEANUP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|TERMINATE_LISTENER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|THREADPOOL |當工作在等候工作者以供其執行時發生。 這可能表示工作者設定上限太低，或者批次執行花費的時間超乎尋常地多，因而減少了可以滿足其他批次的可用工作者數目。| 
|TIMEPRIV_TIMEPERIOD |在「擴充事件」計時器的內部同步處理期間發生。| 
|TRACE_EVTNOTIF |僅供內部使用。| 
|TRACEWRITE |在 SQL 追蹤資料列集追蹤提供者等候可用緩衝區或具有待處理事件之緩衝區時發生。| 
|TRAN_MARKLATCH_DT |在交易標示閂鎖上等候終結模式閂鎖時發生。 交易標示閂鎖可用來同步處理認可與已標示交易。| 
|TRAN_MARKLATCH_EX |在已標示交易上等候獨佔模式閂鎖時發生。 交易標示閂鎖可用來同步處理認可與已標示交易。| 
|TRAN_MARKLATCH_KP |在已標示交易上等候保留模式閂鎖時發生。 交易標示閂鎖可用來同步處理認可與已標示交易。| 
|TRAN_MARKLATCH_NL |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|TRAN_MARKLATCH_SH |在已標示交易上等候共用模式閂鎖時發生。 交易標示閂鎖可用來同步處理認可與已標示交易。| 
|TRAN_MARKLATCH_UP |在已標示交易上等候更新模式閂鎖時發生。 交易標示閂鎖可用來同步處理認可與已標示交易。| 
|TRANSACTION_MUTEX |在同步處理多個批次對交易的存取作業時發生。| 
|UCS_ENDPOINT_CHANGE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|UCS_MANAGER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|UCS_MEMORY_NOTIFICATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|UCS_SESSION_REGISTRATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|UCS_TRANSPORT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|UCS_TRANSPORT_STREAM_CHANGE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|UTIL_PAGE_ALLOC |在交易記錄掃描在記憶體壓力下等候記憶體變成可供使用的狀態時發生。| 
|VDI_CLIENT_COMPLETECOMMAND |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|VDI_CLIENT_GETCOMMAND |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|VDI_CLIENT_OPERATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|VDI_CLIENT_OTHER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|VERSIONING_COMMITTING |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|VIA_ACCEPT |當虛擬介面卡 (VIA) 提供者連接在啟動期間完成時發生。| 
|VIEW_DEFINITION_MUTEX |在同步處理快取檢視定義的存取作業時發生。| 
|WAIT_FOR_RESULTS |在等候查詢通知被觸發時發生。| 
|WAIT_ON_SYNC_STATISTICS_REFRESH |在等候同步統計資料更新完成，然後查詢編譯和執行可以繼續時發生。<br /> **適用於**：從 [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] 起|
|WAIT_SCRIPTDEPLOYMENT_REQUEST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_SCRIPTDEPLOYMENT_WORKER |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XLOGREAD_SIGNAL |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|WAIT_XTP_ASYNC_TX_COMPLETION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_CKPT_AGENT_WAKEUP |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_CKPT_CLOSE |在等候檢查點完成時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_CKPT_ENABLED |當檢查點已停用，且正在等候檢查點啟用時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_CKPT_STATE_LOCK |同步檢查檢查點狀態時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_COMPILE_WAIT |僅供內部使用。 <br /> **適用於**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|WAIT_XTP_GUEST |當資料庫記憶體配置器需要停止接收低記憶體通知時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|WAIT_XTP_HOST_WAIT |當資料庫引擎觸發等候並由主機執行時，就會發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_OFFLINE_CKPT_BEFORE_REDO |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_OFFLINE_CKPT_LOG_IO |離線檢查點等候記錄讀取 IO 完成時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_OFFLINE_CKPT_NEW_LOG |當離線檢查點在等候新記錄檔記錄進行掃描時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_PROCEDURE_ENTRY |當 drop 程式正在等候該程式的所有目前執行完成時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_RECOVERY |當資料庫復原在等候記憶體優化物件的復原完成時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAIT_XTP_SERIAL_RECOVERY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|WAIT_XTP_SWITCH_TO_INACTIVE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|WAIT_XTP_TASK_SHUTDOWN |在等候記憶體內部 OLTP 執行緒完成時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|WAIT_XTP_TRAN_DEPENDENCY |在等候交易相依性時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WAITFOR |發生于 WAITFOR Transact-sql 語句的結果。 等候的持續時間由陳述式的參數決定。 這是使用者起始的等候。| 
|WAITFOR_PER_QUEUE |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|WAITFOR_TASKSHUTDOWN |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|WAITSTAT_MUTEX |在同步處理用來擴展 sys.dm_os_wait_stats 之統計資料集合的存取作業時發生。| 
|WCC |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|WINDOW_AGGREGATES_MULTIPASS |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|WINFAB_API_CALL |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WINFAB_REPLICA_BUILD_OPERATION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|WINFAB_REPORT_FAULT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|WORKTBL_DROP |在工作資料表卸除失敗之後，於重試之前暫停時發生。| 
|WRITE_COMPLETION |當寫入作業正在進行時發生。| 
|WRITELOG |在等候記錄排清完成時發生。 造成記錄排清的一般作業包括檢查點和交易認可。| 
|XACT_OWN_TRANSACTION |在等候取得交易的擁有權時發生。| 
|XACT_RECLAIM_SESSION |在等候工作階段目前的擁有者釋出工作階段擁有權時發生。| 
|XACTLOCKINFO |在同步處理交易鎖定清單的存取作業時發生。 除了交易本身之外，諸如死結偵測和鎖定移轉等作業也會在頁面分割時存取鎖定清單。| 
|XACTWORKSPACE_MUTEX |在同步處理從交易脫離的作業，以及交易之編列成員之間的資料庫鎖定數目時發生。| 
|XDB_CONN_DUP_HASH |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|XDES_HISTORY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|XDES_OUT_OF_ORDER_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|XDES_SNAPSHOT |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|XDESTSVERMGR |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|XE_BUFFERMGR_ALLPROCESSED_EVENT |當擴充的事件工作階段緩衝區排清至目標時發生。 這項等候發生在背景執行緒中。| 
|XE_BUFFERMGR_FREEBUF_EVENT |當下列其中一個條件成立時發生：| 
|XE_CALLBACK_LIST |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|XE_CX_FILE_READ |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|XE_DISPATCHER_CONFIG_SESSION_LIST |當使用非同步目標的擴充的事件工作階段啟動或停止時發生。 這個等候表示下列其中一個狀況：| 
|XE_DISPATCHER_JOIN |當用於擴充的事件工作階段的背景執行緒結束時發生。| 
|XE_DISPATCHER_WAIT |當用於擴充的事件工作階段的背景執行緒正在等候事件緩衝區處理時發生。| 
|XE_FILE_TARGET_TVF |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|XE_LIVE_TARGET_TVF |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。| 
|XE_MODULEMGR_SYNC |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|XE_OLS_LOCK |僅供參考之用。 不支援。 我們無法保證未來的相容性。| 
|XE_PACKAGE_LOCK_BACKOFF |僅供參考之用。 不支援。 <br /> **適用**于：僅 [!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]。 |  
|XE_SERVICES_EVENTMANUAL |僅供內部使用。| 
|XE_SERVICES_MUTEX |僅供內部使用。| 
|XE_SERVICES_RWLOCK |僅供內部使用。| 
|XE_SESSION_CREATE_SYNC |僅供內部使用。| 
|XE_SESSION_FLUSH |僅供內部使用。| 
|XE_SESSION_SYNC |僅供內部使用。| 
|XE_STM_CREATE |僅供內部使用。| 
|XE_TIMER_EVENT |僅供內部使用。| 
|XE_TIMER_MUTEX |僅供內部使用。| 
|XE_TIMER_TASK_DONE |僅供內部使用。| 
|XIO_CREDENTIAL_MGR_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|XIO_CREDENTIAL_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|XIO_EDS_MGR_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|XIO_EDS_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|XIO_IOSTATS_BLOBLIST_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|XIO_IOSTATS_FCBLIST_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 及更新版本。| 
|XIO_LEASE_RENEW_MGR_RWLOCK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|XTP_HOST_DB_COLLECTION |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|XTP_HOST_LOG_ACTIVITY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|XTP_HOST_PARALLEL_RECOVERY |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|XTP_PREEMPTIVE_TASK |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|XTP_TRUNCATION_LSN |僅供內部使用。 <br /> **適用對象**：[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 及更新版本。| 
|XTPPROC_CACHE_ACCESS |在存取所有原生編譯的預存程式快取物件時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更新版本。| 
|XTPPROC_PARTITIONED_STACK_CREATE |在針對指定的程式配置每個 NUMA 節點原生編譯預存程式快取結構（必須針對單一執行緒執行）時發生。 <br /> **適用對象**：[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)] 及更新版本。|

  
 下列 XEvents 與資料分割**切換**和線上索引重建相關。 如需語法的詳細資訊，請參閱[ &#40;alter TABLE&#41; transact-sql](../../t-sql/statements/alter-table-transact-sql.md)和[alter &#40; &#41;INDEX transact-sql](../../t-sql/statements/alter-index-transact-sql.md)。  
  
-   lock_request_priority_state  
  
-   process_killed_by_abort_blockers  
  
-   ddl_with_wait_at_low_priority  
  
 如需鎖定相容性矩陣，請參閱[sys.databases &#40;dm_tran_locks&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)。  
  
## <a name="see-also"></a>另請參閱  
    
 [SQL Server 作業系統相關的動態管理 Views &#40;transact-sql&#41; ](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [dm_exec_session_wait_stats &#40;transact-sql&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-session-wait-stats-transact-sql.md)   
 [dm_db_wait_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-wait-stats-azure-sql-database.md)  
  
  


