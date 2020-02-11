---
title: sys.databases index_resumable_operations （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 11/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.index_resumable_operations_TSQL
- sys.indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes
- sys.index_resumable_operations
ms.assetid: ''
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d33b78710605841e4559f9c402a18210e25b2daa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73980307"
---
# <a name="sysindex_resumable_operations-transact-sql"></a>sys.databases index_resumable_operations （Transact-sql）

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**index_resumable_operations**是系統檢視，會監視並檢查目前的執行狀態，以取得可繼續的索引重建或建立。  
**適用**于： SQL Server （2017和更新版本）和 Azure SQL Database
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|此索引所屬物件的識別碼（不可為 null）。|  
|**index_id**|**int**|索引的識別碼（不可為 null）。 **index_id**只有在物件內才是唯一的。|
|**name**|**sysname**|索引的名稱。 **name**只有在物件內才是唯一的。|  
|**sql_text**|**nvarchar(max)**|DDL T-sql 語句文字|
|**last_max_dop**|**smallint**|上次使用的 MAX_DOP （預設值 = 0）|
|**partition_number**|**int**|擁有索引或堆積內的資料分割編號。 若為非資料分割資料表和索引，或在重建所有分割區時，此資料行的值為 Null。|
|**狀態**|**tinyint**|可繼續索引的操作狀態：<br /><br />0 = 正在執行<br /><br />1 = 暫停|
|**state_desc**|**Nvarchar （60）**|可繼續索引的操作狀態原因（執行中或已暫停）|  
|**start_time**|**datetime**|索引作業開始時間（不可為 null）|
|**last_pause_time**|**datatime**| 索引作業上次暫停時間（可為 null）。 如果作業正在執行且永遠不會暫停，則為 Null。|
|**total_execution_time**|**int**|從開始時間（以分鐘為單位）的總執行時間（不可為 null）|
|**percent_complete**|**即時**|% 中的索引作業進度完成（不可為 null）。|
|**page_count**|**Bigint**|索引建立作業為新的和對應索引所配置的索引頁面總數（不可為 null）。

## <a name="permissions"></a>權限

[!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  

## <a name="example"></a>範例

 列出處於暫停狀態的所有可繼續的索引建立或重建作業。

```sql
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```

## <a name="see-also"></a>另請參閱

- [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)
- [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)
- [目錄檢視](catalog-views-transact-sql.md)
- [物件目錄檢視](object-catalog-views-transact-sql.md)
- [sys.indexes](sys-xml-indexes-transact-sql.md)
- [sys.index_columns](sys-index-columns-transact-sql.md)
- [sys.xml_indexes](sys-xml-indexes-transact-sql.md)
- [sys.objects](sys-index-columns-transact-sql.md)
- [sys.key_constraints](sys-key-constraints-transact-sql.md)
- [sys.filegroups](sys-filegroups-transact-sql.md)
- [sys.partition_schemes](sys-partition-schemes-transact-sql.md)
- [查詢 SQL Server 系統目錄 FAQ](querying-the-sql-server-system-catalog-faq.md)
