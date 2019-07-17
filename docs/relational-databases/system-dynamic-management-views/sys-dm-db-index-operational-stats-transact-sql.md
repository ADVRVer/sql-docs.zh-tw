---
title: sys.dm_db_index_operational_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_index_operational_stats
- sys.dm_db_index_operational_stats_TSQL
- sys.dm_db_index_operational_stats
- dm_db_index_operational_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_operational_stats dynamic management function
ms.assetid: 13adf2e5-2150-40a6-b346-e74a33ce29c6
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b8222454d5e016733abef3c086e38add777cd304
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004892"
---
# <a name="sysdmdbindexoperationalstats-transact-sql"></a>sys.dm_db_index_operational_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回目前的較低層級 I/O、 鎖定、 閂鎖和存取方法活動，每個資料分割資料表或索引的資料庫中。    
    
 記憶體最佳化的索引不會出現在這個 DMV 中。    
    
> [!NOTE]    
>  **sys.dm_db_index_operational_stats**不會傳回記憶體最佳化索引的相關資訊。 記憶體最佳化索引用法的相關資訊，請參閱[sys.dm_db_xtp_index_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)。    
        
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>語法    
    
```    
    
sys.dm_db_index_operational_stats (    
    { database_id | NULL | 0 | DEFAULT }    
  , { object_id | NULL | 0 | DEFAULT }    
  , { index_id | 0 | NULL | -1 | DEFAULT }    
  , { partition_number | NULL | 0 | DEFAULT }    
)    
```    
    
## <a name="arguments"></a>引數    
 *database_id* |NULL |0 |預設值    
 資料庫的識別碼。 *database_id*已**smallint**。 有效的輸入為資料庫的識別碼、NULL、0 或 DEFAULT。 預設值是 0。 NULL、0 和 DEFAULT 是這個內容中的對等值。    
    
 請指定 NULL 來傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中之所有資料庫的資訊。 如果您指定 NULL *database_id*，您也必須指定，則為 NULL *object_id*， *index_id*，以及*partition_number*。    
    
 內建函式[DB_ID](../../t-sql/functions/db-id-transact-sql.md)可以指定。    
    
 *object_id* | NULL | 0 | DEFAULT    
 索引所在之資料表或檢視表的物件識別碼。 *object_id* 是 **int**。    
    
 有效的輸入為資料表和檢視表的識別碼、NULL、0 或 DEFAULT。 預設值是 0。 NULL、0 和 DEFAULT 是這個內容中的對等值。    
    
 請指定 NULL 來傳回指定之資料庫中所有資料表和檢視表的快取資訊。 如果您指定 NULL *object_id*，您也必須指定，則為 NULL *index_id*並*partition_number*。    
    
 *index_id* | 0 | NULL | -1 | DEFAULT    
 索引的識別碼。 *index_id*已**int**。有效輸入如下的索引，0 的 ID 編號，如果*object_id*是堆積，NULL，-1 或預設值。 預設值為 -1；NULL、-1 和 DEFAULT 是這個內容中的對等值。    
    
 請指定 NULL 來傳回基底資料表或檢視表所有索引的快取資訊。 如果您指定 NULL *index_id*，您也必須指定，則為 NULL *partition_number*。    
    
 *partition_number* |NULL |0 |預設值    
 物件的分割區編號。 *partition_number*已**int**。有效輸入如下*partion_number*索引或堆積中，NULL，0 或 DEFAULT。 預設值是 0。 NULL、0 和 DEFAULT 是這個內容中的對等值。    
    
 請指定 NULL 來傳回索引或堆積之所有分割區的快取資訊。    
    
 *partition_number*是以 1 為基礎。 非資料分割索引或堆積*partition_number*設為 1。    
    
## <a name="table-returned"></a>傳回的資料表    
    
|資料行名稱|資料類型|描述|    
|-----------------|---------------|-----------------|    
|**database_id**|**smallint**|資料庫識別碼。|    
|**object_id**|**int**|資料表或檢視表的識別碼。|    
|**index_id**|**int**|索引或堆積的識別碼。<br /><br /> 0 = 堆積| 
|**partition_number**|**int**|在索引或堆積內，以 1 為基底的資料分割編號。| 
|**hobt_id**|**bigint**|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 透過 [目前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658))、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /><br /> 之資料堆積或 B 型樹狀目錄會追蹤資料行存放區索引的內部資料的資料列的識別碼。<br /><br /> 空值-這不是內部的資料行存放區資料列集。<br /><br /> 如需詳細資訊，請參閱 < [sys.internal_partitions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)|       
|**leaf_insert_count**|**bigint**|分葉層級插入的累計計數。|    
|**leaf_delete_count**|**bigint**|分葉層級刪除的累計計數。 已刪除的記錄未標示為準刪除項目第一次只會漸增 leaf_delete_count。 已刪除的記錄，建立映像第一次，如**leaf_ghost_count**會改為遞增。|    
|**leaf_update_count**|**bigint**|分葉層級更新的累計計數。|    
|**leaf_ghost_count**|**bigint**|標示為已經刪除、但尚未移除之分葉層級資料列的累加計數。 這個計數不包含會立即刪除，而不被標示為準刪除記錄。 這些資料列會在設定間隔時，被清除執行緒移除。 由於還有一個未完成的快照集隔離交易，因此這個值不包含保留的資料列。|    
|**nonleaf_insert_count**|**bigint**|分葉層級上面的插入累計計數。<br /><br /> 0 = 堆積或資料行存放區|    
|**nonleaf_delete_count**|**bigint**|分葉層級上面的刪除累計計數。<br /><br /> 0 = 堆積或資料行存放區|    
|**nonleaf_update_count**|**bigint**|分葉層級上面的更新累計計數。<br /><br /> 0 = 堆積或資料行存放區|    
|**leaf_allocation_count**|**bigint**|索引或堆積內分葉層級頁面配置的累計計數。<br /><br /> 如果是索引，則頁面配置為對應於頁面分割。|    
|**nonleaf_allocation_count**|**bigint**|分葉層級上面，由頁面分割所導致的頁面配置累計計數。<br /><br /> 0 = 堆積或資料行存放區|    
|**leaf_page_merge_count**|**bigint**|分葉層級的頁面合併累計計數。 永遠是 0，表示資料行存放區索引。|    
|**nonleaf_page_merge_count**|**bigint**|分葉層級上面的頁面合併累計計數。<br /><br /> 0 = 堆積或資料行存放區|    
|**range_scan_count**|**bigint**|在索引或堆積啟動的範圍和資料表掃描累計計數。|    
|**singleton_lookup_count**|**bigint**|從索引或堆積擷取單資料列的累計計數。|    
|**forwarded_fetch_count**|**bigint**|透過轉送記錄提取的資料列計數。<br /><br /> 0 = 索引|    
|**lob_fetch_in_pages**|**bigint**|從 LOB_DATA 配置單位擷取的大型物件 (LOB) 頁面累加計數。 這些頁面包含儲存在類型的資料行的資料**文字**， **ntext**，**映像**， **varchar （max)** ， **nvarchar (max)** ， **varbinary （max)** ，以及**xml**。 如需詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)。|    
|**lob_fetch_in_bytes**|**bigint**|所擷取的 LOB 資料位元組累計。|    
|**lob_orphan_create_count**|**bigint**|針對大量作業所建立的孤立 LOB 值累計。<br /><br /> 0 = 非叢集索引|    
|**lob_orphan_insert_count**|**bigint**|在大量作業時插入的孤立 LOB 值累計計數。<br /><br /> 0 = 非叢集索引|    
|**row_overflow_fetch_in_pages**|**bigint**|從 ROW_OVERFLOW_DATA 配置單位擷取的資料列溢位資料頁累計計數。<br /><br /> 這些頁面包含類型的資料行中儲存的資料**varchar （n)** ， **nvarchar （n)** ， **varbinary**，以及**sql_variant**已經從資料列發送。|    
|**row_overflow_fetch_in_bytes**|**bigint**|所擷取的資料列溢位資料位元組累計計數。|    
|**column_value_push_off_row_count**|**bigint**|為了讓插入或更新資料列容納在一頁中，而被排除為非資料列的 LOB 資料和資料列溢位資料的資料行值累計計數。|    
|**column_value_pull_in_row_count**|**bigint**|被納入成為同資料列的 LOB 資料和資料列溢位資料的資料行值累加計數。 這項作業是在更新作業釋出記錄空間，讓您有機會將 LOB_DATA 或 ROW_OVERFLOW_DATA 配置單位的一個或多個非資料列值納入 IN_ROW_DATA 配置單位時發生。|    
|**row_lock_count**|**bigint**|所要求的資料列鎖定累計數目。|    
|**row_lock_wait_count**|**bigint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 在資料列鎖定等候的累加次數。|    
|**row_lock_wait_in_ms**|**bigint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 在資料列鎖定等候的總毫秒數。|    
|**page_lock_count**|**bigint**|所要求的頁面鎖定累計數目。|    
|**page_lock_wait_count**|**bigint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 在頁面鎖定等候的累加次數。|    
|**page_lock_wait_in_ms**|**bigint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 在頁面鎖定等候的總毫秒數。|    
|**index_lock_promotion_attempt_count**|**bigint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 試圖提升鎖定的累加次數。|    
|**index_lock_promotion_count**|**bigint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 已經提升鎖定的累加次數。|    
|**page_latch_wait_count**|**bigint**|由於閂鎖競爭之故，而使 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 等候的累加次數。|    
|**page_latch_wait_in_ms**|**bigint**|由於閂鎖競爭之故，而使 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 等候的累加毫秒數。|    
|**page_io_latch_wait_count**|**bigint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 在 I/O 頁面閂鎖等候的累加次數。|    
|**page_io_latch_wait_in_ms**|**bigint**|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 在頁面 I/O 閂鎖等候的累加毫秒數。|    
|**tree_page_latch_wait_count**|**bigint**|子集**page_latch_wait_count**只包含上層 B 型樹狀目錄頁面。 永遠是 0，表示堆積或資料行存放區索引。|    
|**tree_page_latch_wait_in_ms**|**bigint**|子集**page_latch_wait_in_ms**只包含上層 B 型樹狀目錄頁面。 永遠是 0，表示堆積或資料行存放區索引。|    
|**tree_page_io_latch_wait_count**|**bigint**|子集**page_io_latch_wait_count**只包含上層 B 型樹狀目錄頁面。 永遠是 0，表示堆積或資料行存放區索引。|    
|**tree_page_io_latch_wait_in_ms**|**bigint**|子集**page_io_latch_wait_in_ms**只包含上層 B 型樹狀目錄頁面。 永遠是 0，表示堆積或資料行存放區索引。|    
|**page_compression_attempt_count**|**bigint**|針對資料表、索引或索引檢視表之特定分割區的 PAGE 層級壓縮所評估的頁數。 包括由於無法大量節省頁面而未壓縮的頁面。 永遠是 0，表示資料行存放區索引。|    
|**page_compression_success_count**|**bigint**|使用資料表、索引或索引檢視表之特定分割區的頁面壓縮所壓縮的資料頁數。 永遠是 0，表示資料行存放區索引。|    
    
## <a name="remarks"></a>備註    
 這個動態管理物件不接受來自 CROSS APPLY 和 OUTER APPLY 中相互關聯的參數。    
    
 您可以使用**sys.dm_db_index_operational_stats**追蹤的使用者必須等待讀取或寫入資料表、 索引或資料分割，和識別的資料表或索引時遇到重大 I/O 活動或經常存取的時間長度點。    
    
 請利用下列資料行來識別競爭區。    
    
 **若要分析資料表或索引的分割區的共用存取模式**，使用這些資料行：    
    
-   **leaf_insert_count**    
    
-   **leaf_delete_count**    
    
-   **leaf_update_count**    
    
-   **leaf_ghost_count**    
    
-   **range_scan_count**    
    
-   **singleton_lookup_count**    
    
 若要識別閂鎖和鎖定競爭，請使用這些資料行：    
    
-   **page_latch_wait_count**和**page_latch_wait_in_ms**    
    
     這些資料行會指出索引或堆積上是否有閂鎖競爭的情形，以及競爭的嚴重程度。    
    
-   **row_lock_count**和**page_lock_count**    
    
     這些資料行會指出 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 試圖取得資料列和頁面鎖定的次數。    
    
-   **row_lock_wait_in_ms**和**page_lock_wait_in_ms**    
    
     這些資料行會指出索引或堆積上是否有鎖定競爭的情形，以及競爭的嚴重程度。    
    
 **若要分析的索引或堆積的分割區上的實體 I/o 統計資料**    
    
-   **page_io_latch_wait_count**和**page_io_latch_wait_in_ms**    
    
     這些資料行會指出是否有發出實體 I/O，將索引或堆積頁引進記憶體中，以及發出幾個 I/O。    
    
## <a name="column-remarks"></a>資料行備註    
 中的值**lob_orphan_create_count**並**lob_orphan_insert_count**一律應該相等。    
    
 資料行中的值**lob_fetch_in_pages**並**lob_fetch_in_bytes**可以是大於零的非叢集索引包含一或多個 LOB 資料行作為內含資料行。 如需詳細資訊，請參閱 [建立內含資料行的索引](../../relational-databases/indexes/create-indexes-with-included-columns.md)。 同樣地，資料行中的值才**row_overflow_fetch_in_pages**並**row_overflow_fetch_in_bytes**可以是大於 0 的非叢集索引，如果索引包含可以推入的資料行非資料列。    
    
## <a name="how-the-counters-in-the-metadata-cache-are-reset"></a>如何重設中繼資料快取中的計數器    
 所傳回的資料**sys.dm_db_index_operational_stats**存在於只要代表堆積或索引的中繼資料快取物件可用。 這項資料既不能保存，以交易來說也是不一致的。 這表示您不能使用這些計數器來判定索引是否已經使用，或者索引上次是何時使用。 如需資訊，請參閱 < [sys.dm_db_index_usage_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)。    
    
 每當堆積或索引的中繼資料被引進中繼資料快取時，每個資料行的值都會設為零，而且統計資料也會累計，直到快取物件從中繼資料快取移除為止。 因此，使用中堆積或索引的中繼資料可能會一直存放在快取中，而且累加計數也會反映自從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上次啟動以來的活動。 比較不使用的堆積或索引中繼資料，則會在使用時移入和移出快取。 因此，它不見得會有可用的值。 卸除索引會使對應的統計資料從記憶體移除，不會再由該函數報告。 對索引進行的其他 DDL 作業，可能會使統計資料值重設為零。    
    
## <a name="using-system-functions-to-specify-parameter-values"></a>使用系統函數指定參數值    
 您可以使用[!INCLUDE[tsql](../../includes/tsql-md.md)]函式[DB_ID](../../t-sql/functions/db-id-transact-sql.md)並[OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)指定值*database_id*並*object_id*參數。 不過，傳遞對這些函數無效的值可能會造成意料之外的結果。 使用 DB_ID 或 OBJECT_ID 時，請務必確定傳回的是有效的識別碼。 如需詳細資訊，請參閱中的 < 備註 > 一節[sys.dm_db_index_physical_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)。    
    
## <a name="permissions"></a>Permissions    
 需要下列權限：    
    
-   對資料庫中的指定物件具備 CONTROL 權限    
    
-   傳回指定的資料庫中的所有物件的相關資訊，利用物件萬用字元 @ 的 VIEW DATABASE STATE 權限*object_id* = NULL    
    
-   若要利用資料庫萬用字元 @ 傳回所有資料庫的相關資訊的 VIEW SERVER STATE 權限*database_id* = NULL    
    
 授與 VIEW DATABASE STATE 可以傳回資料庫中的所有物件，不論特定物件是否拒絕任何 CONTROL 權限。    
    
 拒絕 VIEW DATABASE STATE 會造成不允許傳回資料庫中的所有物件 (不論是否授與特定物件任何 CONTROL 權限)。 也，當資料庫萬用字元 @*database_id*= 指定 NULL，則會省略資料庫。    
    
 如需詳細資訊，請參閱 <<c0> [ 動態管理檢視和函式&#40;TRANSACT-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)。</c0>    
    
## <a name="examples"></a>範例    
    
### <a name="a-returning-information-for-a-specified-table"></a>A. 傳回指定資料表的資訊    
 下列範例會傳回 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫中 `Person.Address` 資料表所有索引和分割區的相關資訊。 若要執行這項查詢，至少必須對 `Person.Address` 資料表具備 CONTROL 權限。    
    
> [!IMPORTANT]    
>  當您使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函數 DB_ID 和 OBJECT_ID 傳回參數值時，請務必確定您所傳回的是有效的識別碼。 如果找不到資料庫或物件名稱 (例如，因為不存在或是拼錯了)，這兩個函數都會傳回 NULL。 **sys.dm_db_index_operational_stats** 函數會將 NULL 解譯為指定所有資料庫或物件的萬用字元值。 由於這不見得是刻意安排的作業，因此本節所舉的範例，只會示範決定資料庫和物件識別碼的安全方法。    
    
```    
DECLARE @db_id int;    
DECLARE @object_id int;    
SET @db_id = DB_ID(N'AdventureWorks2012');    
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');    
IF @db_id IS NULL     
  BEGIN;    
    PRINT N'Invalid database';    
  END;    
ELSE IF @object_id IS NULL    
  BEGIN;    
    PRINT N'Invalid object';    
  END;    
ELSE    
  BEGIN;    
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);    
  END;    
GO    
    
```    
    
### <a name="b-returning-information-for-all-tables-and-indexes"></a>B. 傳回所有資料表和索引的資訊    
 下列範例會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中所有資料表和索引的相關資訊。 執行這項查詢需要 VIEW SERVER STATE 權限。    
    
```    
SELECT * FROM sys.dm_db_index_operational_stats( NULL, NULL, NULL, NULL);    
GO    
    
```    
    
## <a name="see-also"></a>另請參閱    
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)     
 [索引相關的動態管理檢視和函式 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)     
 [效能的監視與微調](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)     
 [sys.dm_db_index_usage_stats &#40;-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)     
 [sys.dm_os_latch_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)     
 [sys.dm_db_partition_stats &#40;-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)     
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)     
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)    
    
  

