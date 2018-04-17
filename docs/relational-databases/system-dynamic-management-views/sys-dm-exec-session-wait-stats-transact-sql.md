---
title: sys.dm_exec_session_wait_stats (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ddca79ef78b42c06488f8c103b655d280418f7a6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmexecsessionwaitstats-transact-sql"></a>sys.dm_exec_session_wait_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  傳回每個工作階段中執行的執行緒所遇到的所有等候的相關資訊。 您可以使用此檢視來診斷效能問題[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]工作階段以及特定查詢和批次。  此檢視會傳回工作階段會針對彙總的相同資訊[sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)但提供**session_id**以及數字。  
  
**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|工作階段的識別碼。|  
|wait_type|**nvarchar(60)**|等候類型的名稱。 如需詳細資訊，請參閱 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)。|  
|waiting_tasks_count|**bigint**|這個等候類型的等候次數。 這個計數器是從每次開始等候時逐量遞增計算。|  
|wait_time_ms|**bigint**|這個等候類型的總等候時間 (以毫秒為單位)。 這個時間包括 signal_wait_time_ms 在內。|  
|max_wait_time_ms|**bigint**|這個等候類型的等候時間上限。|  
|signal_wait_time_ms|**bigint**|從等候執行緒接獲訊號到開始執行的時間。|  
  
## <a name="remarks"></a>備註  
 此 DMV 在開啟工作階段時，或重設工作階段時，會重設工作階段的資訊 (如果連接共用)，  
  
 等候類型的相關資訊，請參閱[sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)。  
  
## <a name="permissions"></a>Permissions  
 如果使用者具有**VIEW SERVER STATE**伺服器上的權限，使用者會看到所有執行的工作階段的執行個體上[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; 否則使用者會看到目前工作階段。  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server 作業系統相關的動態管理檢視&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 
