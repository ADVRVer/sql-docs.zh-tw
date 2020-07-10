---
title: pdw_distributions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 572b5187-9753-4063-adf8-65dea87d11f8
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 12a3318f88a719ab70043e2685a475e14cf24fdc
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197395"
---
# <a name="syspdw_distributions-transact-sql"></a>pdw_distributions (Transact-sql) 
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  保存設備上散發套件的相關資訊。 它會針對每個設備散發列出一個資料列。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|distribution_id|**int**|與散發相關聯的唯一數值識別碼。<br /><br /> 此視圖的索引鍵。|1到設備中的計算節點數目乘以每個計算節點的散發數目。|  
|pdw_node_id|**int**|此散發所在節點的識別碼。|請參閱[dm_pdw_nodes &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)中的 pdw_node_id。|  
|name|**nvarchar(32)**|與散發相關聯的字串識別碼，用來做為分散式資料表的尾碼。|由 ' a-z '、' a-z '、' 0-9 '、' _ '、'-' 組成的字串。|  
|position|**int**|相對於該節點上其他散發的節點內的分佈位置。|1到每個節點的散發數目。|  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲與平行處理資料倉儲目錄檢視](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
