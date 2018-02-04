---
title: sys.dm_pdw_dms_cores (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72bf3b6d8ce2aa5c445540efb23966e83db89ce6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwdmscores-transact-sql"></a>sys.dm_pdw_dms_cores (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  保留應用裝置的計算節點上執行的所有 DMS 服務的相關資訊。 它會列出每個服務執行個體，也就是目前節點的每一個資料列的一個資料列。  
  
|資料行名稱|資料類型|Description|範圍|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|與這個 DMS 核心相關聯的唯一數值識別碼。<br /><br /> 此檢視的索引鍵。|將節點上執行此 DMS 核心的 pdw_node_id。|  
|pdw_node_id|**int**|此 DMS 服務執行所在之節點的識別碼。|請參閱中的 node_id [sys.dm_pdw_nodes &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(32)**|DMS 服務的目前狀態。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 這份檢視所保留的最大資料列的相關資訊，請參閱中的系統檢視的最大值 」 一節[最小和最大值 (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)主題。  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
