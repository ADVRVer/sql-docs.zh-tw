---
title: sys.dm_exec_connections (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 11/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_connections_TSQL
- sys.dm_exec_connections_TSQL
- sys.dm_exec_connections
- dm_exec_connections
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_connections dynamic management view
ms.assetid: 6bd46fe1-417d-452d-a9e6-5375ee8690d8
caps.latest.revision: 50
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 27499bf31561addd909d92a81222662e4470b8b5
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmexecconnections-transact-sql"></a>sys.dm_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回有關與這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體建立之連接及每一個連接之詳細資料的資訊。 傳回 SQL Server 的伺服器寬的連接資訊。 傳回目前 SQL database 的資料庫連接資訊。  
  
> [!NOTE]
> 若要呼叫從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用[sys.dm_pdw_exec_connections &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-connections-transact-sql.md)。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|識別這項連接的相關工作階段。 可為 Null。|  
|most_recent_session_id|**int**|代表這項連接最近的相關要求的工作階段識別碼 (SOAP 連接可由其他工作階段重複使用)可為 Null。|  
|connect_time|**datetime**|建立連接的時間戳記。 不可為 Null。|  
|net_transport|**nvarchar(40)**|一律傳回**工作階段**當連接已啟用 multiple active result set (MARS)。<br /><br /> **注意：** 描述這個連接所用的實體傳輸通訊協定。 不可為 Null。|  
|protocol_type|**nvarchar(40)**|指定裝載的通訊協定類型。 它目前會區分 TDS (TSQL) 和 SOAP。 可為 Null。|  
|protocol_version|**int**|這項連接的相關資料存取通訊協定的版本。 可為 Null。|  
|endpoint_id|**int**|描述其為何種連接類型的識別碼。 這個 endpoint_id 可用來查詢 sys.endpoints 檢視。 可為 Null。|  
|encrypt_option|**nvarchar(40)**|描述這項連接是否啟用加密的布林值。 不可為 Null。|  
|auth_scheme|**nvarchar(40)**|指定搭配這個連接使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows 驗證配置。 不可為 Null。|  
|node_affinity|**smallint**|識別此連接具有相似性的記憶體節點。 不可為 Null。|  
|num_reads|**int**|這個連接期間所進行的位元組讀取數目。 可為 Null。|  
|num_writes|**int**|這個連接期間所進行的位元組寫入數目。 可為 Null。|  
|last_read|**datetime**|這項連接期間最後一次讀取的時間戳記。 可為 Null。|  
|last_write|**datetime**|這項連接期間最後一次寫入的時間戳記。 不可設為 Null。|  
|net_packet_size|**int**|用來傳送資訊和資料的網路封包大小。 可為 Null。|  
|client_net_address|**varchar(48)**|連接到這部伺服器之用戶端的主機位址。 可為 Null。<br /><br /> 在 V12 之前的版本[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]，此資料行一律會傳回 NULL。|  
|client_tcp_port|**int**|與這項連接相關聯的用戶端電腦上的通訊埠編號。 可為 Null。<br /><br /> 在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]，這個資料行一律會傳回 NULL。|  
|local_net_address|**varchar(48)**|代表這項連接的目標伺服器的 IP 位址。 只適用於使用 TCP 傳輸提供者的連接。 可為 Null。<br /><br /> 在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]，這個資料行一律會傳回 NULL。|  
|local_tcp_port|**int**|當這項連接是使用 TCP 傳輸的連接時，代表這項連接的目標伺服器 TCP 埠。 可為 Null。<br /><br /> 在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]，這個資料行一律會傳回 NULL。|  
|connection_id|**uniqueidentifier**|這用來唯一識別各項連接。 不可為 Null。|  
|parent_connection_id|**uniqueidentifier**|這用來識別 MARS 工作階段在使用的主要連接。 可為 Null。|  
|most_recent_sql_handle|**varbinary(64)**|這項連接所執行之前一項要求的 SQL 控制代碼。 most_recent_sql_handle 資料行一律與 most_recent_session_id 資料行同步。 可為 Null。|  
|pdw_node_id|**int**|**適用於**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此發行版本上的節點識別碼。|  
  
## <a name="permissions"></a>Permissions

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`資料庫的權限。   

## <a name="physical-joins"></a>實體聯結  
 ![Sys.dm_exec_connections 的聯結](../../relational-databases/system-dynamic-management-views/media/join-dm-exec-connections-1.gif "sys.dm_exec_connections 的聯結")  
  
## <a name="relationship-cardinalities"></a>關聯性基數  
  
||||  
|-|-|-|  
|dm_exec_sessions.session_id|dm_exec_connections.session_id|一對一|  
|dm_exec_requests.connection_id|dm_exec_connections.connection_id|多對一|  
|dm_broker_connections.connection_id|dm_exec_connections.connection_id|一對一|  
  
## <a name="examples"></a>範例  
 收集查詢自有連接相關資訊的典型查詢。  
  
```sql  
SELECT   
    c.session_id, c.net_transport, c.encrypt_option,   
    c.auth_scheme, s.host_name, s.program_name,   
    s.client_interface_name, s.login_name, s.nt_domain,   
    s.nt_user_name, s.original_login_name, c.connect_time,   
    s.login_time   
FROM sys.dm_exec_connections AS c  
JOIN sys.dm_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = @@SPID;  
```  
  
## <a name="see-also"></a>另請參閱  

 [執行相關動態管理檢視和函數&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


