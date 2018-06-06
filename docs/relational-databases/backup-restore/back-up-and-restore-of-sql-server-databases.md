---
title: SQL Server 資料庫的備份與還原 | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], see restoring [SQL Server]
- backups [SQL Server]
- restoring databases [SQL Server]
- backup [SQL Server], see backing up [SQL Server]
- databases [SQL Server], restoring
- backing up databases [SQL Server]
- restore [SQL Server], see restoring [SQL Server]
- disaster recovery [SQL Server], see backing up [SQL Server]
- backing up [SQL Server]
- Database Engine [SQL Server], backups
- databases [SQL Server], backups
ms.assetid: 570a21b3-ad29-44a9-aa70-deb2fbd34f27
caps.latest.revision: 91
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f5a985cffb4aa982e598cbaaeb5c8ddb57133fd7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34708026"
---
# <a name="back-up-and-restore-of-sql-server-databases"></a>SQL Server 資料庫的備份與還原
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本文描述備份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的優點、基本備份和還原詞彙，並介紹 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的備份和還原策略，以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份和還原的安全性考量。 

> **尋找逐步指示嗎？** 本主題 **未提供如何執行備份的任何特定步驟！** 如果您想要正確實際備份，請將此頁面捲動至 [連結] 區段，並依備份工作組織，以及是否想要使用 SSMS 或 T-SQL。  
  
 SQL Server 備份與還原元件提供基本的防護措施，可保護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中所儲存的重要資料。 若要將重大資料遺失的風險降到最低，則需要定期備份資料庫，以保留對資料的修改。 計畫完善的備份和還原策略，可協助保護資料庫免於因各種失敗造成損毀而遺失資料。 藉由還原備份組再復原資料庫，以測試您的策略，讓您準備好有效因應損毀情況。
  
 除了儲存備份的本機儲存體之外，SQL Server 也支援備份至與還原自 Windows Azure Blob 儲存體服務。 如需詳細資訊，請參閱 [使用 Microsoft Azure Blob 儲存體服務進行 SQL Server 備份及還原](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。 針對使用 Microsoft Azure Blob 儲存體服務儲存的資料庫檔案， [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 的 Azure 快照集選項，提供近乎即時的備份及更快速的還原。 如需詳細資訊，請參閱 [Azure 中資料庫檔案的檔案快照集備份](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)。  
  
##  <a name="why-back-up"></a>備份原因  
-   備份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫、針對備份執行測試還原程序，並將備份的複本儲存在安全的異地位置，即可避免可能發生的重大資料遺失。 **備份是保護資料的的唯一方法。**

     使用有效的資料庫備份，就可以從多種失敗中復原資料，例如：  
  
    -   媒體錯誤。    
    -   使用者錯誤 (例如不小心卸除資料表)。    
    -   硬體故障 (例如，磁碟機損壞或伺服器永久損毀)。    
    -   天然災害。 藉由對 Windows Azure Blob 儲存體服務使用 SQL Server 備份，就可以在與內部部署位置不同的區域建立異地備份，以便在發生影響內部部署位置的天然災害事件時使用。  
  
-   此外，資料庫備份對於例行管理很有用，例如，將資料庫從一部伺服器複製到另一部伺服器、設定 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 或資料庫鏡像，以及封存。  
  
##  <a name="glossary-of-backup-terms"></a>備份詞彙表
 **備份** [動詞]  
 將資料或記錄檔記錄從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫或其交易記錄複製至備份裝置 (例如磁碟)，以建立資料備份或記錄備份。  
  
 **備份** [名詞]  
 失敗後可用來還原和復原資料的資料複本。 資料庫備份也可用來將資料庫的複本還原到新位置。  
  
**備份** 裝置  
 寫入 SQL Server 備份並從中進行還原的磁碟或磁帶裝置。 SQL Server 備份也可以寫入 Microsoft Azure Blob 儲存體服務，而且會使用 **URL** 格式來指定備份檔案的目的地和名稱。 如需詳細資訊，請參閱 [使用 Microsoft Azure Blob 儲存體服務進行 SQL Server 備份及還原](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。  
  
**備份媒體**  
 已寫入一或多個備份的一或多個磁帶或磁碟檔案。  
  
**資料備份**  
 整個資料庫 (資料庫備份)、部分資料庫 (部分備份) 或是一組資料檔案或檔案群組 (檔案備份) 中資料的備份。  
  
**資料庫備份**  
 資料庫的備份。 完整資料庫備份代表備份完成時的整個資料庫。 差異資料庫備份僅包含自其最近的完整資料庫備份以來，對資料庫所做的變更。  
  
**差異備份**  
 一種資料備份，是以整個或部分資料庫或一組資料檔案或檔案群組 (差異基底) 的最新完整備份為基礎，而且只包含自該基底以來變更的資料。  
  
**完整備份**  
 一種資料備份，包含特定資料庫或一組檔案群組或檔案中的所有資料，也包含足以讓這個資料復原的記錄。  
  
**記錄備份**  
 交易記錄的備份，包含先前的記錄備份中未備份的所有記錄。 (完整復原模式)  
  
**復原 (recover)**  
 將資料庫回復為穩定且一致的狀態。  
  
**recovery**  
 讓資料庫進入交易一致狀態的資料庫啟動階段或含復原之還原的階段。  
  
**復原模式**  
 控制資料庫上交易記錄維護的資料庫屬性。 復原模式共有三種：簡單、完整和大量記錄。 資料庫的復原模式決定其備份和還原需求。  
  
**還原**  
 一個多階段的程序，它會將指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份中的所有資料和記錄頁面複製到指定的資料庫中，然後藉由套用所記錄的變更取得前面時段的資料，向前復原備份中記錄的所有交易。  
  
 ##  <a name="backup-and-restore-strategies"></a>備份與還原策略  
 備份和還原資料作業必須依特定環境自訂，而且也必須使用可用的資源。 因此，為了可靠地使用備份和還原作業進行復原，您需要擬定備份和還原策略。 設計良好的備份和還原策略可充分提高資料可用性，並使資料損失降至最少，同時考慮到您的特定業務需求。  
  
  > [!IMPORTANT] 
  > 請將資料庫和備份放置於不同的裝置上。 否則，如果包含資料庫的裝置故障，備份將無法使用。 將資料和備份放置於不同的裝置，也可以針對寫入備份和資料庫生產使用強化 I/O 效能。**  
  
 備份和還原策略包含備份部分與還原部分。 策略的備份部分定義備份的類型和頻率、所需硬體的本質和速度、測試備份的方法，以及儲存備份媒體的位置與方法 (包括安全性考量)。 策略的還原部分定義誰負責執行還原，以及應該如何執行還原，以達到資料庫可用性並將資料損失降到最低的目標。 建議您寫下備份和還原程序，並將文件的副本保留在執行書中。  
  
 設計有效的備份和還原策略需要仔細計畫、實作及測試。 測試是必要的。 在利用還原策略中包含的所有備份組合順利完成還原之前，您還稱不上有備份策略。 您必須考慮各種因素。 這些選項包括：  
  
-   您的組織對於資料庫的生產目標，特別是對資料可用性以及保護資料免於遺失的需求。  
  
-   您的每一個資料庫的本質：其大小、使用模式、內容本質及資料需求等等。  
  
-   相關資源的限制，例如：硬體、人員、儲存備份媒體的空間、儲存媒體的實體安全性等等。  

### <a name="impact-of-the-recovery-model-on-backup-and-restore"></a>復原模式對備份和還原的影響  
 備份和還原作業是在復原模式的內容中發生。 復原模式是控制交易記錄管理方式的資料庫屬性。 此外，資料庫的復原模式也將決定資料庫所支援的備份類型與還原實例。 一般而言，資料庫會使用完整復原模式或簡單復原模式。 完整復原模式可以藉由在大量作業之前切換到大量記錄復原模式，補充其功能。 如需這些復原模式及其對交易記錄管理之影響的簡介，請參閱 [交易記錄 (SQL Server)](https://msdn.microsoft.com/library/ms190925(SQL.130).aspx)  
  
 資料庫復原模式的最佳選擇視您的商務需求而定。 若要避免管理交易記錄，並簡化備份和還原，請使用簡單復原模式。 若要將遺失工作的風險降到最低 (但會耗用管理負擔成本)，請使用完整復原模式。 如需復原模式對備份與還原之影響的資訊，請參閱 [備份概觀 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)。  
  
### <a name="design-your-backup-strategy"></a>設計備份策略  
 在為特定資料庫選擇符合商務需求的復原模式之後，您必須規劃並實作對應的備份策略。 最佳備份策略取決於各種因素，其中特別重要的是下列項目：  
  
-   應用程式每天必須花多少時間來存取資料庫？  
  
     如果可預測離峰期間，則建議您排定該期間內完整資料庫備份的作業時程。  
  
-   可能發生變更和更新的頻率為何？  
  
     如果經常變更，請考慮下列作法：  
  
    -   在簡單復原模式下，請考慮在完整資料庫備份之間排程差異備份。 差異備份只會擷取最後一次完整資料庫備份之後所發生的變更。  
  
    -   在完整復原模式下，您應排程經常的記錄備份。 在完整備份之間排定差異備份，可減少您在還原資料後必須還原的記錄備份數目，從而減少還原時間。  
  
-   變更可能會發生在資料庫的一小部分，還是資料庫的大部分？  
  
     如果是大型資料庫，且其變更集中於檔案或檔案群組部分，則部分備份及 (或) 檔案備份可能十分有用。 如需詳細資訊，請參閱[部分備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/partial-backups-sql-server.md) 和[完整檔案備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-file-backups-sql-server.md)。  
  
-   完整資料庫備份需要多少磁碟空間？  
  
 ### <a name="estimate-the-size-of-a-full-database-backup"></a>估計完整資料庫備份的大小  
 在實作備份和還原策略前，您必須估計完整資料庫備份將使用多少磁碟空間。 備份作業會將資料庫中的資料複製到備份檔中。 備份僅包含資料庫中的實際資料，而不包含任何未使用的空間。 因此，備份通常會比資料庫本身還小。 您可以使用 **sp_spaceused** 系統預存程序來估計完整資料庫備份的大小。 如需詳細資訊，請參閱 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)。  
  
### <a name="schedule-backups"></a>排程備份  
 執行備份作業對進行中的交易影響最小，所以可以在一般作業過程中執行備份作業。 您可以執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份，並且將實際執行工作負載受到的影響降至最低。  
   
>  如需備份期間之並行限制的資訊，請參閱 [備份概觀 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)。  
  
 決定您需要的備份類型以及執行每一類型所需的頻率之後，建議您將一般備份排程為資料庫之資料庫維護計畫的一部分。 如需有關維護計畫以及如何為資料庫備份和記錄備份建立這些計畫的詳細資訊，請參閱＜ [Use the Maintenance Plan Wizard](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)＞。
  
### <a name="test-your-backups"></a>測試備份！  
 在您完成備份的測試之前，還不能算是具備還原策略。 您務必要將資料庫副本還原到測試系統，以針對每個資料庫完整測試備份策略。 您必須測試還原您要使用的每個備份類型。
  
 建議您維護每個資料庫的作業手冊。 這份作業手冊應記載備份位置、備份裝置名稱 (如果有的話)，以及還原測試備份所需的時間量。

## <a name="monitor-progress-with-xevent"></a>使用 xEvent 監視進度
由於資料庫的大小和涉及作業的複雜度，備份和還原作業可能需要相當長的時間。 當任一項作業引發問題時，您可以使用 **backup_restore_progress_trace** 擴充事件來即時監視進度。 如需擴充事件的詳細資訊，請參閱[擴充事件](../extended-events/extended-events.md)。

  >[!WARNING]
  > 使用 backup_restore_progress_trace 擴充事件可能會造成效能問題，而且會耗用大量的磁碟空間。 請於短時間內使用、小心執行，並且在生產環境中實作之前徹底測試。


```sql
-- Create the backup_restore_progress_trace extended event esssion
CREATE EVENT SESSION [BackupRestoreTrace] ON SERVER 
ADD EVENT sqlserver.backup_restore_progress_trace
ADD TARGET package0.event_file(SET filename=N'BackupRestoreTrace')
WITH (MAX_MEMORY=4096 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=5 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=OFF)
GO

-- Start the event session  
ALTER EVENT SESSION [BackupRestoreTrace]  
ON SERVER  
STATE = start;  
GO  

-- Stop the event session  
ALTER EVENT SESSION [BackupRestoreTrace]  
ON SERVER  
STATE = stop;  
GO  
```

### <a name="sample-output-from-extended-event"></a>來自擴充事件的範例輸出 

![備份 xevent 輸出的範例](media/back-up-and-restore-of-sql-server-databases/backup-xevent-example.png)
![還原 xevent 輸出的範例](media/back-up-and-restore-of-sql-server-databases/restore-xevent-example.png)
 
  
## <a name="more-about-backup-tasks"></a>深入了解備份工作  
-   [建立維護計畫](../../relational-databases/maintenance-plans/create-a-maintenance-plan.md)  
  
-   [建立作業](http://msdn.microsoft.com/library/b35af2b6-6594-40d1-9861-4d5dd906048c)  
  
-   [排程作業](http://msdn.microsoft.com/library/f626390a-a3df-4970-b7a7-a0529e4a109c)  
  
## <a name="working-with-backup-devices-and-backup-media"></a>使用備份裝置和備份媒體  
-   [定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [指定磁碟或磁帶作為備份目的地 &#40;SQL Server&#41;](../../relational-databases/backup-restore/specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [刪除備份裝置 &#40;SQL Server&#41;](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)  
  
-   [設定備份的到期日 &#40;SQL Server&#41;](../../relational-databases/backup-restore/set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [檢視備份組中的資料和記錄檔 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [從裝置還原備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="creating-backups"></a>建立備份  
**注意！** 如果是部分備份或只複製備份，就必須分別搭配 PARTIAL 或 COPY_ONLY 選項來使用 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](../../t-sql/statements/backup-transact-sql.md) 陳述式。  
  
 ### <a name="using-ssms"></a>使用 SSMS   
-   [建立完整資料庫備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [備份交易記錄 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [備份檔案和檔案群組 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [建立差異資料庫備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 ### <a name="using-t-sql"></a>使用 T-SQL  
-   [使用資源管理員來限制備份壓縮的 CPU 使用量 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [資料庫損毀時備份交易記錄 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [在備份或還原期間啟用或停用備份總和檢查碼 &#40;SQL Server&#41;](../../relational-databases/backup-restore/enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [指定在發生錯誤後備份或還原作業應該繼續還是停止 &#40;SQL Server&#41;](../../relational-databases/backup-restore/specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
## <a name="restore-data-backups"></a>還原資料備份 
### <a name="using-ssms"></a>使用 SSMS 
-   [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [將資料庫還原到新位置 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
  
-   [還原差異資料庫備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)  
  
-   [還原檔案和檔案群組 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-sql-server.md)  
  
### <a name="using-t-sql"></a>使用 T-SQL
-   [在簡單復原模式下還原資料庫備份 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [在完整復原模式下將資料庫還原至失敗點 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)  
  
-   [以覆蓋現有檔案的方式還原檔案與檔案群組 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [將檔案還原到新位置 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [還原 master 資料庫 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md)  

## <a name="restore-transaction-logs-full-recovery-model"></a>還原交易記錄 (完整復原模式)
### <a name="using-ssms"></a>使用 SSMS  
-   [還原資料庫至標示的交易 &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [還原交易記錄備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
 ### <a name="using-t-sql"></a>使用 T-SQL 
-   [將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](../../relational-databases/backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
 
-   [重新啟動中斷的還原作業 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restart-an-interrupted-restore-operation-transact-sql.md)  
  
-   [在不還原資料的情況下復原資料庫 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)  
 
## <a name="more-information-and-resources"></a>詳細資訊和資源
 [備份概觀 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [還原和復原概觀 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [備份與還原 Analysis Services 資料庫](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [備份並還原全文檢索目錄與索引。](../../relational-databases/search/back-up-and-restore-full-text-catalogs-and-indexes.md)   
 [備份及還原複寫的資料庫](../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [交易記錄 &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [復原模式 &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
