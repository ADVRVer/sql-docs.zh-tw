---
title: sys.dm_hadr_auto_page_repair (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_auto_page_repair_TSQL
- sys.dm_hadr_auto_page_repair
- sys.dm_hadr_auto_page_repair_TSQL
- dm_hadr_auto_page_repair
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- automatic page repair
- sys.dm_hadr_auto_page_repair dynamic management view
ms.assetid: d7840adf-4a1b-41ac-bc94-102c07ad1c79
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9d46e5ee0b350e7164c0dfec55666d4b6c8e34a7
ms.sourcegitcommit: 1510d9fce125e5b13e181f8e32d6f6fbe6e7c7fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55771324"
---
# <a name="sysdmhadrautopagerepair-transact-sql"></a>sys.dm_hadr_auto_page_repair (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  針對可用性複本上的任何可用性資料庫進行的每個自動修復頁面嘗試行為，各傳回一個資料列，該可用性複本是針對伺服器執行個體的任何可用性群組所裝載。 這個檢視包含在給定之主要或次要資料庫上進行最新自動修復頁面嘗試行為的資料列，而且每個資料庫最多 100 個資料列。 一旦資料庫到達上限時，下一個自動修復頁面嘗試行為的資料列就會取代其中一個現有的項目。
  
  下表定義各資料行的意義：  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|這個資料列所對應的資料庫識別碼。|  
|**file_id**|**int**|頁面所在之檔案的識別碼。|  
|**page_id**|**bigint**|檔案中頁面的識別碼。|  
|**error_type**|**int**|錯誤的類型。 其值可能是：<br /><br /> **-** 1 = 所有硬體 823 錯誤<br /><br /> 1 = 824 錯誤的總和檢查碼或損毀的頁 （例如，不正確的頁面識別碼） 以外的錯誤<br /><br /> 2 = 總和檢查碼錯誤<br /><br /> 3 = 頁面損毀|  
|**page_status**|**int**|修復頁面嘗試行為的狀態：<br /><br /> 2 = 已將夥伴的要求排入佇列。<br /><br /> 3 = 要求已傳送給夥伴。<br /><br /> 4 = 已成功修復分頁。<br /><br /> 5 = 在上一次嘗試時無法修復的頁面 / 自動修復頁面嘗試一次修復該頁面。|  
|**modification_time**|**datetime**|上次變更頁面狀態的時間。|  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>Permissions  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [自動修復頁面 &#40;可用性群組：資料庫鏡像&#41;](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [suspect_pages &#40;Transact-SQL&#41;](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [管理 suspect_pages 資料表 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  

