---
title: sys.database_mirroring & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring
- database_mirroring
- sys.database_mirroring_TSQL
- database_mirroring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_mirroring catalog view
ms.assetid: 480de2b0-2c16-497d-a6a3-bf7f52a7c9a0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bea7712fd4efa1934117937a5168843d727d0dc6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62693917"
---
# <a name="sysdatabasemirroring-transact-sql"></a>sys.database_mirroring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體中每個資料庫，各包含一個資料列。 如果資料庫不在線上，或未啟用資料庫鏡像，除了 database_id 以外的所有資料行的值會是 NULL。  
  
 若要查看 master 或 tempdb 以外的資料庫的資料列，您必須是資料庫擁有者，或至少具有 ALTER ANY DATABASE 或 VIEW ANY DATABASE 伺服器層級權限或在 master 資料庫的 CREATE DATABASE 權限。 若要查看鏡像資料庫上的非 NULL 值，您必須隸屬**sysadmin**固定的伺服器角色。  
  
> [!NOTE]  
>  如果資料庫未參與鏡像，前置詞為 "mirroring_" 的所有資料行都是 NULL。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|資料庫的識別碼。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體內，這是唯一的。|  
|**mirroring_guid**|**uniqueidentifier**|鏡像合作關係的識別碼。<br /><br /> NULL = 資料庫無法存取或未鏡像。<br /><br /> 注意:如果資料庫未參與鏡像，前置詞為"mirroring_"的所有資料行都是 NULL。|  
|**mirroring_state**|**tinyint**|鏡像資料庫或資料庫鏡像工作階段的狀態。<br /><br /> 0 = 已暫停<br /><br /> 1 = 與其他夥伴中斷連接<br /><br /> 2 = 正在同步處理<br /><br /> 3 = 暫止容錯移轉<br /><br /> 4 = 已同步處理<br /><br /> 5 = 夥伴不同步。 現在不可能進行容錯移轉。<br /><br /> 6 = 夥伴已同步。 現在可能可以進行容錯移轉。 如需容錯移轉，請參閱需求的詳細資訊[Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)。<br /><br /> NULL= 資料庫無法存取或未鏡像。|  
|**mirroring_state_desc**|**nvarchar(60)**|這是鏡像資料庫或資料庫鏡像工作階段之狀態的描述，它有下列幾種：<br /><br /> DISCONNECTED<br /><br /> SYNCHRONIZED<br /><br /> SYNCHRONIZING<br /><br /> PENDING_FAILOVER<br /><br /> SUSPENDED<br /><br /> UNSYNCHRONIZED<br /><br /> SYNCHRONIZED<br /><br /> NULL<br /><br /> 如需詳細資訊，請參閱[鏡像狀態 &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)。|  
|**mirroring_role**|**tinyint**|本機資料庫在資料庫鏡像工作階段中目前所扮演的角色。<br /><br /> 1 = 主體<br /><br /> 2 = 鏡像<br /><br /> NULL= 資料庫無法存取或未鏡像。|  
|**mirroring_role_desc**|**nvarchar(60)**|這是本機資料庫在鏡像中所扮演之角色的描述，它有下列幾種：<br /><br /> PRINCIPAL<br /><br /> MIRROR|  
|**mirroring_role_sequence**|**int**|鏡像夥伴因容錯移轉或強制服務而切換主體和鏡像角色的次數。<br /><br /> NULL= 資料庫無法存取或未鏡像。|  
|**mirroring_safety_level**|**tinyint**|鏡像資料庫的更新安全設定：<br /><br /> 0 = 未知狀態<br /><br /> 1 = 關閉 [非同步]<br /><br /> 2 = 完整 [同步]<br /><br /> NULL= 資料庫無法存取或未鏡像。|  
|**mirroring_safety_level_desc**|**nvarchar(60)**|這是鏡像資料庫的更新交易安全設定，它有下列幾種：<br /><br /> UNKNOWN<br /><br /> OFF<br /><br /> FULL<br /><br /> NULL|  
|**mirroring_safety_sequence**|**int**|將變更的序號更新為交易安全層級。<br /><br /> NULL= 資料庫無法存取或未鏡像。|  
|**mirroring_partner_name**|**nvarchar(128)**|資料庫鏡像夥伴的伺服器名稱。<br /><br /> NULL= 資料庫無法存取或未鏡像。|  
|**mirroring_partner_instance**|**nvarchar(128)**|其他夥伴的執行個體名稱和電腦名稱。 如果夥伴變成主體伺服器，用戶端就需要這項資訊，才能連接到這個夥伴。<br /><br /> NULL= 資料庫無法存取或未鏡像。|  
|**mirroring_witness_name**|**nvarchar(128)**|資料庫鏡像見證的伺服器名稱。<br /><br /> NULL= 沒有見證存在。|  
|mirroring_witness_state|**tinyint**|這是資料庫的資料庫鏡像工作階段中之見證的狀態，它有下列幾種：<br /><br /> 0 = 未知<br /><br /> 1 = 已連接<br /><br /> 2 = 已中斷連接<br /><br /> NULL= 無見證存在、資料庫不在線上或資料庫未鏡像。|  
|**mirroring_witness_state_desc**|**nvarchar(60)**|這是狀態的描述，它有下列幾種：<br /><br /> UNKNOWN<br /><br /> CONNECTED<br /><br /> DISCONNECTED<br /><br /> NULL|  
|**mirroring_failover_lsn**|**numeric(25,0)**|保證寫入雙方磁碟的最新交易記錄的記錄序號 (LSN)。 容錯移轉之後， **mirroring_failover_lsn**供合作夥伴用為新的鏡像伺服器開始同步處理新的鏡像資料庫與新的主體資料庫的重新調整點。|  
|**mirroring_connection_timeout**|**int**|鏡像連接逾時 (以秒為單位)。 這是等待夥伴或見證回應的秒數，過了這段時間，便將它們視為無法使用。 預設的逾時值是 10 秒。<br /><br /> NULL= 資料庫無法存取或未鏡像。|  
|**mirroring_redo_queue**|**int**|在鏡像中重做的最大記錄量。 如果 mirroring_redo_queue_type 設為無限制，也就是預設值，這個資料行就會是 NULL。 如果資料庫不在線上，這個資料行也是 NULL。<br /><br /> 否則，這個資料行會包含最大記錄量 (以 MB 為單位)。 當到達最大值時，會在主體上暫停記錄，等鏡像伺服器趕上。 這項功能會限制容錯移轉的時間。<br /><br /> 如需詳細資訊，請參閱 [預估角色切換期間的服務中斷時間 &#40;資料庫鏡像&#41;](../../database-engine/database-mirroring/estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)的程序交換。|  
|**mirroring_redo_queue_type**|**nvarchar(60)**|UNLIMITED 表示鏡像不會抑制重做佇列。 這是預設值。<br /><br /> 重做佇列的大小上限以 MB 表示。 請注意，如果佇列大小指定為 KB 或 GB，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會將這個值轉換成 MB。<br /><br /> 如果資料庫不在線上，這個資料行就是 NULL。|  
|**mirroring_end_of_log_lsn**|**numeric(25,0)**|已排清至磁碟的本機記錄檔結束。 這相當於強行寫入 LSN 鏡像伺服器 (請參閱**mirroring_failover_lsn**資料行)。|  
|**mirroring_replication_lsn**|**numeric(25,0)**|複寫可傳送的最大 LSN。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)   
 [資料庫和檔案目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [查詢 SQL Server 系統目錄常見問題集](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
