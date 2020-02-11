---
title: sys.databases dm_exec_session_wait_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fc51bec78cf01522e6731648bdb7870ea7d9fb0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73982614"
---
# <a name="sysdm_exec_session_wait_stats-transact-sql"></a>sys.databases dm_exec_session_wait_stats （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  傳回針對每個會話執行之執行緒所遇到之所有等候的相關資訊。 您可以使用此視圖來診斷[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]會話的效能問題，以及特定查詢和批次。  此視圖會傳回與針對 sys.databases 所匯總的相同資訊[dm_os_wait_stats &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)但也會提供**session_id**號碼。  
  
**適用**于： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] （ [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]和更新版本）。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|會話的識別碼。|  
|wait_type|**Nvarchar （60）**|等候類型的名稱。 如需詳細資訊，請參閱 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)。|  
|waiting_tasks_count|**Bigint**|這個等候類型的等候次數。 這個計數器是從每次開始等候時逐量遞增計算。|  
|wait_time_ms|**Bigint**|這個等候類型的總等候時間 (以毫秒為單位)。 這個時間包括 signal_wait_time_ms 在內。|  
|max_wait_time_ms|**Bigint**|這個等候類型的等候時間上限。|  
|signal_wait_time_ms|**Bigint**|從等候執行緒接獲訊號到開始執行的時間。|  
  
## <a name="remarks"></a>備註  
 此 DMV 會在會話開啟或會話重設（如果連接共用）時重設會話的資訊，  
  
 如需等候類型的詳細資訊，請參閱[dm_os_wait_stats &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)。  
  
## <a name="permissions"></a>權限  
 如果使用者具有伺服器的**VIEW SERVER STATE**許可權，使用者會看到實例上所有執行中的會話[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];否則，使用者只會看到目前的會話。  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server 作業系統相關的動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 
