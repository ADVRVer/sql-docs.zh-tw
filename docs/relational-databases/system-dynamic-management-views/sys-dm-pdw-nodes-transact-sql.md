---
title: dm_pdw_nodes (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 9ba367379795408a79b412c5b4c04097484bfd2b
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197212"
---
# <a name="sysdm_pdw_nodes-transact-sql"></a>dm_pdw_nodes (Transact-sql) 
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  保存中所有節點的相關資訊 [!INCLUDE[ssAPS](../../includes/ssaps-md.md)] 。 它會針對設備中的每個節點列出一個資料列。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|與節點相關聯的唯一數值識別碼。<br /><br /> 此視圖的索引鍵。|在設備上是唯一的，不論類型為何。|  
|類型|**nvarchar(32)**|節點的類型。|「計算」、「控制項」、「管理」|  
|name|**nvarchar(32)**|節點的邏輯名稱。|適當長度的任何字串。|  
|address|**nvarchar(32)**|此節點的 IP 位址。|格式為 [0-255]。[0-255]。[0-255]。[0-255]。|  
|is_passive|**int**|指出執行節點的虛擬機器是否正在指派的伺服器上執行，或已故障切換至待命伺服器。|0-節點 VM 正在源伺服器上執行。<br /><br /> 1-節點 VM 正在待命伺服器上執行。|  
|region|**nvarchar(32)**|節點正在執行的區域。|' PDW '、' HDINSIGHT '|  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
