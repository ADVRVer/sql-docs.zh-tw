---
title: sys.databases dm_xtp_transaction_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_transaction_stats_TSQL
- dm_xtp_transaction_stats
- sys.dm_xtp_transaction_stats_TSQL
- sys.dm_xtp_transaction_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_transaction_stats dynamic management view
ms.assetid: 9389f48d-0de5-47bd-9821-4db8f04504e4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e272d66fef1a6426e13cc6ab8ea72d3912003d3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829004"
---
# <a name="sysdm_xtp_transaction_stats-transact-sql"></a>sys.dm_xtp_transaction_stats (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  報告自伺服器啟動後已執行之交易的統計資料。  
  
 如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|total_count|**bigint**|已在記憶體中 OLTP 資料庫引擎中執行之交易的總數。|  
|read_only_count|**bigint**|唯讀交易數目。|  
|total_aborts|**bigint**|已透過使用者或系統中止之交易的總數。|  
|user_aborts|**bigint**|由系統起始的中止數目。 例如，由於寫入衝突、驗證失敗或相依性失敗。|  
|validation_failures|**bigint**|因為驗證失敗，交易中止的次數。|  
|dependencies_taken|**bigint**|僅供內部使用。|  
|dependencies_failed|**bigint**|因為其相依的交易中止，此交易中止的次數。|  
|savepoint_create|**bigint**|所建立之儲存點的數目。 已針對每一個不可部分完成的區塊建立新儲存點。|  
|savepoint_rollbacks|**bigint**|前一個儲存點的回復數目。|  
|savepoint_refreshes|**bigint**|僅供內部使用。|  
|log_bytes_written|**bigint**|寫入記憶體中 OLTP 記錄檔記錄的總位元組數。|  
|log_IO_count|**bigint**|需要記錄 IO 之交易的總數。 僅考慮持久性資料表上的交易。|  
|phantom_scans_started|**bigint**|僅供內部使用。|  
|phatom_scans_retries|**bigint**|僅供內部使用。|  
|phantom_rows_touched|**bigint**|僅供內部使用。|  
|phantom_rows_expiring|**bigint**|僅供內部使用。|  
|phantom_rows_expired|**bigint**|僅供內部使用。|  
|phantom_rows_expired_removed|**bigint**|僅供內部使用。|  
|scans_started|**bigint**|僅供內部使用。|  
|scans_retried|**bigint**|僅供內部使用。|  
|rows_returned|**bigint**|僅供內部使用。|  
|rows_touched|**bigint**|僅供內部使用。|  
|rows_expiring|**bigint**|僅供內部使用。|  
|rows_expired|**bigint**|僅供內部使用。|  
|rows_expired_removed|**bigint**|僅供內部使用。|  
|rows_inserted|**bigint**|僅供內部使用。|  
|rows_updated|**bigint**|僅供內部使用。|  
|rows_deleted|**bigint**|僅供內部使用。|  
|write_conflicts|**bigint**|僅供內部使用。|  
|unique_constraint_violations|**bigint**|唯一條件約束違規的總數。|  
  
## <a name="permissions"></a>權限  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體最佳化的資料表動態管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
