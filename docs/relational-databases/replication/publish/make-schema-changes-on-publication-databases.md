---
title: "對發行集資料庫進行結構描述變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "複寫 [SQL Server], 結構描述變更"
  - "快照式複寫 [SQL Server], 複寫結構描述變更"
  - "合併式複寫 [SQL Server 複寫], 複寫結構描述變更"
  - "異動複寫, 複寫結構描述變更"
  - "結構描述 [SQL Server 複寫], 複寫變更"
  - "發行 [SQL Server 複寫], 結構描述變更"
ms.assetid: 926c88d7-a844-402f-bcb9-db49e5013b69
caps.latest.revision: 73
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 73
---
# 對發行集資料庫進行結構描述變更
  複寫支援對已發行物件進行大範圍的結構描述變更。 當您進行下列結構描述變更的任何針對適當已發行物件，在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行者，變更會傳播到所有的預設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 「 訂閱者 」:  
  
-   ALTER TABLE  
  
-   ALTER TABLE SET LOCK ESCALATION (如果結構描述變更複寫已啟用，且有拓撲包含 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或 [!INCLUDE[ssEWnoversion](../../../includes/ssewnoversion-md.md)] 訂閱者，則不應使用。) ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
     ALTER TRIGGER (僅可用於資料管理語言 [DML] 觸發器，因為無法複寫資料定義語言 [DDL] 觸發器。)  
  
> [!IMPORTANT]  
>  必須使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) 對資料表進行結構描述變更。 在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中進行結構描述變更時，[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 會嘗試卸除並重新建立資料表。 您無法卸除已發行的物件，因此結構描述變更會失敗。  
  
 對於異動複寫與合併式複寫，結構描述變更會在「散發代理程式」或「合併代理程式」執行時進行累加傳播。 對於快照式複寫，結構描述變更則在「訂閱者」套用新的快照集時進行傳播。 在快照式複寫中，每次發生同步處理時，結構描述的新副本便會傳送至「訂閱者」。 因此，對先前已發行物件進行的所有結構描述變更 (不僅僅是以上所列的變更) 會與每個同步處理一起自動傳播。  
  
 新增及移除發行集的發行項的相關資訊，請參閱 [新增和卸除現有的發行集的文章](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)。  
  
 **若要複寫結構描述變更**  
  
 依預設，會複寫以上所列的結構描述變更。 停用結構描述變更複寫的相關資訊，請參閱 [複寫結構描述變更](../../../relational-databases/replication/publish/replicate-schema-changes.md)。  
  
## 結構描述變更之考量  
 複寫結構描述變更時，請記住下列考量。  
  
### 一般考量  
  
-   結構描述變更必須遵從由 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 規定的任何條件約束。 例如，ALTER TABLE 不允許對主索引鍵資料行執行 ALTER。  
  
-   資料類型對應只會針對初始快照集執行。 結構描述變更並不會對應到舊版的資料類型。 例如，如果陳述式 `ALTER TABLE ADD datetime2 column` 用於 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], ，資料類型不會轉譯成 **nvarchar** 的 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 「 訂閱者 」。 在某些案例中，發行者上會封鎖結構描述變更。  
  
-   如果發行集設定為允許傳播結構描述變更，則不論發行集中發行項的相關結構描述選項如何設定，結構描述都會傳播。 例如，如果選取不對資料表發行項的外部索引鍵條件約束進行複寫，但是接著發出 ALTER TABLE 命令，將外部索引鍵新增至「發行者」端的資料表，則外部索引鍵會新增至「訂閱者」端的資料表。 若要防止發生這種情況，則在發出 ALTER TABLE 命令前停用結構描述變更的傳播。  
  
-   僅應在「發行者」而不是「訂閱者」端 (包括重新發行「訂閱者」) 進行結構描述變更。 合併式複寫防止在「訂閱者」端的結構描述變更。 異動複寫不會防止變更，但是變更會造成複寫失敗。  
  
-   依預設，傳播至重新發行訂閱者的變更會傳播至其訂閱者。  
  
-   如果結構描述變更參考了存在於「發行者」而不是「訂閱者」上的物件或條件約束，則結構描述變更會在「發行者」上成功，但會在「訂閱者」上失敗。  
  
-   新增外部索引鍵時所參考之「訂閱者」上所有物件的名稱和擁有者，必須與「發行者」上對應的物件相同。  
  
-   不支援明確地新增、卸除或改變索引。 支援為條件約束 (例如主索引鍵條件約束) 隱含建立的索引。  
  
-   不支援改變或卸除由複寫管理的識別欄位。 如需自動管理識別欄位的詳細資訊，請參閱 [複寫識別欄位](../../../relational-databases/replication/publish/replicate-identity-columns.md)。  
  
-   不支援包括非決定性函數的結構描述變更，因為該變更會導致「發行者」和「訂閱者」上的資料各不相同 (稱為非聚合)。 例如，如果在「發行者」端發出下列命令：`ALTER TABLE SalesOrderDetail ADD OrderDate DATETIME DEFAULT GETDATE()`，則將命令複寫至「訂閱者」並執行此命令時，值會各不相同。 如需非決定性函數的詳細資訊，請參閱 [決定性與非決定性函數](../../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)。  
  
-   建議對條件約束進行明確命名。 如果條件約束沒有明確命名，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會產生條件約束的名稱，並且這些名稱在發行者及每個訂閱者會有所不同。 在結構描述變更的複寫期間，這可能會造成問題。 例如，如果您卸除發行者端的資料行，並且卸除相依性條件約束，複寫便會嘗試卸除訂閱者端的條件約束。 因為條件約束名稱不同，所以訂閱者端的卸除動作會失敗。 如果同步處理因條件約束名稱問題而失敗，請手動卸除訂閱者端的條件約束，然後重新執行合併代理程式。  
  
-   發行資料表來進行複寫時，如果已產生發行集快照集，則無法將該資料表中的資料行改為 XML 資料類型。若要改變此資料行，您必須先移除複寫。  
  
-   在已發行的資料表上執行 DDL 時，讀取未認可不是一個支援的隔離等級。  
  
-   **SET CONTEXT_INFO** 不應修改交易的內容，針對已發行的物件執行結構描述變更。  
  
#### 新增資料行  
  
-   若要將新的資料行加入至資料表，並包含該資料行中現有的發行集，執行 ALTER TABLE \< 資料表> 新增 \< 資料行>。 依預設，資料行然後便會寫至所有「訂閱者」。 資料行必須允許 NULL 值或包含預設條件約束。 如需有關加入資料行的詳細資訊，請參閱本主題中的「合併式複寫」一節。  
  
-   若要將新的資料行加入資料表並不包含該資料行中現有的發行集，停用的結構描述變更複寫，然後執行 ALTER TABLE \< 資料表> 新增 \< 資料行>。  
  
-   若要加入現有的資料行中現有的發行集，使用 [sp_articlecolumn & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), ，[sp_mergearticlecolumn & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), ，或 **發行集屬性-\< 發行集>** 對話方塊。  
  
     如需詳細資訊，請參閱 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)。 這需要重新初始化訂閱。  
  
-   不支援在已發行的資料表上加入識別欄位，因為可能在資料行複寫至「訂閱者」時，導致無法聚合。 簽發者端識別欄位中的值，隨著受影響的資料表之資料列的實際儲存順序而不同。 資料列可能以不同方式儲存在訂閱者端；因此識別欄位的值可能與同資料列的不同。  
  
#### 卸除資料行  
  
-   若要從現有的發行集卸除資料行，並從 「 發行者 」 端的資料表中卸除資料行，請執行 ALTER TABLE \< 資料表> 卸除 \< 資料行>。 依預設，資料行然後便會從所有「訂閱者」端的資料表中卸除。  
  
-   若要從現有的發行集卸除資料行，但保留 「 發行者 」 端的資料表中的資料行，請使用 [sp_articlecolumn & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), ，[sp_mergearticlecolumn & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), ，或 **發行集屬性-\< 發行集>** 對話方塊。  
  
     如需詳細資訊，請參閱 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)。 這需要產生新的快照集。  
  
-   要卸除的資料行不可以用於資料庫內任何發行集，任何發行項的篩選子句。  
  
-   卸除已發行之發行項的資料行時，請考慮會影響資料庫的任何條件約束、索引或資料行屬性。 例如：  
  
    -   您無法從交易式發行集的發行項中卸除使用於主索引鍵的資料行，因為它們由複寫使用。  
  
    -   無法從合併式發行集的發行項中卸除 rowguid 資料行，或從支援更新訂閱之交易式發行集的發行項中卸除 mstran_repl_version 資料行，因為它們由複寫使用。  
  
    -   索引變更不會傳播至訂閱者：如果您卸除發行者端的資料行，並且卸除相依性條件約束，則不會複寫索引卸除。 您必須先卸除訂閱者端的索引，然後卸除發行者端的資料行，如此一來，從發行者複寫至訂閱者時才會成功將資料行卸除。 如果同步處理因訂閱者端的索引而失敗，請手動卸除索引，然後重新執行合併代理程式。  
  
    -   條件約束應明確命名，才能允許卸除。 如需詳細資訊，請參閱本主題中的「一般考量」一節。  
  
### 異動複寫  
  
-   結構描述變更傳播至執行舊版 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的「訂閱者」，但是 DDL 陳述式應僅包含「訂閱者」端版本所支援的語法。  
  
     如果「訂閱者」重新發行資料，則唯一受支援的結構描述變更會新增及卸除資料行。 應該在 「 發行者 」 端進行這些變更使用 [sp_repladdcolumn & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-repladdcolumn-transact-sql.md) 和 [sp_repldropcolumn & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-repldropcolumn-transact-sql.md) 而不是 ALTER TABLE DDL 語法。  
  
-   結構描述變更不會複寫到非 SQL Server 訂閱者。  
  
-   結構描述變更不會從非 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行者傳播。  
  
-   您無法改變複寫為資料表的索引檢視表。 複寫為索引檢視的索引檢視可以改變，但是改變它們會使其變成一般的檢視而不是索引檢視。  
  
-   如果發行集支援立即更新或佇列更新訂閱，則在進行結構描述變更之前必須停止系統：已發行資料表上的所有活動必須在「發行者」或「訂閱者」端停止，且暫止資料變更必須傳播至所有節點。 結構描述變更傳播至所有節點之後，可於已發行的資料表上繼續進行活動。  
  
-   如果發行集在點對點拓撲中，則進行結構描述變更前必須停止系統。 如需詳細資訊，請參閱 [停止複寫拓樸 & #40。複寫 TRANSACT-SQL 程式設計 & #41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)。  
  
-   將時間戳記資料行新增至資料表並將時間戳記對應至 binary(8)，會造成所有作用中訂閱的發行項重新初始化。  
  
### 合併式複寫  
  
-   合併式複寫如何處理結構描述變更是由發行集相容性層級以及快照集是設定為原生模式 (預設值) 還是字元模式而定：  
  
    -   若要複寫結構描述變更，則發行集的相容性層級必須至少為 90RTM。 如果 「 訂閱者 」 執行的舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或相容性層級低於的 90RTM，您可以使用 [sp_repladdcolumn & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-repladdcolumn-transact-sql.md) 和 [sp_repldropcolumn & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-repldropcolumn-transact-sql.md) 若要新增卸除資料行。 不過，這些程序都已被取代。  
  
    -   如果您嘗試將具有 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 中導入之資料類型的資料行加入到現有發行項，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 便具有以下行為：  
  
        ||100RTM，原生快照集|100RTM，字元快照集|所有其他相容性層級|  
        |-|-----------------------------|--------------------------------|------------------------------------|  
        |**hierarchyid**|允許變更|封鎖變更|封鎖變更|  
        |**地理位置** 和 **幾何**|允許變更|允許變更*|封鎖變更|  
        |**檔案資料流**|允許變更|封鎖變更|封鎖變更|  
        |**日期**, ，**時間**, ，**datetime2**, ，和 **datetimeoffset**|允許變更|允許變更*|封鎖變更|  
  
         * SQL Server Compact 訂閱者會在訂閱者上轉換這些資料類型。  
  
-   如果套用結構描述變更時發生錯誤 (例如，因為新增參考了「訂閱者」端上不可用之資料表的外部索引鍵而發生的錯誤)，則同步處理會失敗且必須重新初始化訂閱)。  
  
-   如果在聯結篩選或參數化篩選涉及的資料行上進行結構描述變更，則必須重新初始化所有訂閱並重新產生快照集。  
  
-   合併式複寫會提供預存程序，以在疑難排解期間略過結構描述變更。 如需詳細資訊，請參閱 [sp_markpendingschemachange & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-markpendingschemachange-transact-sql.md) 和 [sp_enumeratependingschemachanges & #40。TRANSACT-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md)。  
  
## 另請參閱  
 [ALTER TABLE & #40。TRANSACT-SQL & #41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER VIEW & #40。TRANSACT-SQL & #41;](../../../t-sql/statements/alter-view-transact-sql.md)   
 [ALTER PROCEDURE & #40。TRANSACT-SQL & #41;](../../../t-sql/statements/alter-procedure-transact-sql.md)   
 [ALTER FUNCTION & #40。TRANSACT-SQL & #41;](../../../t-sql/statements/alter-function-transact-sql.md)   
 [ALTER TRIGGER & #40。TRANSACT-SQL & #41;](../../../t-sql/statements/alter-trigger-transact-sql.md)   
 [發行資料和資料庫物件](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [重新產生自訂交易程序以反映結構描述變更](../../../relational-databases/replication/transactional/regenerate-custom-transactional-procedures-to-reflect-schema-changes.md)  
  
  