---
title: sys.dm_io_virtual_file_stats (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fc6511c6a0999dfd366c87fcfa18630614215efa
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52407295"
---
# <a name="sysdmiovirtualfilestats-transact-sql"></a>sys.dm_io_virtual_file_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  傳回資料和記錄檔的 I/O 統計資料。 這個動態管理檢視會取代[fn_virtualfilestats](../../relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql.md)函式。  
  
> [!NOTE]  
>  若要呼叫這個屬性從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]，使用名稱**sys.dm_pdw_nodes_io_virtual_file_stats**。 

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


 *database_id* |NULL

 **適用於：** SQL Server （從 2008年開始）、 Azure SQL Database

 資料庫的識別碼。 *database_id*是 int，沒有預設值。 資料庫的識別碼或 NULL 都是有效的輸入。 如果指定 NULL，則會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中所有的資料庫。  
  
 內建函式[DB_ID](../../t-sql/functions/db-id-transact-sql.md)可以指定。  
  
*file_id* |NULL

**適用於：** SQL Server （從 2008年開始）、 Azure SQL Database
 
檔案識別碼。 *file_id*是 int，沒有預設值。 有效輸入是檔案的識別碼或 NULL。 如果指定 NULL，則會傳回資料庫中所有的檔案。  
  
 內建函式[FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md)指定，且參考目前資料庫中的檔案。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|資料庫名稱。</br></br>針對 SQL 資料倉儲，這是儲存在由 pdw_node_id 的節點上的資料庫名稱。 每個節點都有 13 個檔案的一個 tempdb 資料庫。 每個節點也有一個資料庫，每個散發，而且每個散發資料庫中有 5 個檔案。 比方說，如果每個節點包含 4 個散發套件，結果會顯示 pdw_node_id 每 20 個散發資料庫檔案。 
|**database_id**|**smallint**|資料庫的識別碼。|  
|**file_id**|**smallint**|檔案的識別碼。|  
|**sample_ms**|**bigint**|自電腦啟動之後的毫秒數。 這個資料行可用來比較這個函數的不同輸出。</br></br>資料類型是**int**如[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]透過 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|**num_of_reads**|**bigint**|對檔案發出的讀取數。|  
|**num_of_bytes_read**|**bigint**|這個檔案讀取的總位元組數。|  
|**io_stall_read_ms**|**bigint**|使用者等候在檔案發出讀取的總時間 (以毫秒為單位)。|  
|**num_of_writes**|**bigint**|這個檔案所進行的寫入數。|  
|**num_of_bytes_written**|**bigint**|寫入檔案的總位元組數。|  
|**io_stall_write_ms**|**bigint**|使用者等候檔案完成寫入的總時間 (以毫秒為單位)。|  
|**io_stall**|**bigint**|使用者等候檔案完成 I/O 的總時間 (以毫秒為單位)。|  
|**size_on_disk_bytes**|**bigint**|該檔案在磁碟上所用的位元組數。 如果是疏鬆檔案，這個數字就是資料庫快照集在磁碟上所用的實際位元組數。|  
|**file_handle**|**varbinary**|這個檔案的 Windows 檔案控制代碼。|  
|**io_stall_queued_read_ms**|**bigint**|**不適用於：**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]透過[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)]。<br /><br /> IO 資源管理針對讀取導入的總 IO 延遲。 不可為 Null。 如需詳細資訊，請參閱 < [sys.dm_resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)。|  
|**io_stall_queued_write_ms**|**bigint**|**不適用於：**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]透過[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)]。<br /><br />  IO 資源管理針對寫入導入的總 IO 延遲。 不可為 Null。|
|**pdw_node_id**|**int**|**適用於：**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]</br></br>發佈節點的識別碼。
 
  
## <a name="permissions"></a>Permissions  
 需要 VIEW SERVER STATE 權限。 如需詳細資訊，請參閱 <<c0> [ 動態管理檢視和函式&#40;TRANSACT-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)。</c0>  
  
## <a name="examples"></a>範例  

### <a name="a-return-statistics-for-a-log-file"></a>A. 傳回記錄檔的統計的資料

**適用於：** SQL Server （從 2008年開始）、 Azure SQL Database

 下列範例會傳回 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫中記錄檔的統計資料。  
  
```sql  
SELECT * FROM sys.dm_io_virtual_file_stats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="b-return-statistics-for-file-in-tempdb"></a>B. 在 tempdb 中傳回檔案的統計資料

**適用於：** Azure SQL 資料倉儲

```sql
SELECT * FROM sys.dm_pdw_nodes_io_virtual_file_stats 
WHERE database_name = 'tempdb' AND file_id = 2;

```

## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [我 O 相關動態管理檢視和函數&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

