---
title: "記憶體內部 OLTP 不支援的 SQL Server 功能 | Microsoft Docs"
ms.custom: ""
ms.date: "10/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c39f03a7-e223-4fd7-bd30-142e28f51654
caps.latest.revision: 55
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 55
---
# 記憶體內部 OLTP 不支援的 SQL Server 功能
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  本主題探討在使用記憶體最佳化的物件時不受支援的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。  
  
## [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體內部 OLTP 不支援的功能  
 擁有記憶體最佳化之物件的資料庫不支援下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能，包括記憶體最佳化的資料檔案群組在內。  
  
|不支援的功能|功能描述|  
|-------------------------|-------------------------|  
|記憶體最佳化之資料表的資料壓縮。|使用資料壓縮功能有助於將資料壓縮在資料庫內及縮小資料庫的大小。 如需詳細資訊，請參閱 [Data Compression](../../relational-databases/data-compression/data-compression.md)。|  
|記憶體最佳化之資料表、雜湊索引與非叢集索引的資料分割。|資料分割資料表和索引的資料，已分成可以在資料庫中的多個檔案群組之間分佈的單位。 如需詳細資訊，請參閱 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)。|  
|複寫|訂閱者端記憶體最佳化資料表的異動複寫以外的複寫組態與參考記憶體最佳化資料表的資料表或檢視表不相容。 如果有記憶體最佳化檔案群組，則不支援使用 sync_mode=’database snapshot’ 的複寫。 如需詳細資訊，請參閱[複寫至記憶體最佳化資料表訂閱者](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md)。|  
|鏡像|具有 MEMORY_OPTIMIZED_DATA 檔案群組的資料庫不支援資料庫鏡像。 如需鏡像的詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。|  
|重建記錄檔|具有 MEMORY_OPTIMIZED_DATA 檔案群組的資料庫不支援透過附加或 ALTER DATABASE 重建記錄檔。|  
|連結的伺服器|在以記憶體最佳化資料表形式的相同查詢或交易中，您無法存取連結的伺服器。 如需詳細資訊，請參閱[連結的伺服器 &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)。|  
|大量記錄|無論資料庫使用何種復原模式，所有在持久性記憶體最佳化的資料表上的作業，一律會完整記錄。|  
|最低限度記錄|記憶體最佳化資料表不支援最低限度記錄。 如需最低限度記錄的詳細資訊，請參閱[交易記錄 &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md) 和[大量匯入採用最低限度記錄的必要條件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)。|  
|變更追蹤|變更追蹤可在具有記憶體中 OLTP 物件的資料庫上啟用。 不過，記憶體最佳化的資料表中的變更不會受到追蹤。|  
|DDL 觸發程序|記憶體內部 OLTP 資料表和原生編譯預存程序皆不支援資料庫層級與伺服器層級的 DDL 觸發程序。|  
|異動資料擷取 (CDC)|CDC 不能搭配使用具有記憶體最佳化資料表的資料庫，因為它實際上是使用 DROP TABLE 的 DDL 觸發程序。|  
|Fiber 模式|記憶體最佳化資料表不支援 Fiber 模式：<br /><br /> 如果 Fiber 模式為使用中，您就無法建立具有記憶體最佳化檔案群組的資料庫，或將記憶體最佳化檔案群組加入至現有的資料庫。<br /><br /> 如果具有記憶體最佳化檔案群組的資料庫已存在，您可以啟用 Fiber 模式。 不過，啟動 Fiber 模式需要重新啟動伺服器。 在該情況下，具有記憶體最佳化檔案群組的資料庫會無法復原，而且您會看到一則錯誤訊息，建議您停用 Fiber 模式以使用具有記憶體最佳化檔案群組的資料庫。<br /><br /> 如果 Fiber 模式為使用中，附加與還原具有記憶體最佳化檔案群組的資料庫將會失敗。 資料庫將標示為可疑。<br /><br /> <br /><br /> 如需詳細資訊，請參閱[輕量型共用伺服器組態選項](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)。|  
|Service Broker 的限制|無法從原生編譯的預存程序存取佇列。<br /><br /> 也無法在存取記憶體最佳化的資料表的交易中存取遠端資料庫內的佇列。|  
|訂閱者的複寫|系統支援訂閱者端之記憶體最佳化資料表的異動複寫，但是有一些限制。 如需詳細資訊，請參閱[複寫至記憶體最佳化資料表訂閱者](../../relational-databases/replication/replication-to-memory-optimized-table-subscribers.md)|  
  
 有一些例外狀況，不支援跨資料庫的交易。 下表描述支援的案例和對應的限制。 (另請參閱[跨資料庫查詢](../../relational-databases/in-memory-oltp/cross-database-queries.md))。  
  
|資料庫|Allowed|描述|  
|---------------|-------------|-----------------|  
|使用者資料庫、model 和 msdb。|否|不支援跨資料庫的查詢和交易。<br /><br /> 存取記憶體最佳化的資料表或原生編譯的預存程序的查詢和交易都無法存取其他資料庫，但是系統資料庫 master (用於唯讀存取) 和 tempdb 例外。|  
|資源資料庫、tempdb|是|跨資料庫交易並沒有限制，除了單一使用者資料庫以外，只能使用資源資料庫和 tempdb。|  
|master|唯讀|如果包含任何寫入 master 資料庫的作業，則接觸記憶體中 OLTP 和 master 資料庫的跨資料庫交易認可會失敗。 只允許從 master 讀取及使用一個使用者資料庫的跨資料庫交易。|  
  
## 不支援的案例  
  
-   記憶體內部 OLTP 不支援資料庫的內含項目 ([自主資料庫](../../relational-databases/databases/contained-databases.md))。 支援自主資料庫驗證。 不過，所有記憶體中 OLTP 物件在 DMV dm_db_uncontained_entities 中都會標示為中斷內含項目 (Breaking Containment)。  
  
-   使用內容連接，從 CLR 預存程序內部存取記憶體最佳化的資料表。  
  
-   存取記憶體最佳化資料表之查詢上的索引鍵集與動態資料指標。 這些資料指標會降級為靜態，且為唯讀。  
  
-   搭配 *target* 使用 **MERGE INTO***target* 即為記憶體最佳化資料表。 記憶體最佳化資料表支援 **MERGE USING***source*。  
  
-   不支援 ROWVERSION (TIMESTAMP) 資料類型。 如需詳細資訊，請參閱 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)。  
  
-   具有 MEMORY_OPTIMIZED_DATA 檔案群組的資料庫不支援自動關閉。  
  
-   具有 MEMORY_OPTIMIZED_DATA 檔案群組的資料庫不支援資料庫快照集。  
  
-   交易式 DDL。 使用者交易內不支援記憶體內部 OLTP 物件的 CREATE/ALTER/DROP。  
  
-   事件通知。  
  
-   原則式管理 (PBM)。 不會阻止並只記錄 PBM 的模式。 伺服器上存在這類原則時，可能會使記憶體中 OLTP DDL 無法成功執行。 支援視需要和依排程模式。  
  
## 另請參閱  
 [記憶體中 OLTP 的 SQL Server 支援](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)  
  
  