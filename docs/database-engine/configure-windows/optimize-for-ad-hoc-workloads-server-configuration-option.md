---
title: "針對特定工作負載最佳化伺服器組態選項 | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 207ca8c64cd20e8e98093960bd68ad23b770ea24
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a>針對特定工作負載最佳化伺服器組態選項
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **optimize for ad hoc workloads** 選項是用來針對包含許多使用一次特定批次的工作負載，改善計畫快取的效率。 如果這個選項設定為 1， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 就會在首次編譯批次時，將小型已編譯計畫虛設常式 (而非完整的已編譯計畫) 儲存在計畫快取中。 這會透過避免計畫快取填滿不重複使用的已編譯計畫，協助減輕記憶體不足的壓力。  
  
 已編譯計畫虛設常式可讓 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 辨識出這個特定批次先前已經編譯，但是只儲存已編譯計畫虛設常式，如此再次叫用 (編譯或執行) 這個批次時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 就會編譯此批次、從計畫快取中移除已編譯計畫虛設常式，並且將完整的已編譯計畫加入至計畫快取。 
  
 已編譯計畫虛設常式是 sys.dm_exec_cached_plans 目錄檢視所顯示的其中一個 cacheobjtype。 它具有唯一的 SQL 控制代碼和計畫控制代碼。 已編譯計畫虛設常式沒有相關聯的執行計畫，因此查詢計畫控制代碼將不會傳回 XML 執行程序表。  
  
 [追蹤旗標 8032](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 會將快取限制參數還原為 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] RTM 設定，這項設定通常會允許使用更大的快取。 當經常重複使用的快取項目無法納入快取中，以及 [針對特定工作負載最佳化伺服器組態選項] 無法解決計畫快取的問題時，請使用這項設定。  
  
> [!WARNING]  
>  如果大型快取為其他記憶體取用者 (例如緩衝集區) 提供較少的記憶體，追蹤旗標 8032 可能會導致效能降低。  

## <a name="recommendations"></a>建議
如果一次性計畫的數目佔用 OLTP 伺服器中絕大部分的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 記憶體，且這些計畫為特定計畫，請使用此伺服器選項來降低這些物件的記憶體使用量。
若要找到一次性快取計畫的數目，請執行下列查詢：

```t-sql
SELECT objtype, cacheobjtype, 
  AVG(usecounts) AS Avg_UseCount, 
  SUM(refcounts) AS AllRefObjects, 
  SUM(CAST(size_in_bytes AS bigint))/1024/1024 AS Size_MB
FROM sys.dm_exec_cached_plans
WHERE objtype = 'Adhoc' AND usecounts = 1
GROUP BY objtype, cacheobjtype;
```

> [!IMPORTANT]
> 將 **optimize for ad hoc workloads** 設定為 1 只會影響新的計畫。已經存在計畫快取中的計畫則不會受到影響。
> 若要立即影響已快取的查詢計畫，需要使用 [ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) 清除計畫快取，或必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。

## <a name="see-also"></a>另請參閱  
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
