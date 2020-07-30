---
title: sys.databases pdw_materialized_view_mappings （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: bf5146b885839b88268b5ffbd6fe642503523655
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395796"
---
# <a name="syspdw_materialized_view_mappings-transact-sql"></a>sys.databases pdw_materialized_view_mappings （Transact-sql）  

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

藉由 object_id，將具體化視圖系結至內建物件名稱。

Physical_name 的資料行和 object_id 會形成此目錄檢視的索引鍵。
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|physical_name |**Nvarchar （36）**|具體化視圖的機構名稱。|  
|object_id  |**int**|具體化視圖的物件識別碼。 請參閱[sys.databases （transact-sql）](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql?view=azure-sqldw-latest)。| 

## <a name="permissions"></a>權限

需要 VIEW DATABASE STATE 權限。
  
## <a name="see-also"></a>另請參閱

[使用具體化視圖進行效能微調](/azure/sql-data-warehouse/performance-tuning-materialized-views)   
[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[說明 &#40;Transact-sql&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL 資料倉儲與平行處理資料倉儲目錄檢視](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Azure SQL 資料倉儲中支援的系統檢視](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Azure SQL 資料倉儲中支援的 T-SQL 陳述式](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements) 
