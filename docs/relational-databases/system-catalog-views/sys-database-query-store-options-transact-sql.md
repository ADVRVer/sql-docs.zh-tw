---
title: sys.database_query_store_options & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ca46886ab9648142bb79863dad0818033c2ce0a1
ms.sourcegitcommit: 3d50caa30681bf384f5628b1dd3e06e24fc910cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54838105"
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>sys.database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  傳回這個資料庫的查詢存放區選項。  
  
**適用於**：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|表示查詢存放區，由使用者明確設定的所需的作業模式。<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(60)**|文字的查詢存放區的所需的作業模式的詳細描述：<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|表示查詢存放區的作業模式。 所需的狀態所需的使用者清單中，除了實際狀態可能是處於錯誤狀態。<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = 錯誤|  
|**actual_state_desc**|**nvarchar(60)**|查詢存放區的實際作業模式的文字描述。<br />OFF<br />READ_ONLY<br />READ_WRITE<br />error<br /><br /> 當實際狀態是不同於預期的狀態，則需要有情況：<br /><br /> 即使使用者已指定讀寫，可能會在唯讀模式下運作查詢存放區。 例如，可能會發生如果資料庫處於唯讀模式，或查詢存放區大小超過配額。<br /><br /> 極少，查詢存放區最後可能處於錯誤狀態因為發生內部錯誤。 如果發生這種情況，無法執行復原查詢存放區**sp_query_store_consistency_check**預存程序內受影響的資料庫。|  
|**readonly_reason**|**int**|當**desired_state_desc**是 READ_WRITE 和**actual_state_desc**是 READ_ONLY **readonly_reason**傳回位元對應來表示查詢存放區處於為何唯讀模式。<br /><br /> 1-資料庫處於唯讀模式<br /><br /> 2-資料庫處於單一使用者模式<br /><br /> 4-資料庫處於緊急模式<br /><br /> 8-資料庫是次要複本 (適用於 Always On 和 Azure[!INCLUDE[ssSDS](../../includes/sssds-md.md)]異地複寫)。 這個值可以有效地觀察到只有**讀取**次要複本<br /><br /> 65536-查詢存放區已達到的 MAX_STORAGE_SIZE_MB 選項所設定的大小限制。<br /><br /> 131072 查詢存放區中不同的陳述式的-數目已達到內部記憶體限制。 建議您移除您不需要的查詢，或升級至較高的服務層，以便傳送至讀寫模式的查詢存放區。<br />只適用於 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]。<br /><br /> 262144 大小的記憶體等候保存在磁碟上的項目已達到內部記憶體限制。 只有在記憶體中的項目會保存在磁碟上之前，暫時查詢存放區將處於唯讀模式。 <br />只適用於 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]。<br /><br />524288 資料庫已達到磁碟大小限制。 查詢存放區資料庫的一部分使用者，因此如果沒有更多可用空間的資料庫，表示查詢存放區無法進一步成長就淪陷了。<br />只適用於 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]。 <br /> <br /> 若要切換的查詢存放區作業模式後，要讀寫，請參閱**確認查詢存放區會持續收集查詢資料**一節[執行查詢存放區的最佳作法](../../relational-databases/performance/best-practice-with-the-query-store.md)。|  
|**current_storage_size_mb**|**bigint**|查詢存放區的大小以 mb 為單位的磁碟上。|  
|**flush_interval_seconds**|**bigint**|定義的規則排清的查詢存放區資料到磁碟的期限。 預設值為 900 （15 分鐘）。<br /><br /> 藉由變更`ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)`陳述式。|  
|**interval_length_minutes**|**bigint**|統計資料彙總間隔。 不允許任意值。 您可以使用下列其中一項：1、 5、 10、 15、 30、 60 和 1440年分鐘。 預設值為 60 分鐘。|  
|**max_storage_size_mb**|**bigint**|查詢存放區的最大磁碟大小。 預設值為 100 MB。<br />針對 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium 版本預設值為 1Gb，而針對 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic 版本預設值為 10Mb。<br /><br /> 藉由變更`ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)`陳述式。|  
|**stale_query_threshold_days**|**bigint**|查詢與任何原則設定會保留查詢存放區中的日數。 預設值為 30。 若要停用保留原則設為 0。<br />[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic 版的預設值為 7 天。<br /><br /> 藉由變更`ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )`陳述式。|  
|**max_plans_per_query**|**bigint**|限制預存的計劃的最大數目。 預設值為 200。 如果達到最大值時，查詢存放區會停止擷取新的計畫，該查詢。 設定為 0 會移除關於擷取之計畫的數目限制。<br /><br /> 藉由變更`ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)`陳述式。|  
|**query_capture_mode**|**smallint**|目前使用中的查詢擷取模式：<br /><br /> 1 = ALL-會擷取所有查詢。 這是預設組態值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 透過 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。<br /><br /> 2 = AUTO-擷取相關的查詢，根據執行計數和資源耗用量。 這是預設組態值[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。<br /><br /> 3 = 無-停止擷取新的查詢。 查詢存放區將會繼續收集已擷取查詢的編譯和執行階段統計資料。 請小心使用此設定，因為您可能會錯過擷取重要查詢。|  
|**query_capture_mode_desc**|**nvarchar(60)**|文字的查詢存放區的實際擷取模式的詳細描述：<br /><br /> 全部 (預設值[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> 自動 (預設值[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> 無|  
|**size_based_cleanup_mode**|**smallint**|控制當總資料量接近大小上限時，是否將自動啟用清除：<br /><br /> 0 = 關閉-不會自動啟用依據的清除的大小。<br /><br /> 1 = AUTO-大小的磁碟達到 90%時自動啟用依據的清除的大小**max_storage_size_mb**。 這是預設組態值。<br /><br />以大小為依據的清除會先移除成本最高和最舊的查詢。 它會在大約 80%的 max_storage_size_mb 停止。|  
|**size_based_cleanup_mode_desc**|**nvarchar(60)**|文字的查詢存放區的實際大小為基礎的清除模式的詳細描述：<br /><br /> OFF <br /><br /> 自動 （預設值）|  
|**wait_stats_capture_mode**|**smallint**|控制查詢存放區是否執行擷取的等候統計資料： <br /><br /> 0 = OFF <br /><br /> 1 = ON <br /> **適用於**： [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|
|**wait_stats_capture_mode_desc**|**nvarchar(60)**|實際的等待統計資料的擷取模式的文字描述： <br /><br /> OFF <br /><br /> （預設值）<br /> **適用於**： [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。| 
  
## <a name="permissions"></a>Permissions  
 需要**VIEW DATABASE STATE**權限。  
  
## <a name="see-also"></a>另請參閱  
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [相關檢視、函數與程序](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [查詢存放區預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
