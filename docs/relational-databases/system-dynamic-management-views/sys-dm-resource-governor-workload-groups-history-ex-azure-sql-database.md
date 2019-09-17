---
title: sys.databases _resource_governor_workload_groups_history_ex （Azure SQL Database） |Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups_history_ex_TSQL
- sys.dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_resource_governor_workload_groups_history_ex dynamic management view
author: joesackmsft
ms.author: josack
ms.openlocfilehash: 5fea5badf14ce9863f07dff189f1665788ec5fb6
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70873777"
---
# <a name="sysdm_resource_governor_workload_groups_history_ex-azure-sql-database"></a>sys.dm_resource_governor_workload_groups_history_ex (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

針對 Azure SQL Database 的資源集區統計資料，以20秒的 128 32 間隔傳回快照集。
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**pool_id**| ssNoversion |資源集區的識別碼。 不可為 Null。|
|**group_id**| ssNoversion |工作負載群組的識別碼。 不可為 Null。|
|**name**| nvarchar(256) |工作負載群組的名稱。 不可為 Null。|
|**snapshot_time**| datetime |所建立之資源群組統計資料快照集的日期時間。|
|**duration_ms**| ssNoversion |目前與上一個快照之間的持續時間。|
|**active_worker_count**| ssNoversion |目前快照中的工作者總數。|
|**active_request_count**| ssNoversion |目前的要求計數。 不可為 Null。|
|**active_session_count**| ssNoversion |目前快照中的作用中會話總數。|
|**total_request_count**| Bigint |已在工作負載群組中完成之要求的累計計數。 不可為 Null。|
|**delta_request_count**| ssNoversion |自上一個快照集以來，在工作負載群組中完成的要求計數。 不可為 Null。|
|**total_cpu_usage_ms**| Bigint |此工作負載群組的累計 CPU 使用量 (以毫秒為單位)。 不可為 Null。|
|**delta_cpu_usage_ms**| ssNoversion |自上一個快照以來的 CPU 使用率（以毫秒為單位）。 不可為 Null。|
|**delta_cpu_usage_preemptive_ms**| ssNoversion |自上一個快照集以來，由 SQL CPU RG 不管理的搶先式 win32 呼叫。|
|**delta_reads_reduced_memgrant_count**| ssNoversion |自上一個快照集以來已達到最大查詢大小限制的記憶體授與計數。 不可為 Null。|
|**reads_throttled**| ssNoversion |已節流的讀取總數。|
|**delta_reads_queued**| ssNoversion |自上一個快照集以來，已排入佇列的讀取 Io 總數。 可為 Null。 如果資源群組不受 IO 管制，則為 Null。|
|**delta_reads_issued**| ssNoversion |自上一個快照集以來發出的讀取 Io 總數。 可為 Null。 如果資源群組不受 IO 管制，則為 Null。|
|**delta_reads_completed**| ssNoversion |自上一個快照集以來完成的讀取 Io 總數。 不可為 Null。|
|**delta_read_bytes**| Bigint |自上一個快照集以來讀取的總位元組數。 不可為 Null。|
|**delta_read_stall_ms**| ssNoversion |自上一個快照以來，讀取 IO 抵達和完成的總時間（以毫秒為單位）。 不可為 Null。|
|**delta_read_stall_queued_ms**| ssNoversion |讀取 IO 抵達和上次快照集後發生問題的總時間（以毫秒為單位）。 可為 Null。 如果資源群組不受 IO 管制，則為 Null。 非零的 delta_read_stall_queued_ms 表示 IO 受到 RG 的影響。|
|**delta_writes_queued**| ssNoversion |自上一個快照集以來，排入佇列的總 Io。 可為 Null。 如果資源群組不受 IO 管制，則為 Null。|
|**delta_writes_issued**| ssNoversion |自上一個快照集以來發行的寫入 Io 總數。 可為 Null。 如果資源群組不受 IO 管制，則為 Null。|
|**delta_writes_completed**| ssNoversion |自上一個快照集以來完成的總寫入 Io。 不可為 Null。|
|**delta_writes_bytes**| Bigint |自上一個快照集以來寫入的總位元組數。 不可為 Null。|
|**delta_write_stall_ms**| ssNoversion |自上一個快照集起，寫入 IO 抵達與完成的總時間（以毫秒為單位）。 不可為 Null。|
|**delta_background_writes**| ssNoversion |自上一個快照以來，背景工作所執行的寫入總數。|
|**delta_background_write_bytes**| Bigint |自上一個快照以來，背景工作所執行的寫入大小總計（以位元組為單位）。|
|**delta_log_bytes_used**| Bigint |自上次快照集以來使用的記錄檔，以位元組為單位。|
|**delta_log_temp_db_bytes_used**| Bigint |自上一個快照集以來使用的 Tempdb 記錄（以位元組為單位）。|
|**delta_query_optimizations**| Bigint |自上一個快照集以來，此工作負載群組中的查詢優化計數。 不可為 Null。|
|**delta_suboptimal_plan_generations**| Bigint |在此工作負載群組中，由於上一個快照集以來的記憶體壓力，而發生的次佳計畫層代計數。 不可為 Null。
|**max_memory_grant_kb**| Bigint |群組的最大記憶體授與（以 KB 為單位）。|
|**max_request_cpu_msec**| Bigint |單一要求的最大 CPU 使用量 (以毫秒為單位)。 不可為 Null。|
|**max_concurrent_request**| ssNoversion |並行要求之最大數目的目前設定。 不可為 Null。|
|**max_io**| ssNoversion |群組的最大 IO 限制。|
|**max_global_io**| ssNoversion |僅供參考之用。 不支援。 我們無法保證未來的相容性。
|**max_queued_io**| ssNoversion |僅供參考之用。 不支援。 我們無法保證未來的相容性。|
|**max_log_rate_kb**| Bigint |資源群組層級的最大記錄速率（每秒千位元組）。|
|**max_session**| ssNoversion |群組的會話限制。|
|**max_worker**| ssNoversion |群組的背景工作限制。|
|||

## <a name="permissions"></a>Permissions

此視圖需要 VIEW SERVER STATE 許可權。

## <a name="remarks"></a>備註

使用者可以存取此動態管理檢視，以監視使用者工作負載集區的近乎即時資源耗用量，以及 Azure SQL Database 實例的系統內部集區。

> [!IMPORTANT]
> 此 DMV 所呈現的大部分資料都是供內部使用，而且可能隨時變更。

## <a name="examples"></a>範例

下列範例會依使用者集區傳回每個快照的最大記錄速率資料和耗用量：

```sql
SELECT snapshot_time,
       name,
       max_log_rate_kb,
       delta_log_bytes_used
FROM sys.dm_resource_governor_workload_groups_history_ex
WHERE name LIKE 'User%'
ORDER BY snapshot_time DESC;
```

## <a name="see-also"></a>另請參閱

- [翻譯記錄速率治理](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [彈性集區 DTU 資源限制](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [彈性集區 vCore 資源限制](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
