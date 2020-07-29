---
title: sqllogship 應用程式
description: sqllogship 應用程式會為 SQL Server 資料庫上的記錄傳送設定執行備份、複製或還原作業，以及清除工作。
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqllogship
ms.assetid: 8ae70041-f3d9-46e4-8fa8-31088572a9f8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: af98af52bfe6416c489be821fa2d8b27092fac27
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918356"
---
# <a name="sqllogship-application"></a>sqllogship 應用程式
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]
  **sqllogship** 應用程式會對記錄傳送組態執行備份、複製或還原作業，以及相關的清除工作。 這些作業是在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的特定執行個體上對特定資料庫執行。  
  
 ![主題連結圖示](../database-engine/configure-windows/media/topic-link.gif "主題連結圖示")如需語法慣例，請參閱[命令提示字元公用程式參考 &#40;Database Engine&#41;](../tools/command-prompt-utility-reference-database-engine.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
sqllogship -server instance_name { -backup primary_id | -copy secondary_id | -restore secondary_id } [ -verboselevel level ] [ -logintimeout timeout_value ] [ -querytimeout timeout_value ]  
```  
  
## <a name="arguments"></a>引數  
 **-server** _instance_name_  
 指定執行作業所在的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。 指定的伺服器執行個體會視指定哪一項記錄傳送作業而定。 若為 **-backup**， *instance_name* 必須是記錄傳送組態中的主要伺服器名稱。 若為 **-copy** 或 **-restore**， *instance_name* 必須是記錄傳送組態中的次要伺服器名稱。  
  
 **-backup** _primary_id_  
 針對主要資料庫執行備份作業，資料庫的主要識別碼是由 *primary_id*指定。 您可以從 [log_shipping_primary_databases](../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md) 系統資料表選取這個識別碼，或使用 [sp_help_log_shipping_primary_database](../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql.md) 預存程序取得這個識別碼。  
  
 備份作業會在備份目錄中建立記錄備份。 **sqllogship** 應用程式接著會根據檔案保留期限，清除任何舊的備份檔案。 接下來，應用程式會記錄主要伺服器和監視伺服器的備份作業歷程。 最後，應用程式會執行 [sp_cleanup_log_shipping_history](../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)，根據保留期限清除舊的記錄資訊。  
  
 **-copy** _secondary_id_  
 執行複製作業，從指定的次要伺服器複製次要資料庫的備份，資料庫的次要識別碼是由 *secondary_id*指定。 您可以從 [log_shipping_secondary](../relational-databases/system-tables/log-shipping-secondary-transact-sql.md) 系統資料表選取這個識別碼，或使用 [sp_help_log_shipping_secondary_database](../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md) 預存程序取得這個識別碼。  
  
 這項作業會將備份檔從備份目錄複製到目的地目錄。 **sqllogship** 應用程式接著會記錄次要伺服器和監視伺服器的複製作業歷程。  
  
 **-restore** _secondary_id_  
 在指定的次要伺服器上對次要資料庫執行還原作業，資料庫的次要識別碼是由 *secondary_id*指定。 您可以使用 **sp_help_log_shipping_secondary_database** 預存程序取得這個識別碼。  
  
 目的地目錄中自最近還原點之後建立的任何備份檔，都會還原至次要資料庫。 **sqllogship** 應用程式接著會根據檔案保留期限，清除任何舊的備份檔案。 接下來，應用程式會記錄次要伺服器和監視伺服器的還原作業歷程。 最後，應用程式會執行 **sp_cleanup_log_shipping_history**，根據保留期限清除舊的記錄資訊。  
  
 **-verboselevel** _level_  
 指定要加入記錄傳送記錄的訊息層級。 *level* 是下列其中一個整數：  
  
|層級|描述|  
|-----------|-----------------|  
|0|輸出不追蹤和偵錯的訊息。|  
|1|輸出錯誤處理訊息。|  
|2|輸出警告和錯誤處理訊息。|  
|**3**|輸出參考用訊息、警告和錯誤處理訊息。 這是預設值。|  
|4|輸出所有偵錯和追蹤訊息。|  
  
 **-logintimeout** _timeout_value_  
 指定嘗試登入伺服器執行個體的逾時時間。預設為 15 秒。 *timeout_value* 是 **int** _。_  
  
 **-querytimeout** _timeout_value_  
 指定啟動執行作業的嘗試逾時時間。預設沒有逾時期限。 *timeout_value* 是 **int** _。_  
  
## <a name="remarks"></a>備註  
 建議您盡可能使用備份、複製和還原作業來執行備份、複製和還原。 若要從批次作業或其他應用程式執行這些作業，請呼叫 [sp_start_job](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md) 預存程序。  
  
 **sqllogship** 所建立的記錄傳送記錄會穿插記錄傳送備份、複製和還原作業所建立的記錄。 如果您要重複使用 **sqllogship** 對記錄傳送組態執行備份、複製或還原作業，請考慮停用對應的一或多個記錄傳送作業。 如需詳細資訊，請參閱 [Disable or Enable a Job](../ssms/agent/disable-or-enable-a-job.md)。  
  
 **sqllogship** 應用程式 (SqlLogShip.exe) 安裝在 x:\Program Files\Microsoft SQL Server\130\Tools\Binn 目錄中。  
  
## <a name="permissions"></a>權限  
 **sqllogship** 使用「Windows 驗證」。 執行命令的「Windows 驗證」帳戶必須擁有 Windows 目錄存取權和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 權限。 需求取決於 **sqllogship** 命令是指定 **-backup**、 **-copy**或 **-restore** 選項。  
  
|選項|目錄存取|權限|  
|------------|----------------------|-----------------|  
|**-backup**|需要讀取/寫入權限才能備份目錄。|需要與 BACKUP 陳述式相同的權限。 如需詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](../t-sql/statements/backup-transact-sql.md)。|  
|**-copy**|需要讀取權限才能備份目錄，以及需要寫入權限才能複製目錄。|需要與 [sp_help_log_shipping_secondary_database](../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md) 預存程序相同的權限。|  
|**-restore**|需要讀取/寫入權限才能複製目錄。|需要與 RESTORE 陳述式相同的權限。 如需詳細資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](../t-sql/statements/restore-statements-transact-sql.md)備份。|  
  
> [!NOTE]  
>  若要找出備份和複製目錄的路徑，您可以執行 **sp_help_log_shipping_secondary_database** 預存程序或檢視 **msdb** 中的 **log_shipping_secondary**資料表。 備份目錄和目的地目錄的路徑分別位於 **backup_source_directory** 和 **backup_destination_directory** 資料行中。  
  
## <a name="see-also"></a>另請參閱  
 [關於記錄傳送 &#40;SQL Server&#41;](../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [log_shipping_primary_databases &#40;Transact-SQL&#41;](../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)   
 [log_shipping_secondary &#40;Transact-SQL&#41;](../relational-databases/system-tables/log-shipping-secondary-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_help_log_shipping_primary_database &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)  
  
  
