---
title: "sys.column_store_segments (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 01/15/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f73379d3ae23570f95209631444d1335279a5ef5
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2018
---
# <a name="syscolumnstoresegments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

傳回一個資料列資料行存放區索引中每個資料行區段。 沒有每個資料行，每個資料列群組的一個資料行區段。 例如，具有 10 個資料列群組和 34 的資料行的資料表傳回 340 的資料列。 
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|指出資料分割識別碼。 在資料庫中，這是唯一的。|  
|**hobt_id**|**bigint**|具有此資料行存放區索引之資料表的堆積或 B 型樹狀目錄索引 (hobt) 的識別碼。|  
|**column_id**|**int**|資料行存放區資料行的識別碼。|  
|**segment_id**|**int**|資料列群組的識別碼。 回溯相容性，資料行名稱會繼續可呼叫 segment_id，即使這是資料列群組識別碼。 您可以唯一識別區段使用\<hobt_id，sys.partitions、 column_id >，< segment_id >。|  
|**version**|**int**|資料行區段格式的版本。|  
|**encoding_type**|**int**|該區段使用的編碼類型：<br /><br /> 1 = VALUE_BASED-非字串/二進位與 （非常類似於 4 有一些內部的變化） 沒有字典<br /><br /> 2 = VALUE_HASH_BASED-字典中的一般值與非二進位字串/資料行<br /><br /> 3 = STRING_HASH_BASED-字典中的一般值字串/二進位資料行<br /><br /> 4 = STORE_BY_VALUE_BASED-非字串/二進位與沒有字典<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED-字串/二進位檔沒有字典<br /><br /> 所有編碼方式的位元封裝執行長度編碼盡可能利用。|  
|**row_count**|**int**|資料列群組中的列數。|  
|**has_nulls**|**int**|如果資料行區段具有 Null 值，則為 1。|  
|**base_id**|**bigint**|如果使用編碼類型 1 的基底值識別碼。  如果沒有使用編碼類型 1，base_id 會設定為-1。|  
|**magnitude**|**float**|如果正在使用編碼類型 1 的範圍。  如果沒有使用編碼類型 1，會將範圍設為-1。|  
|**primary_dictionary_id**|**int**|值為 0 表示通用的字典。 -1 表示沒有為此資料行建立全域字典。|  
|**secondary_dictionary_id**|**int**|為非零的值會指向本機字典中目前的區段 （也就是資料列群組） 此資料行。 -1 表示沒有任何本機的字典，此區段。|  
|**min_data_id**|**bigint**|資料行區段中的最小資料識別碼。|  
|**max_data_id**|**bigint**|資料行區段中的最大資料識別碼。|  
|**null_value**|**bigint**|用來表示 Null 的值。|  
|**on_disk_size**|**bigint**|區段大小 (以位元組為單位)。|  
  
## <a name="remarks"></a>備註  
 下列查詢會傳回資料行存放區索引之區段的相關資訊。  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 所有資料行都至少需要**VIEW DEFINITION**資料表的權限。 下列資料行傳回 null，除非使用者也必須**選取**權限： has_nulls、 base_id、 magnitude、 min_data_id、 max_data_id 和 null_value。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [物件目錄檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [資料行存放區索引指南](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

