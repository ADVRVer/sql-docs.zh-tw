---
title: "資料行存放區索引 - 新功能 | Microsoft Docs"
ms.custom: 
ms.date: 12/1/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: indexes
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fe5ea05-5b19-45a4-9b7a-8ae5ca367897
caps.latest.revision: "28"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 24426c82299598fbf80b31b8d2a1ee24b6142d9a
ms.sourcegitcommit: ea68e8a68ee58584dd52035ed3d611a69b6c3818
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="columnstore-indexes---what39s-new"></a>資料行存放區索引 - 新功能
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  每個版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以及最新版的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium Edition、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 都有資料行存放區功能摘要。  

 > [!NOTE]
 > 針對 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]，資料行存放區索引僅適用於 Premium Edition。
 
## <a name="feature-summary-for-product-releases"></a>產品版本的功能摘要  
 本表會摘要說明資料行存放區索引的重要功能以及提供它們的產品。  

|資料行存放區索引功能|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]|[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]|  
|-------------------------------|---------------------------|---------------------------|---------------------------|--------------------------------------------|-------------------------|---|  
|批次執行多執行緒查詢|是|是|是|是|是|是| 
|批次執行單一執行緒查詢|||是|是|是|是|  
|封存壓縮選項||是|是|是|是|是|  
|快照集隔離和讀取認可快照集隔離|||是|是|是|是| 
|建立資料表時指定資料行存放區索引|||是|是|是|是|  
|AlwaysOn 支援資料行存放區索引|是|是|是|是|是|是| 
|AlwaysOn 可讀取次要支援唯讀的非叢集資料行存放區索引|是|是|是|是|是|是|  
|AlwaysOn 可讀取次要支援可更新的資料行存放區索引|||是|是|||  
|堆積或 B-tree 的唯讀非叢集資料行存放區索引|是|是|是 <sup>1</sup>|是 <sup>1</sup>|是 <sup>1</sup>|是 <sup>1</sup>|  
|堆積或 B-tree 的可更新非叢集資料行存放區索引|||是|是|是|是|  
|有非叢集資料行存放區索引的堆積或 B-tree 允許其他的 B-tree 索引|是|是|是|是|是|是|  
|可更新的叢集資料行存放區索引||是|是|是|是|是|  
|叢集資料行存放區索引的 B-tree 索引|||是|是|是|是|  
|記憶體最佳化資料表的資料行存放區索引|||是|是|是|是|  
|非叢集資料行存放區索引定義支援使用篩選的條件|||是|是|是|是|  
|`CREATE TABLE` 和 `ALTER TABLE` 中資料行存放區索引的壓縮延遲選項|||是|是|是|是|
|資料行存放區索引可以具有非保存的計算資料行||||是|||   
  
 <sup>1</sup> 若要建立可讀取的非叢集資料行存放區索引，請將索引儲存在唯讀的檔案群組中。  

## [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 
 [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 新增這些新功能。

### <a name="functional"></a>功能
- [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 支援叢集資料行存放區索引中的非保存計算資料行。 叢集資料行存放區索引不支援保存的資料行。您無法在具有計算資料行的資料行存放區索引上建立非叢集索引。 

## [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 會加入索引鍵增強功能，以改善資料行存放區索引的效能和彈性。 這些改善會強化資料倉儲案例，並進行即時作業分析。  
  
### <a name="functional"></a>功能  
  
-   資料列存放區資料表可以有一個可更新的非叢集資料行存放區索引。 非叢集資料行存放區索引以前是唯讀的。  
  
-   非叢集資料行存放區索引定義支援使用篩選的條件。 若要將 OLTP 資料表新增資料行存放區索引對效能的影響降到最低，請只對您作業的工作負載冷資料，使用篩選的條件建立非叢集資料行存放區索引。 
  
-   記憶體中的資料表可以有一個資料行存放區索引。 您可以在建立資料表時予以建立，或稍後使用 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md) 將其加入。 從前，只有磁碟資料表可以有資料行存放區索引。  
  
-   叢集資料行存放區索引可以有一或多個非叢集資料列存放區索引。 資料行存放區索引以前不支援非叢集索引。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會自動維護 DML 作業的非叢集索引。  
  
-   您可以使用 B-tree 索引對叢集資料行存放區索引強制執行這些條件約束，來支援主索引鍵和外部索引鍵。  
  
-   資料行存放區索引的壓縮延遲選項，可將即時作業分析的交易工作負載影響降到最低。  這個選項允許經常變更的資料列在穩定後，再壓縮到資料行存放區。 如需詳細資訊，請參閱 [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md) 和[開始使用資料行存放區進行即時作業分析](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)。  
  
### <a name="performance-for-database-compatibility-level-120-or-130"></a>資料庫相容性等級 120 或 130 的效能  
  
-   資料行存放區索引支援讀取認可快照集隔離等級 (RCSI) 和快照集隔離 (SI)。 這可讓交易式一致性分析查詢沒有任何鎖定。  
  
-   資料行存放區透過移除刪除的資料列，但不必明確重建索引，來支援索引重組。 `ALTER INDEX … REORGANIZE` 陳述式會根據內部定義的原則，如同線上作業從資料行存放區中移除已刪除的資料列  
  
-   您可以在 AlwaysOn 可讀取次要複本上存取資料行存放區索引。 您可以將分析查詢卸載到 AlwaysOn 次要複本，以改善作業分析的效能。  
  
-   為改善效能，當資料類型使用不超過 8 個位元組，且不是字串類型時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在資料表掃描期間計算彙總函式 `MIN`、`MAX`、`SUM`、`COUNT` 和 `AVG`。 無論是否使用 Group By 子句，叢集資料行存放區索引和非叢集資料行存放區都支援彙總下推。  
  
-   述詞下推會加快比較 [v]archar 或 n[v]archar 字串類型的查詢。 這適用於一般比較運算子和包括運算子，如使用點陣圖篩選器的 LIKE。 這對 SQL Server 支援的所有定序都有效。  
  
### <a name="performance-for-database-compatibility-level-130"></a>資料庫相容性等級 130 的效能  
  
-   新的批次模式執行支援使用任一這些作業的查詢︰  
    -   SORT  
    -   使用多個不同的函式進行彙總。 部分範例：`COUNT/COUNT`、`AVG/SUM`、`CHECKSUM_AGG`、`STDEV/STDEVP`。  
    -   視窗彙總函式：`COUNT`、`COUNT_BIG`、`SUM`、`AVG`、`MIN`、`MAX` 和 `CLR`。  
    -   視窗使用者定義彙總：`CHECKSUM_AGG`、`STDEV`、`STDEVP`、`VAR`、`VARP` 和 `GROUPING`。  
    -   視窗彙總分析函式：`LAG`、`LEAD`、`FIRST_VALUE`、`LAST_VALUE`、`PERCENTILE_CONT`、`PERCENTILE_DISC`、`CUME_DIST` 和 `PERCENT_RANK`。  
-   在 `MAXDOP 1` 下執行，或以批次模式執行序列查詢計畫的單一執行緒查詢。 以前只有多執行緒查詢可以批次執行的方式來執行。  
-   在存取資料列存放區或資料行存放區索引中的資料時，記憶體最佳化資料表查詢在 SQL InterOp 模式中可以有平行計畫。  
  
### <a name="supportability"></a>可支援性  
這些系統檢視表對資料行存放區而言是新的︰  
||| 
|-|-|
|[sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)|[sys.dm_column_store_object_pool &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)|  
|[sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)|[sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)|  
|[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)|[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)|  
|[sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)||  
  
這些記憶體中的 OLTP 型 DMV 包含資料行存放區的更新︰  
||| 
|-|-|
|[sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql.md)|[sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)|  
|[sys.dm_db_xtp_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-memory-consumers-transact-sql.md)|[sys.dm_db_xtp_nonclustered_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-nonclustered-index-stats-transact-sql.md)|  
|[sys.dm_db_xtp_object_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-object-stats-transact-sql.md)|[sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql.md)|  
  
### <a name="limitations"></a>限制  
  
-   B-tree 索引在叢集資料行存放區索引上定義時，MERGE 就會停用。  
-   至於記憶體中資料表，資料行存放區索引必須包含所有的資料行，而資料行存放區索引不能有篩選的條件。  
-   至於記憶體中資料表，針對資料行存放區索引的查詢只能在 InterOP 模式中執行，不是在記憶體中原生模式中執行。 支援平行執行。  
  
## [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 引進叢集資料行存放區索引，作為主要的儲存體格式。 這允許一般的負載以及更新、刪除和插入作業。  
  
-   資料表可以使用叢集資料行存放區索引作為主要的資料表儲存體。 資料表上不允許其他索引，但是叢集資料行存放區索引是可以更新的，所以您可以執行一般的載入並對個別資料列進行變更。  
-   非叢集資料行存放區索引繼續保有在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中的相同功能，但現在可在批次模式中執行其他運算子。 而除非重建和使用資料分割切換，否則仍然不能更新。 只有磁碟資料表支援非叢集資料行存放區索引，記憶體中資料表不支援。  
-   叢集與非叢集資料行存放區索引都有封存壓縮選項，可進一步壓縮資料。 封存選項有利於減少記憶體中和磁碟上的資料大小，但是確實會降低查詢效能。 它非常適合不常存取的資料。  
-   叢集資料行存放區索引和非叢集資料行存放區索引的作用十分相似，它們使用相同的單欄式儲存體格式、相同的查詢處理引擎，和相同的動態管理檢視集合。 差別在於主要和次要的索引類型，而且非叢集資料行存放區索引是唯讀的。  
-   這些運算子可在批次模式下執行多執行緒查詢︰scan、filter、project、join、group by 和 union all。  
  
## [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 引進非叢集資料行存放區索引，作為資料列存放區資料表的另一個索引類型和批次處理資料行存放區資料的查詢。  
  
-   資料列存放區資料表可以有一個非叢集資料行存放區索引。  
-   資料行存放區索引是唯讀的。 建立資料行存放區索引之後，您無法執行 `INSERT`、`DELETE` 和 `UPDATE` 作業來更新資料表；若要執行這些作業，您必須卸除索引，並更新資料表，然後重建資料行存放區索引。 您可以切換資料分割，在資料表中載入其他資料。 資料分割切換的優點是您可以載入資料，卻不用卸除和重建資料行存放區索引。  
-   資料行存放區索引一定需要額外的儲存體，通常是資料列存放區多加 10%，因為它會儲存一份資料複本。  
-   批次處理序提供 2 倍或更高的查詢效能，但僅供平行查詢執行使用。  
  
## <a name="see-also"></a>另請參閱  
 [資料行存放區索引設計指導](../../relational-databases/indexes/columnstore-indexes-design-guidance.md)   
 [資料行存放區索引資料載入指導](../../relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)   
 [資料行存放區索引效能](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [開始使用資料行存放區進行即時作業分析](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [資料倉儲的資料行存放區索引](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)   
 [資料行存放區索引重組](../../relational-databases/indexes/columnstore-indexes-defragmentation.md) 
  
  
  
