---
title: sys.dm_os_server_diagnostics_log_configurations |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations_TSQL
- dm_os_server_diagnostics_log_configurations
- dm_os_server_diagnostics_log_configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_os_server_diagnostics_log_configurations
- sys.dm_os_server_diagnostics_log_configurations
ms.assetid: c09ea433-d283-4f83-af69-d458aad59217
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6c895d4ab88f54620f2305783d8d2e1a3699e1b8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmosserverdiagnosticslogconfigurations"></a>sys.dm_os_server_diagnostics_log_configurations
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  傳回一個資料列，並在其中包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集診斷記錄檔目前的組態。 這些屬性設定可決定要開啟或關閉診斷記錄，以及記錄檔的位置、數目與大小。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|is_enabled|**bit**|指定是要開啟或關閉記錄。<br /><br /> 1 = 開啟診斷記錄功能<br /><br /> 0 = 關閉診斷記錄功能|  
|max_size|**int**|每個診斷記錄檔可成長的大小上限 (以 MB 為單位)。 預設值是 100 MB。|  
|max_files|**int**|在回收以用於新的診斷記錄檔之前，電腦上可儲存的診斷記錄檔數目上限。|  
|路徑|**nvarchar(260)**|指定診斷記錄檔位置的路徑。 預設位置是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體之安裝資料夾內的 \<\MSSQL\Log>。|  
  
## <a name="permissions"></a>Permissions  
 需要 SQL Server 容錯移轉叢集執行個體的 VIEW SERVER STATE 權限。  
  
## <a name="examples"></a>範例  
 下列範例會使用 sys.dm_os_server_diagnostics_log_configurations 傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉診斷記錄檔的屬性設定。  
  
```  
SELECT <list of columns>  
FROM sys.dm_os_server_diagnostics_log_configurations;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|IS_ENABLED|PATH|MAX_SIZE|MAX_FILES|  
|-----------------|----------|---------------|----------------|  
|1|\<C:\Program Files\Microsoft SQL Server\MSSQL13\MSSQL\Log>|10|10|  
  
## <a name="see-also"></a>另請參閱  
 [檢視及閱讀容錯移轉叢集執行個體診斷記錄檔](../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  
