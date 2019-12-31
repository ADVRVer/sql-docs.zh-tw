---
title: sys.databases dm_db_column_store_row_group_physical_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_column_store_row_group_physical_stats_TSQL
- sys.dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_column_store_row_group_physical_stats
- sys.dm_db_column_store_row_group_physical_stats dynamic management view
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c676f82f3bf424638fcb6a2705853a5ff482921c
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75254466"
---
# <a name="sysdm_db_column_store_row_group_physical_stats-transact-sql"></a>sys.databases dm_db_column_store_row_group_physical_stats （Transact-sql）

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

提供目前資料庫中所有資料行存放區索引的目前資料列群組層級資訊。  

這會延伸目錄檢視[sys.databases column_store_row_groups &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)。  

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|基礎資料表的識別碼。|  
|**index_id**|**int**|*Object_id*資料表上此資料行存放區索引的識別碼。|  
|**partition_number**|**int**|保存*row_group_id*之資料表分割區的識別碼。 您可以使用 partition_number 將此 DMV 聯結至 sys.partitions。|  
|**row_group_id**|**int**|此資料列群組的識別碼。 對於資料分割資料表而言，值在資料分割內是唯一的。<br /><br /> -1 表示記憶體中的尾。|  
|**delta_store_hobt_id**|**bigint**|差異存放區中資料列群組的 hobt_id。<br /><br /> 如果資料列群組不在差異存放區中，則為 Null。<br /><br /> 記憶體中資料表的結尾會是 Null。|  
|**狀態**|**Tinyint**|*State_description*相關聯的識別碼。<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED<br /><br /> 4 = 標記<br /><br /> 「壓縮」是適用于記憶體內部資料表的唯一狀態。|  
|**state_desc**|**Nvarchar （60）**|資料列群組狀態的描述：<br /><br /> 不可見-正在建立的資料列群組。 例如： <br />資料行存放區中的資料列群組在壓縮時不可見。 完成壓縮時，中繼資料參數會將資料行存放區資料列群組的狀態從不可見變更為已壓縮，並將差異存放區資料列群組的狀態從 CLOSED 變更為標記。<br /><br /> OPEN-接受新資料列的差異存放區資料列群組。 開啟的資料列群組仍採用資料列存放區格式，且尚未壓縮為資料行存放區格式。<br /><br /> CLOSED-差異存放區中的資料列群組，其中包含最大資料列數目，而且正在等候元組移動程式將它壓縮到資料行存放區。<br /><br /> 已壓縮-以資料行存放區壓縮壓縮並儲存在資料行存放區的資料列群組。<br /><br /> 標記-先前在差異存放區中且不再使用的資料列群組。|  
|**total_rows**|**bigint**|實際儲存在資料列群組中的資料列數目。 適用于壓縮的資料列群組。 包含標示為已刪除的資料列。|  
|**deleted_rows**|**bigint**|實際儲存在標示為要刪除之已壓縮資料列群組的資料列數目。<br /><br /> 0 代表位於差異存放區中的資料列群組。|  
|**size_in_bytes**|**bigint**|此資料列群組中所有頁面的組合大小（以位元組為單位）。 此大小不包含儲存中繼資料或共用字典所需的大小。|  
|**trim_reason**|**Tinyint**|觸發壓縮資料列群組小於資料列數目上限的原因。<br /><br /> 0-UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1-NO_TRIM<br /><br /> 2-BULKLOAD<br /><br /> 3-REORG<br /><br /> 4-DICTIONARY_SIZE<br /><br /> 5-MEMORY_LIMITATION<br /><br /> 6-RESIDUAL_ROW_GROUP<br /><br /> 7-STATS_MISMATCH<br /><br /> 8-溢出|  
|**trim_reason_desc**|**Nvarchar （60）**|*Trim_reason*的描述。<br /><br /> 0-UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION：從舊版升級時發生[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。<br /><br /> 1-NO_TRIM：未修剪資料列群組。 已壓縮資料列群組，最大值為1048476個數據列。  如果在差異資料列群組關閉後刪除資料列子集，資料列數目可能會較少<br /><br /> 2-BULKLOAD：大量載入批次大小限制資料列數目。<br /><br /> 3-REORG：強制壓縮作為 REORG 命令的一部分。<br /><br /> 4-DICTIONARY_SIZE：字典大小成長太大，無法一起壓縮所有的資料列。<br /><br /> 5-MEMORY_LIMITATION：沒有足夠的可用記憶體可將所有資料列壓縮在一起。<br /><br /> 6-RESIDUAL_ROW_GROUP：在索引建立作業期間，以資料列 < 1000000 的最後一個資料列群組的一部分關閉<br /><br /> STATS_MISMATCH：僅適用于記憶體內部資料表上的資料行存放區。 如果統計資料未正確指出 >= 結尾的1000000個限定資料列，但我們發現較少，則壓縮的資料列群組會有 < 1000000 個數據列<br /><br /> 溢出：僅適用于記憶體內部資料表上的資料行存放區。 如果 tail 具有 > 1000000 限定的資料列，則最後一個批次的資料列會壓縮（如果計數介於100k 到1000000之間）|  
|**transition_to_compressed_state**|tinyint|顯示如何將此資料列群組從差異存放區移至資料行存放區中的壓縮狀態。<br /><br /> 1-NOT_APPLICABLE<br /><br /> 2-INDEX_BUILD<br /><br /> 3-TUPLE_MOVER<br /><br /> 4-REORG_NORMAL<br /><br /> 5-REORG_FORCED<br /><br /> 6-BULKLOAD<br /><br /> 7-合併|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE-此作業不會套用至差異存放區。 或者，在升級至[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]之前，資料列群組已經過壓縮，在此情況下不會保留歷程記錄。<br /><br /> INDEX_BUILD-索引建立或索引重建已壓縮的資料列群組。<br /><br /> TUPLE_MOVER-在背景中執行的元組移動器會壓縮資料列群組。 在資料列群組變更狀態從開啟到已關閉之後，元組移動器就會發生。<br /><br /> REORG_NORMAL-重新組織作業，ALTER INDEX .。。REORG，將已關閉的資料列群組從差異存放區移至資料行存放區。 這是在元組-移動器有時間移動資料列群組之前發生。<br /><br /> REORG_FORCED-此資料列群組已在差異存放區中開啟，並已強制進入資料行存放區，因為它擁有完整的資料列數目。<br /><br /> BULKLOAD-大量載入作業會直接壓縮資料列群組，而不使用差異存放區。<br /><br /> MERGE-合併作業會將一或多個資料列群組合並至此資料列群組，然後執行資料行存放區壓縮。|  
|**has_vertipaq_optimization**|bit|VertiPaq 優化藉由重新排列資料列群組中的資料列順序來改善資料行存放區壓縮，以達到更高的壓縮。 這項優化會在大部分情況下自動進行。 在兩種情況下，不會使用 VertiPaq 優化：<br/>  a. 當差異資料列群組移至資料行存放區，且資料行存放區索引上有一或多個非叢集索引時-在此情況下，會略過 VertiPaq 優化，將對應索引的變更降至最低。<br/> b. 適用于記憶體優化資料表上的資料行存放區索引。 <br /><br /> 0 = 否<br /><br /> 1 = 是|  
|**代數**|bigint|與此資料列群組相關聯的資料列群組產生。|  
|**created_time**|datetime2|建立此資料列群組的時間。<br /><br /> Null-適用于記憶體內部資料表上的資料行存放區索引。|  
|**closed_time**|datetime2|此資料列群組關閉時的時鐘時間。<br /><br /> Null-適用于記憶體內部資料表上的資料行存放區索引。|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="results"></a>結果  
 針對目前資料庫中的每個資料列群組傳回一個資料列。  
  
## <a name="permissions"></a>權限  
需要`CONTROL`資料表的許可權和`VIEW DATABASE STATE`資料庫的許可權。  
  
## <a name="examples"></a>範例  
  
### <a name="a-calculate-fragmentation-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. 計算片段，以決定何時要重新組織或重建資料行存放區索引。  
 針對資料行存放區索引，已刪除資料列的百分比對於資料列群組中的片段而言是很好的量值。 當片段為20% 或以上時，請移除已刪除的資料列。 如需更多範例，請參閱[重新組織和重建索引](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)。  
  
 這個範例會聯結 sys.databases 與其他系統資料表的**dm_db_column_store_row_group_physical_stats** ，然後將`Fragmentation`資料行計算為目前資料庫中每個資料列群組的效率估計。 若要尋找單一資料表的資訊，請移除**WHERE**子句前面的批註連字號，並提供資料表名稱。  
  
```sql  
SELECT i.object_id,   
    object_name(i.object_id) AS TableName,   
    i.name AS IndexName,   
    i.index_id,   
    i.type_desc,   
    CSRowGroups.*,  
    100*(ISNULL(deleted_rows,0))/NULLIF(total_rows,0) AS 'Fragmentation'
FROM sys.indexes AS i  
JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id AND i.index_id = CSRowGroups.index_id   
-- WHERE object_name(i.object_id) = 'table_name'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的物件目錄檢視](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [&#40;Transact-sql&#41;的目錄檢視](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)      
 [資料行存放區索引架構](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)         
 [查詢 SQL Server 系統目錄常見問題](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [all_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [computed_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
 [column_store_dictionaries &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [column_store_segments &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
