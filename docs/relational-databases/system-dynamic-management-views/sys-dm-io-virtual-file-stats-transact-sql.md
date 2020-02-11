---
title: sys.databases dm_io_virtual_file_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_io_virtual_file_stats
- sys.dm_io_virtual_file_stats_TSQL
- sys.dm_io_virtual_file_stats
- dm_io_virtual_file_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_virtual_file_stats dynamic management function
ms.assetid: fa3e321f-6fe5-45ff-b397-02a0dd3d6b7d
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0ad2d38c031f97e46ef36f33f5e7a0fc82bcb5e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "74412835"
---
# <a name="sysdm_io_virtual_file_stats-transact-sql"></a>sys.dm_io_virtual_file_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  傳回資料和記錄檔的 I/O 統計資料。 這個動態管理檢視會取代[fn_virtualfilestats](../../relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql.md)函數。  
  
> [!NOTE]  
>  若要從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]呼叫此，請使用**dm_pdw_nodes_io_virtual_file_stats**的名稱。 

## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server and Azure SQL Database

sys.dm_io_virtual_file_stats (   
    { database_id | NULL },  
    { file_id | NULL }  
)  
```  

```  
-- Syntax for Azure SQL Data Warehouse

sys.dm_pdw_nodes_io_virtual_file_stats
```
  
## <a name="arguments"></a>引數  


 *database_id* |Null

 **適用於：** SQL Server (從 2008 開始)、Azure SQL Database

 資料庫的識別碼。 *database_id*是 int，沒有預設值。 資料庫的識別碼或 NULL 都是有效的輸入。 如果指定 NULL，則會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中所有的資料庫。  
  
 可以指定內建函數 [DB_ID](../../t-sql/functions/db-id-transact-sql.md)。  
  
*file_id* |Null

**適用於：** SQL Server (從 2008 開始)、Azure SQL Database
 
檔案識別碼。 *file_id*是 int，沒有預設值。 有效輸入是檔案的識別碼或 NULL。 如果指定 NULL，則會傳回資料庫中所有的檔案。  
  
 您可以指定內建函數[FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) ，並參考目前資料庫中的檔案。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|資料庫名稱。</br></br>針對 SQL 資料倉儲，這是儲存在節點上的資料庫名稱，由 pdw_node_id 所識別。 每個節點都有一個具有13個檔案的 tempdb 資料庫。 每個節點在每個散發中也有一個資料庫，而每個散發資料庫都有5個檔案。 例如，如果每個節點都包含4個散發，則結果會顯示每個 pdw_node_id 20 個散發資料庫檔案。 
|**database_id**|**smallint**|資料庫的識別碼。|  
|**file_id**|**smallint**|檔案的識別碼。|  
|**sample_ms**|**Bigint**|自電腦啟動之後的毫秒數。 這個資料行可用來比較這個函數的不同輸出。</br></br>資料類型是透過的**int** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|**num_of_reads**|**Bigint**|對檔案發出的讀取數。|  
|**num_of_bytes_read**|**Bigint**|這個檔案讀取的總位元組數。|  
|**io_stall_read_ms**|**Bigint**|使用者等候在檔案發出讀取的總時間 (以毫秒為單位)。|  
|**num_of_writes**|**Bigint**|這個檔案所進行的寫入數。|  
|**num_of_bytes_written**|**Bigint**|寫入檔案的總位元組數。|  
|**io_stall_write_ms**|**Bigint**|使用者等候檔案完成寫入的總時間 (以毫秒為單位)。|  
|**io_stall**|**Bigint**|使用者等候檔案完成 I/O 的總時間 (以毫秒為單位)。|  
|**size_on_disk_bytes**|**Bigint**|該檔案在磁碟上所用的位元組數。 如果是疏鬆檔案，這個數字就是資料庫快照集在磁碟上所用的實際位元組數。|  
|**file_handle**|**varbinary**|這個檔案的 Windows 檔案控制代碼。|  
|**io_stall_queued_read_ms**|**Bigint**|不**適用于：**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]至。 [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)]<br /><br /> IO 資源管理針對讀取導入的總 IO 延遲。 不可為 Null。 如需詳細資訊，請參閱[dm_resource_governor_resource_pools &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)。|  
|**io_stall_queued_write_ms**|**Bigint**|不**適用于：**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]至。 [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)]<br /><br />  IO 資源管理針對寫入導入的總 IO 延遲。 不可為 Null。|
|**pdw_node_id**|**int**|**適用物件：**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]</br></br>散發的節點識別碼。
 
## <a name="remarks"></a>備註
每當啟動 SQL Server （MSSQLSERVER）服務時，計數器就會初始化為空的。
  
## <a name="permissions"></a>權限  
 需要 VIEW SERVER STATE 權限。 如需詳細資訊，請參閱[動態管理檢視和函數 &#40;transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)。  
  
## <a name="examples"></a>範例  

### <a name="a-return-statistics-for-a-log-file"></a>A. 傳回記錄檔的統計資料

**適用物件：** SQL Server （從2008開始），Azure SQL Database

 下列範例會傳回 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫中記錄檔的統計資料。  
  
```sql  
SELECT * FROM sys.dm_io_virtual_file_stats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="b-return-statistics-for-file-in-tempdb"></a>B. 傳回 tempdb 中檔案的統計資料

**適用物件：** Azure SQL 資料倉儲

```sql
SELECT * FROM sys.dm_pdw_nodes_io_virtual_file_stats 
WHERE database_name = 'tempdb' AND file_id = 2;

```

## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [I/o 相關的動態管理檢視和函數 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)   
 [database_files &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

