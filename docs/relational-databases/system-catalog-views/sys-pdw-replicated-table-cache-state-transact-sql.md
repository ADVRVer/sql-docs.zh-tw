---
title: "sys.pdw_replicated_table_cache_state (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 07/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: barbkess
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5efc510645a6a5648c4d1e2c6e2c05567159e6e2
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  傳回快取使用的複寫資料表相關聯的狀態**object_id**。  
  
|資料行名稱|資料類型|Description|範圍|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|資料表物件識別碼。 請參閱[sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。<br /><br /> **object_id**針對此檢視的索引鍵。||  
|state|**nvarchar(40)**|這份資料表的複寫的資料表快取狀態。|'NotReady','Ready'|  
  
## <a name="example"></a>範例
這個範例會聯結 sys.pdw_replicated_table_cache_state 與 sys.tables 來擷取資料表名稱和複寫的資料表快取的狀態。

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>後續的步驟  
 如需所有 SQL 資料倉儲和平行處理資料倉儲的目錄檢視的清單，請參閱[SQL 資料倉儲和平行資料倉儲目錄檢視](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)。   
  
