---
title: sys.pdw_nodes_indexes (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 261bcb7f-a906-4979-b274-bc5f1aa66426
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 04591e83fdfd8222a84480f983b21a6d77d51da2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwnodesindexes-transact-sql"></a>sys.pdw_nodes_indexes (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  傳回索引[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]。  
  
|資料行名稱|資料類型|Description|範圍|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|此索引所屬的物件識別碼。||  
|name|**sysname**|索引的名稱。 名稱只物件內是唯一。 NULL = 堆積||  
|index_id|**int**|索引的識別碼。 index_id 只物件內是唯一。<br /><br /> 0 = 堆積<br /><br /> 1 = 叢集索引<br /><br /> > 1 = 非叢集索引||  
|型別|**tinyint**|索引的類型：<br /><br /> 0 = 堆積<br /><br /> 1 = 叢集<br /><br /> 2 = 非叢集<br /><br /> 5 = 叢集 xVelocity 記憶體最佳化的資料行存放區索引|  
|type_desc|**nvarchar(60)**|索引類型的描述：<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> 叢集資料行存放區||  
|is_unique|**bit**|0 = 索引不是唯一的。|一律是 0。|  
|data_space_id|**int**|這個索引的資料空間識別碼。 資料空間是一個檔案群組或分割區結構描述。<br /><br /> 0 = object_id 是資料表值函式。||  
|ignore_dup_key|**bit**|0 = IGNORE_DUP_KEY 是 OFF。|一律是 0。|  
|is_primary_key|**bit**|1 = 索引是 PRIMARY KEY 條件約束的一部分。|一律是 0。|  
|is_unique_constraint|**bit**|1 = 索引是 UNIQUE 條件約束的一部分。|一律是 0。|  
|fill_factor|**tinyint**|> 0 = 當建立或重建索引時，所用的 FILLFACTOR 百分比。<br /><br /> 0 = 預設值|一律是 0。|  
|is_padded|**bit**|0 = PADINDEX 是 OFF。|一律是 0。|  
|is_disabled|**bit**|1 = 索引已停用。<br /><br /> 0 = 索引未停用。||  
|is_hypothetical|**bit**|0 = 索引不是假設的。|一律是 0。|  
|allow_row_locks|**bit**|1 = 索引允許資料列鎖定。|永遠為 1。|  
|allow_page_locks|**bit**|1 = 索引允許頁面鎖定。|永遠為 1。|  
|has_filter|**bit**|0 = 索引沒有篩選。|一律是 0。|  
|filter_definition|**nvarchar(max)**|包含在已篩選之索引內的資料列子集運算式。|一律為 NULL。|  
|pdw_node_id|**int**|唯一識別項[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]節點。|NOT NULL|  
  
## <a name="permissions"></a>Permissions  
 需要 CONTROL SERVER 權限。  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲目錄檢視](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
