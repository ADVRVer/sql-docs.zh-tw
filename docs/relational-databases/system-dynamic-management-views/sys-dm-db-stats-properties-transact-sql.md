---
title: "sys.dm_db_stats_properties (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 12/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_stats_properties_TSQL
- sys.dm_db_stats_properties
- dm_db_stats_properties_TSQL
- dm_db_stats_properties
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_stats_properties
ms.assetid: 8a54889d-e263-4881-9fcb-b1db410a9453
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d1603e9d1fb3fb9e84556f432c5b421844f8c1c3
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2018
---
# <a name="sysdmdbstatsproperties-transact-sql"></a>sys.dm_db_stats_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  針對目前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的指定資料庫物件 (資料表或索引檢視表) 傳回統計資料的屬性。 對於資料分割資料表，請參閱類似[sys.dm_db_incremental_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md)。 
 
## <a name="syntax"></a>語法  
  
```  
sys.dm_db_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>引數  
 *object_id*  
 這是目前資料庫中，要求其中一個統計資料屬性之物件的識別碼。 *@object_id* 是 **int**。  
  
 *stats_id*  
 這是指定 *object_id*之統計資料的識別碼。 您可以從 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) 動態管理檢視取得統計資料識別碼。 *stats_id* 是 **int**。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|object_id|**int**|要傳回統計資料物件屬性之物件 (資料表或索引檢視表) 的識別碼。|  
|stats_id|**int**|統計資料物件的識別碼。 這在資料表或索引檢視表中是唯一的。 如需詳細資訊，請參閱 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)。|  
|last_updated|**datetime2**|上次更新統計資料物件的日期和時間。 如需詳細資訊，請參閱[備註](#Remarks)此頁面中的區段。|  
|rows|**bigint**|上一次更新統計資料時位於資料表或索引檢視表中的資料列總數。 如果篩選了統計資料或是統計資料對應至篩選過的索引，此資料列數可能會少於資料表中的資料列數。|  
|rows_sampled|**bigint**|針對統計資料計算進行取樣的資料列總數。|  
|步驟|**int**|長條圖中的步驟數。 如需詳細資訊，請參閱 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)並未包含檢視。|  
|unfiltered_rows|**bigint**|套用篩選運算式 (針對篩選的統計資料) 之前，資料表中的資料列總數。 如果統計資料未經過篩選，unfiltered_row 就會等於 rows 資料行中傳回的值。|  
|modification_counter|**bigint**|自從上次更新統計資料以來，前端統計資料資料行 (用以建置長條圖的資料行) 的總修改次數。<br /><br /> 記憶體最佳化資料表： 正在啟動[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]然後在[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]此資料行包含： 修改資料表的最後一個時間統計資料已更新或資料庫已重新啟動之後的總數。|  
|persisted_sample_percent|**float**|保存未明確指定取樣百分比的統計資料更新所使用的取樣百分比。 如果值為零，這個統計資料的設定沒有持續性的範例百分比。<br /><br /> **適用於：** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4|  
  
## <a name="Remarks"></a> 備註  
 **sys.dm_db_stats_properties**傳回任何下列的情況下的空白資料列集：  
  
-   **object_id**或**stats_id**是 NULL。    
-   找不到指定的物件，或者該物件沒有對應至資料表或索引檢視表。    
-   指定的統計資料識別碼沒有對應至指定之物件識別碼的現有統計資料。    
-   目前的使用者沒有檢視統計資料物件的權限。  
  
 此行為可讓您安全地使用**sys.dm_db_stats_properties**當交叉套用至檢視中的資料列例如**sys.objects**和**sys.stats**。  
 
統計資料更新將日期儲存在[統計資料的 blob 物件](../../relational-databases/statistics/statistics.md#DefinitionQOStatistics)搭配[長條圖](../../relational-databases/statistics/statistics.md#histogram)和[密度向量](../../relational-databases/statistics/statistics.md#density)、 中繼資料中找不到。 讀取任何資料時產生統計資料，就不會建立統計資料的 blob，日期無法使用，而*last_updated*資料行是 NULL。 這是篩選的統計資料述詞未傳回任何資料列，或新的空白資料表的情況。
  
## <a name="permissions"></a>Permissions  
 要求使用者對於統計資料資料行擁有選取權限，或是使用者擁有資料表，或使用者是 `sysadmin` 固定伺服器角色、`db_owner` 固定資料庫角色或 `db_ddladmin` 固定資料庫角色的成員。  
  
## <a name="examples"></a>範例  

### <a name="a-simple-example"></a>A. 簡單範例
下列範例會傳回的統計資料`Person.Person`AdventureWorks 資料庫中的資料表。

```sql
SELECT * FROM sys.dm_db_stats_properties (object_id('Person.Person'), 1);
``` 
  
### <a name="b-returning-all-statistics-properties-for-a-table"></a>B. 傳回資料表的所有統計資料屬性  
 下列範例會傳回 TEST 資料表現有的所有統計資料屬性。  
  
```sql  
SELECT sp.stats_id, name, filter_definition, last_updated, rows, rows_sampled, steps, unfiltered_rows, modification_counter   
FROM sys.stats AS stat   
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE stat.object_id = object_id('TEST');  
```  
  
### <a name="c-returning-statistics-properties-for-frequently-modified-objects"></a>C. 傳回經常修改之物件的統計資料屬性  
 下列範例會傳回目前資料庫中，自從上次更新統計資料以來修改前端資料行超過 1000 次的所有資料表、索引檢視表和統計資料。  
  
```sql  
SELECT obj.name, obj.object_id, stat.name, stat.stats_id, last_updated, modification_counter  
FROM sys.objects AS obj   
INNER JOIN sys.stats AS stat ON stat.object_id = obj.object_id  
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE modification_counter > 1000;  
```  
  
## <a name="see-also"></a>請參閱  
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [物件相關的動態管理檢視和函數 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
 [sys.dm_db_incremental_stats_properties (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md)  
 [sys.dm_db_stats_histogram (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
  

