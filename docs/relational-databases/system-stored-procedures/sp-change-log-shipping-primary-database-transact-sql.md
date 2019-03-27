---
title: sp_change_log_shipping_primary_database & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_primary_database
- sp_change_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_primary_database
ms.assetid: 8c9dce6b-d2a3-4ca7-a832-8f59a5adb214
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3a713687d41c21a3c99c30d6b7192d7c59e41505
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492720"
---
# <a name="spchangelogshippingprimarydatabase-transact-sql"></a>sp_change_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  變更主要資料庫設定。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_change_log_shipping_primary_database [ @database = ] 'database'  
[, [ @backup_directory = ] 'backup_directory']   
[, [ @backup_share = ] 'backup_share']   
[, [ @backup_retention_period = ] 'backup_retention_period']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] 'backup_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
[, [ @backup_compression = ] backup_compression_option ]   
```  
  
## <a name="arguments"></a>引數  
`[ @database = ] 'database'` 是主要伺服器上名稱。 *primary_database&lt*已**sysname**，沒有預設值。  
  
`[ @backup_directory = ] 'backup_directory'` 是主要伺服器上備份資料夾的路徑。 *backup_directory*已**nvarchar(500)**，沒有預設值，不能是 NULL。  
  
`[ @backup_share = ] 'backup_share'` 是主要伺服器上備份目錄的網路路徑。 *backup_share*已**nvarchar(500)**，沒有預設值，不能是 NULL。  
  
`[ @backup_retention_period = ] 'backup_retention_period'` 這是時間的以分鐘為單位，將記錄備份檔儲存在備份目錄中主要伺服器上長度。 *backup_retention_period*已**int**，沒有預設值，不能是 NULL。  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'` 用來連接到監視伺服器的安全性模式。  
  
 1 = Windows 驗證。  
  
 0 = SQL Server 驗證。  
  
 *monitor_server_security_mode&lt*已**元**不能是 NULL。  
  
`[ @monitor_server_login = ] 'monitor_server_login'` 是用來存取監視伺服器的使用者名稱。  
  
`[ @monitor_server_password = ] 'monitor_server_password'` 這是帳戶的用來存取監視伺服器密碼。  
  
`[ @backup_threshold = ] 'backup_threshold'` 是一段時間，以分鐘為單位，在之前的最後一個備份之後*threshold_alert*就會引發錯誤。 *backup_threshold*已**int**，預設值是 60 分鐘的時間。  
  
`[ @threshold_alert = ] 'threshold_alert'` 當超出備份臨界值時產生警示。 *threshold_alert*已**int**不能是 NULL。  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` 指定是否產生警示時*backup_threshold*超過。  
  
 1 = 已啟用。  
  
 0 = 已停用。  
  
 *threshold_alert_enabled*已**元**不能是 NULL。  
  
`[ @history_retention_period = ] 'history_retention_period'` 這是時間的以分鐘為單位中保留記錄長度。 *history_retention_period*已**int**。若未指定，則使用 14420。  
  
`[ @backup_compression = ] backup_compression_option` 指定是否要使用記錄傳送組態[備份壓縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)。 只有在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (或更新版本) 中才支援這個參數。  
  
 0 = 已停用。 永遠不會壓縮記錄備份。  
  
 1 = 已啟用。 一定會壓縮記錄備份。  
  
 2 = 使用的設定[檢視或設定 backup compression default 伺服器組態選項](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。 這是預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 **sp_change_log_shipping_primary_database**必須從執行**主要**主要伺服器上的資料庫。 這個預存程序會執行下列動作：  
  
1.  在設定的變更**log_shipping_primary_database**記錄，如有必要。  
  
2.  變更在本機的資料錄**log_shipping_monitor_primary**主要伺服器上使用提供的引數，如有必要。  
  
3.  如果監視伺服器不是從主要伺服器，變更會記錄在**log_shipping_monitor_primary**監視伺服器使用提供的引數，如有必要。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可以執行此程序。  
  
## <a name="examples"></a>範例  
 此範例說明如何使用**sp_change_log_shipping_primary_database**來更新主要資料庫與相關聯的設定[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。  
  
```  
EXEC master.dbo.sp_change_log_shipping_primary_database   
 @database = N'AdventureWorks'   
, @backup_directory = N'c:\LogShipping'   
, @backup_share = N'\\tribeca\LogShipping'   
, @backup_retention_period = 1440   
, @backup_threshold = 60   
, @threshold_alert = 0   
, @threshold_alert_enabled = 1   
, @history_retention_period = 1440   
,@monitor_server_security_mode = 1  
,@backup_compression = 1;  
```  
  
## <a name="see-also"></a>另請參閱  
 [關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [log_shipping_primary_databases &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)  
  
  
