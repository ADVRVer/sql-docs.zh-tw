---
title: _pdw_nodes_exec_query_plan （Transact-sql） |Microsoft Docs
description: 動態管理檢視會針對計畫控制碼所指定的批次，傳回 XML 格式的執行程式表。 計畫控制代碼指定的計畫可以是快取或目前正在執行的計畫。
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 96b499ea5bc38d2a4cf9c380116108009ea46086
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73145633"
---
# <a name="syspdw_nodes_dm_exec_query_plan-transact-sql"></a>sys.databases _nodes_dm_exec_query_plan （Transact-sql）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

針對計畫控制代碼指定的批次，以 XML 格式傳回顯示計畫。 計畫控制代碼指定的計畫可以是快取或目前正在執行的計畫。  

## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|[名稱]|[描述]|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**整數**|與節點相關聯的唯一數值識別碼。| 
|**dbid**|**smallint**|當編譯對應於這個計畫的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式時，作用中內容資料庫的識別碼。 若為未規劃和備妥的 SQL 語句，則為編譯語句的資料庫識別碼。<br /><br /> 資料行可為 Null。|  
|**objectid**|**整數**|這個查詢計畫的物件識別碼 (如預存程序或使用者自訂函數)。 若是臨機操作和備妥的批次，這個資料行是**null**。<br /><br /> 資料行可為 Null。|  
|**number**|**smallint**|編號預存程序整數。 若是臨機操作和備妥的批次，這個資料行是**null**。<br /><br /> 資料行可為 Null。| 
|**加密**|**bit**|指出對應的預存程序是否加密。<br /><br /> 0 = 未加密<br /><br /> 1 = 加密<br /><br /> 資料行不可為 Null。|  
|**query_plan**|**xml**|包含使用*plan_handle*指定之查詢執行計畫的編譯時間顯示計畫標記法。 顯示計畫是 XML 格式。 每個包含諸如特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式、預存程序呼叫和使用者自訂函數呼叫的批次，都會產生一份計畫。<br /><br /> 資料行可為 Null。|  
  
## <a name="remarks"></a>Remarks  
適用于[_exec_query_plan](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql?view=sql-server-ver15)的相同備註。  
  
## <a name="permissions"></a>[權限]  
 需要伺服器的**系統管理員（sysadmin** ）伺服器角色或 `VIEW SERVER STATE` 許可權。  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理&#40;Views transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

 ## <a name="next-steps"></a>後續的步驟
 如需更多開發秘訣，請參閱[SQL 資料倉儲開發總覽](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop)。