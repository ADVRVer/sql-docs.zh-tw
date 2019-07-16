---
title: log_shipping_monitor_history_detail (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_history_detail_TSQL
- log_shipping_monitor_history_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_history_detail system table
ms.assetid: 7080c888-323b-4206-a1ab-e6c51f9e2579
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f0a304020b972b29d521bd32da3f98b8d3fdfc9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989999"
---
# <a name="logshippingmonitorhistorydetail-transact-sql"></a>log_shipping_monitor_history_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  儲存記錄傳送作業的記錄詳細資料。 這份資料表儲存在**msdb**資料庫。  
  
 主要伺服器和次要伺服器也會使用記錄和監視的相關資料表。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|用來備份的主要識別碼，或用來複製或還原的次要識別碼。|  
|**agent_type**|**tinyint**|記錄傳送作業的類型。<br /><br /> 0 = 備份。<br /><br /> 1 = 複製。<br /><br /> 2 = 還原。|  
|**session_id**|**int**|備份/複製/還原作業的工作階段識別碼。|  
|**database_name**|**sysname**|這項記錄的相關資料庫名稱。 主要資料庫會用於備份；次要資料庫會用於還原；而空白則會用於複製。|  
|**session_status**|**tinyint**|工作階段的狀態。<br /><br /> 0 = 啟動中。<br /><br /> 1 = 執行中。<br /><br /> 2 = 成功。<br /><br /> 3 = 錯誤。<br /><br /> 4 = 警告。|  
|**log_time**|**datetime**|建立記錄的日期和時間。|  
|**log_time_utc**|**datetime**|建立記錄的日期和時間，用國際標準時間 (UTC) 來表示。|  
|**message**|**nvarchar(max)**|訊息文字。|  
  
## <a name="remarks"></a>備註  
 這份資料表包含記錄傳送代理程式的記錄詳細資料。 若要識別代理程式工作階段，請使用 資料行**agent_id**， **agent_type**，並**session_id**。 若要查看代理程式工作階段的記錄詳細資料，請依排序**log_time**。  
  
 除了儲存在遠端監視伺服器，主要伺服器的相關資訊會儲存在主要伺服器上其**log_shipping_monitor_history_detail**資料表 」 和 「 次要資料庫的相關資訊伺服器也會儲存在次要伺服器上其**log_shipping_monitor_history_detail**資料表。  
  
## <a name="see-also"></a>另請參閱  
 [關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [系統資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [log_shipping_monitor_error_detail &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql.md)  
  
  
