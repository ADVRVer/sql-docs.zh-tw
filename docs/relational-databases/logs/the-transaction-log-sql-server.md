---
title: 交易記錄 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], about
- databases [SQL Server], transaction logs
- logs [SQL Server], transaction logs
ms.assetid: d7be5ac5-4c8e-4d0a-b114-939eb97dac4d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cd975ed830f9a0b705e516707d550697fbf34325
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79287802"
---
# <a name="the-transaction-log-sql-server"></a>交易記錄 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫都有交易記錄來記錄所有交易及每項交易所作的資料庫修改。
  
交易記錄是資料庫的重要元件。 若系統故障，您便需要該記錄檔讓資料庫返回一致的狀態。 

如需交易記錄架構與內部項目的資訊，請參閱 [SQL Server 交易記錄架構與管理指南](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md)。

> [!WARNING] 
> 永遠不要刪除或移動此記錄檔，除非您完全了解這麼做的後果。 

> [!TIP]
> 檢查點會在資料庫復原期間建立開始套用交易記錄的已知恰當起點。 如需詳細資訊，請參閱[資料庫檢查點 (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md)。  
  
## <a name="operations-supported-by-the-transaction-log"></a>交易記錄所支援的作業  
 交易記錄檔支援下列作業：  
  
-   個別交易的復原。  
-   在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動時，復原所有未完成的交易。 
-   將還原的資料庫、檔案、檔案群組或頁面向前復原到失敗點。  
-   支援異動複寫。  
-   支援高可用性和災害復原解決方案： [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]、資料庫鏡像和記錄傳送。

### <a name="individual-transaction-recovery"></a>個別交易復原
若應用程式發出一個 `ROLLBACK` 陳述式，或若是 [!INCLUDE[ssde_md](../../includes/ssde_md.md)] 偵測到與用戶端的通訊中斷等錯誤，則記錄檔記錄可用來復原未完成交易所作的修改。 

### <a name="recovery-of-all-incomplete-transactions-when-ssnoversion-is-started"></a>在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動時復原所有未完成的交易
如果伺服器失敗，資料庫的狀態可能停留於緩衝區快取中有些修改尚未寫入資料檔中，並且未完成的交易已在資料檔中作了一些修改。 當啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，它會在每個資料庫上執行復原。 已記錄於記錄中、但尚未寫入資料檔中的每個修改將會向前復原。 將會回復交易記錄檔中所發現的每筆未完成交易，以確保資料庫的完整性。 如需詳細資訊，請參閱[還原和復原概觀 (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#TlogAndRecovery)。

### <a name="rolling-a-restored-database-file-filegroup-or-page-forward-to-the-point-of-failure"></a>將還原的資料庫、檔案、檔案群組或頁面向前復原到失敗點
在硬體損毀或磁碟失敗影響資料庫檔案後，您可以將資料庫還原至失敗點。 請先還原最後一次的完整資料庫備份和最後一次的差異資料庫備份，然後將後續一連串的交易記錄備份還原到失敗點。 

在還原每個記錄備份時，[!INCLUDE[ssde_md](../../includes/ssde_md.md)] 會重新套用記錄中的所有修改，以向前復原所有交易。 在還原最後一個記錄備份後，[!INCLUDE[ssde_md](../../includes/ssde_md.md)] 接著會使用記錄資訊來復原在該點尚未完成的所有交易。 如需詳細資訊，請參閱[還原和復原概觀 (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#TlogAndRecovery)。

### <a name="supporting-transactional-replication"></a>支援異動複寫
「記錄讀取器代理程式」會監視設定異動複寫的各資料庫交易記錄，並將標示要複寫的交易從交易記錄複製到散發資料庫中。 如需詳細資訊，請參閱 [異動複寫的運作方式](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms151706(v=sql.105))。

### <a name="supporting-high-availability-and-disaster-recovery-solutions"></a>支援高可用性和災害復原解決方案
待命伺服器方案、[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]、資料庫鏡像和記錄傳送都是高度依賴交易記錄。 

在 **[!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 案例**中，資料庫的每個更新 (主要複本) 都會立即在另一個完整的資料庫複本 (次要複本) 中重製。 主要複本會立即將每個記錄檔記錄傳送至次要複本，而它會將收到的記錄檔記錄套用到可用性群組資料庫，以持續向前復原。 如需詳細資訊，請參閱 [Always On 容錯移轉叢集執行個體](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)

在**記錄傳送案例**中，主要伺服器會傳送主要資料庫的使用中交易記錄至一或多個目的地。 每個次要伺服器都會將記錄檔還原至其本機次要資料庫。 如需詳細資訊，請參閱 [關於記錄傳送](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。 

在**資料庫鏡像案例**中，主體資料庫的每個更新都會立即在另一個完整的個別資料庫複本 (鏡像資料庫) 中重製。 主體伺服器執行個體會立即傳送每個記錄檔記錄到鏡像伺服器執行個體，而它會將傳入的記錄檔記錄套用至鏡像資料庫，以持續向前復原。 如需詳細資訊，請參閱 [資料庫鏡像](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。

##  <a name="Characteristics"></a>交易記錄特性
[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 交易記錄的特性： 
-  交易記錄是實作成資料庫中的個別檔案或一組檔案。 記錄檔快取是與資料頁的緩衝區快取分開管理，以在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 內產生簡單、快速和健全的程式碼。 如需詳細資訊，請參閱[交易記錄實體架構](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)。

-  記錄檔記錄與頁面的格式並不一定要遵照資料頁的格式。

-  交易記錄檔可實作於多個檔案上。 可以設定記錄檔的 `FILEGROWTH` 值，以定義記錄檔為自動擴充。 這減少了交易記錄檔用完空間的可能性，而同時又減少了管理上的額外負擔。 如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41; 檔案及檔案群組選項](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)。

-  重複使用記錄檔空間的機制很迅速，並對於交易輸送量的影響很小。

如需交易記錄架構與內部項目的資訊，請參閱 [SQL Server 交易記錄架構與管理指南](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md)。

##  <a name="Truncation"></a> 交易記錄截斷  
記錄截斷會釋出記錄檔中的空間，以供交易記錄重複使用。 您必須定期截斷交易記錄，以防止它填滿所分配的空間。 有數種因素會延遲記錄的截斷，所以監控記錄大小很重要。 某些作業可使用最低限度記錄，以減少其對交易記錄大小的影響。  
 
記錄截斷會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的邏輯交易記錄中刪除非使用中的[虛擬記錄檔 (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)，釋出邏輯記錄中的空間以供實體交易記錄重複使用。 如果永遠都不截斷交易記錄，最終將會填滿分配給實體記錄檔的所有磁碟空間。  
  
為了避免用盡空間，除非記錄截斷因為某個原因而延遲，否則將在以下事件後自動進行截斷：  
  
- 在簡單復原模式下，發生在檢查點之後。  
- 在完整復原模式或大量記錄復原模式下，如果上一次備份之後已產生檢查點，則截斷會發生在記錄備份之後 (除非它是只複製的記錄備份)。  
  
 如需詳細資訊，請參閱本主題稍後的[可能會延遲記錄截斷的因素](#FactorsThatDelayTruncation)。  
  
> [!NOTE]
> 記錄截斷並不會讓實體記錄檔變小。 若要減少實體記錄檔的實體大小，則必須壓縮記錄檔。 如需有關壓縮實體記錄檔大小的詳細資訊，請參閱＜ [管理交易記錄檔的大小](../../relational-databases/logs/manage-the-size-of-the-transaction-log-file.md)＞。  
> 不過，請記住[可能會延遲記錄截斷的因素](#FactorsThatDelayTruncation)。 如果壓縮記錄檔之後再次需要儲存空間，交易記錄檔將再次成長，並且會因此在記錄檔成長作業期間，導入效能額外負荷。
  
##  <a name="FactorsThatDelayTruncation"></a> Factors that can delay log truncation  
 當記錄檔記錄有一段很長的時間維持在使用中狀態時，交易記錄截斷會延遲，並填滿交易記錄，就像我們在這個長主題前面所提的一樣。  
  
> [!IMPORTANT]
> 如需如何對應寫滿交易記錄的相關資訊，請參閱 [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)。  
  
 實際上，記錄截斷可能會因為各種原因而延遲。 查詢 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 目錄檢視的 **log_reuse_wait** 和 **log_reuse_wait_desc** 資料行，了解是否有任何原因導致無法進行記錄截斷。 下表描述這些資料行的值。  
  
|log_reuse_wait 值|log_reuse_wait_desc 值|描述|  
|----------------------------|----------------------------------|-----------------|  
|0|NOTHING|目前有一或多個可重複使用的[虛擬記錄檔 (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)。|  
|1|CHECKPOINT|自從上次記錄截斷後尚未出現任何檢查點，或是記錄標頭尚未移到[虛擬記錄檔 (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) 的範圍之外。 (所有復原模式)<br /><br /> 這是延遲記錄截斷的一般原因。 如需詳細資訊，請參閱[資料庫檢查點 &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)。|  
|2|LOG_BACKUP|在截斷交易記錄前，需要進行記錄備份。 (僅限完整或大量記錄復原模式)<br /><br /> 當下一個記錄備份完成後，某些記錄空間可能就可以重複使用。|  
|3|ACTIVE_BACKUP_OR_RESTORE|正在進行資料備份或還原 (所有復原模式)。<br /><br /> 如果資料備份阻礙截斷記錄，則取消備份作業可能有助於化解眼前的問題。|  
|4|ACTIVE_TRANSACTION|交易在使用中 (所有復原模式)：<br /><br /> 長時間執行的交易可能存在於記錄備份的開頭。 在此情況下，釋出空間可能需要另一個記錄備份。 請注意，長時間執行的交易會避免所有復原模式下的記錄截斷，包括簡單復原模式，在該模式下，通常會在每一個自動檢查點截斷交易記錄。<br /><br /> 延遲交易。 *「延遲交易」* 實際上是回復遭到封鎖的使用中交易 (因為某些無法使用的資源所造成)。 如需有關延遲交易的原因以及如何將延遲交易移出延遲狀態的詳細資訊，請參閱[延遲交易 &#40;SQL Server&#41;](../../relational-databases/backup-restore/deferred-transactions-sql-server.md)。<br /> <br /> 長時間執行的交易可能也會填滿 tempdb 的交易記錄。 內部物件的使用者交易會隱含地使用 tempdb，例如進行排序的工作資料表、進行雜湊處理的工作檔案、資料指標工作資料表，以及資料列版本設定。 即使使用者交易只包括讀取資料 (`SELECT` 查詢)，還是可以在使用者交易下建立和使用內部物件。 因此，可能會填滿 tempdb 交易記錄。|  
|5|DATABASE_MIRRORING|資料庫鏡像已暫停，或者在高效能模式下，鏡像資料庫已大幅落後主體資料庫。 (僅限完整復原模式)<br /><br /> 如需詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。|  
|6|複寫|進行異動複寫期間，與發行集相關的交易仍然未傳遞至散發資料庫。 (僅限完整復原模式)<br /><br /> 如需有關異動複寫的詳細資訊，請參閱＜ [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md)＞。|  
|7|DATABASE_SNAPSHOT_CREATION|正在建立資料庫快照集。 (所有復原模式)<br /><br /> 這是延遲記錄截斷的一般原因 (通常也是暫時的原因)。|  
|8|LOG_SCAN|正在進行記錄掃描。 (所有復原模式)<br /><br /> 這是延遲記錄截斷的一般原因 (通常也是暫時的原因)。|  
|9|AVAILABILITY_REPLICA|可用性群組的次要複本正在將這個資料庫的交易記錄檔記錄套用到對應的次要資料庫。 (完整復原模式)<br /><br /> 如需詳細資訊，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)。|  
|10|-|僅供內部使用|  
|11|-|僅供內部使用|  
|12|-|僅供內部使用|  
|13|OLDEST_PAGE|如果將資料庫設定為使用間接檢查點，資料庫中最舊的頁面可能會比檢查點[記錄序號 (LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) 更舊。 在此情況下，最舊的頁面可能會延遲記錄截斷。 (所有復原模式)<br /><br /> 如需間接檢查點的相關資訊，請參閱 [Database Checkpoints &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)。|  
|14|OTHER_TRANSIENT|這個值目前尚未使用。|  
|16|XTP_CHECKPOINT|必須執行記憶體內部 OLTP 檢查點。針對經記憶體最佳化的資料表，當交易記錄檔自上一個檢查點之後變得大於 1.5 GB (同時包含磁碟型和經記憶體最佳化的資料表) 時，就會執行自動檢查點<br /> 如需詳細資訊，請參閱[經記憶體最佳化的資料表的檢查點作業](../../relational-databases/in-memory-oltp/checkpoint-operation-for-memory-optimized-tables.md)與 [記憶體內部最佳化資料表的記錄和檢查點處理] (https://blogs.msdn.microsoft.com/sqlcat/2016/05/20/logging-and-checkpoint-process-for-memory-optimized-tables-2/)
  
##  <a name="MinimallyLogged"></a> 可以進行最低限度記錄的作業  
「最低限度記錄」  包含僅記錄復原交易所需的資訊，不支援時間點復原。 這個主題將識別在大量記錄 [復原模式](../backup-restore/recovery-models-sql-server.md) 下 (以及簡單復原模式下，但備份正在執行時除外) 會進行最低限度記錄的作業。  
  
> [!NOTE]
> 記憶體最佳化資料表不支援最低限度記錄。  
  
> [!NOTE]
> 在完整 [復原模式](../backup-restore/recovery-models-sql-server.md)下，將完整記錄所有大量作業。 不過，您可以暫時針對大量作業，將資料庫切換成大量記錄復原模式，藉以將大量作業集的記錄降至最低。 最低限度記錄會比完整記錄更具效率，並降低大規模的大量作業在大量交易期間，填滿可用交易記錄空間的可能性。 然而，如果資料庫在最低限度記錄作用時損毀或遺失，您就無法將資料庫復原至失敗點。  
  
 下列作業 (在完整復原模式下會完整記錄) 在簡單和大量記錄復原模式下會進行最低限度記錄：  
  
-   大量匯入作業 ([bcp](../../tools/bcp-utility.md)、[BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) 及 [INSERT...SELECT](../../t-sql/statements/insert-transact-sql.md))。 如需何時大量匯入至資料表會採用最低限度記錄的詳細資訊，請參閱＜ [Prerequisites for Minimal Logging in Bulk Import](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)＞。  
  
啟用異動複寫時，即使在大量記錄復原模式下也會完整記錄 `BULK INSERT`作業。  
  
-   [SELECT INTO](../../t-sql/queries/select-into-clause-transact-sql.md) 作業。  
  
啟用異動複寫時，即使在大量記錄復原模式下也會完整記錄 `SELECT INTO`作業。  
  
-   插入或附加新資料時，在 [UPDATE](../../t-sql/queries/update-transact-sql.md) 陳述式中使用 `.WRITE` 子句，對大數值資料類型執行的部分更新。 請注意，更新現有值時不使用最低限度記錄。 如需有關大數值資料類型的詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)。  
  
-   將新的資料插入或附加至[nUPDATETEXT](../../t-sql/queries/writetext-transact-sql.md) 、 [nUPDATETEXT](../../t-sql/queries/updatetext-transact-sql.md) 和 **UPDATETEXT**, **nUPDATETEXT**, 、 **UPDATETEXT** 陳述式。 請注意，更新現有值時不使用最低限度記錄。  
  
    > [!WARNING]
    > `WRITETEXT` 與 `UPDATETEXT` 陳述式**已被取代**，所以您應該避免在新的應用程式中加以使用。  
  
-   如果資料庫設定為簡單或大量記錄復原模式，則不管作業是離線執行或線上執行，某些索引 DDL 作業都是以最低限度的方式記錄。 以最低限度方式記錄的索引作業如下：  
  
    -   [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md) 作業 (包括索引檢視表)。  
  
    -   [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) REBUILD 或 DBCC DBREINDEX 作業。  
  
        > [!WARNING]
        > `DBCC DBREINDEX` 陳述式**已被淘汰**；請避免在新的應用程式中使用。  
  
    -   [DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md) 新堆積重建 (如果適用)。 `DROP INDEX`作業期間的索引頁取消配置**一律**經完整記錄。
  
##  <a name="RelatedTasks"></a> Related tasks  
**管理交易記錄**  
  
-   [管理交易記錄檔的大小](../../relational-databases/logs/manage-the-size-of-the-transaction-log-file.md)  
  
-   [寫滿交易記錄疑難排解 &#40;SQL Server 錯誤 9002&#41;](../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
**備份交易記錄 (完整復原模式)**  
  
-   [備份交易記錄 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  

-   [資料庫損毀時備份交易記錄 (SQL Server)](../../relational-databases/backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)

**還原交易記錄 (完整復原模式)**  
  
-   [還原交易記錄備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a>另請參閱  
[SQL Server 交易記錄架構與管理指南](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md)   
[控制交易持久性](../../relational-databases/logs/control-transaction-durability.md)   
[大量匯入採用最低限度記錄的必要條件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)   
[SQL Server 資料庫的備份與還原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)     
[還原和復原概觀 (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#TlogAndRecovery)      
[資料庫檢查點 &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)   
[檢視或變更資料庫的屬性](../../relational-databases/databases/view-or-change-the-properties-of-a-database.md)   
[復原模式 &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
[交易記錄備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)    
[sys.dm_db_log_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)  
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)    
  
  
