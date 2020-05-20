---
title: syssubscriptions （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- syssubscriptions_TSQL
- syssubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syssubscriptions system table
ms.assetid: 106c1707-e0e0-49b4-ba50-25380c40fab2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0a7fa169bef5d105889bf9035155fef97505f723
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82812101"
---
# <a name="syssubscriptions-transact-sql"></a>syssubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對資料庫中的每項訂閱，各包含一個資料列。 這份資料表儲存在發行集資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|發行項的唯一識別碼。|  
|**srvid**|**smallint**|訂閱者的伺服器識別碼。|  
|**dest_db**|**sysname**|目的地資料庫的名稱。|  
|**status**|**tinyint**|訂閱的狀態：<br /><br /> **0** = 非使用中。<br /><br /> **1** = 已訂閱。<br /><br /> **2** = 使用中。|  
|**sync_type**|**tinyint**|初始同步處理的類型：<br /><br /> **1** = 自動。<br /><br /> **2** = 無|  
|**login_name**|**sysname**|用來加入訂閱的登入名稱。|  
|**subscription_type**|**int**|訂閱的類型：<br /><br /> 0 = 發送 - 散發代理程式執行於散發者端。<br /><br /> 1 = 提取 - 散發代理程式執行於訂閱者端。|  
|**distribution_jobid**|**binary(16)**|散發代理程式的作業識別碼。|  
|**timestamp**|**timestamp**|時間戳記。|  
|**update_mode**|**tinyint**|更新模式：<br /><br /> **0** = 唯讀。<br /><br /> **1** = 立即更新。|  
|**loopback_detection**|**bit**|適用於雙向異動複寫拓撲中的訂閱。 回送偵測會判斷散發代理程式是否將起源於訂閱者端的交易傳回給訂閱者：<br /><br /> **0** = 傳回。<br /><br /> **1** = 不傳回。|  
|**queued_reinit**|**bit**|指定發行項是否標示初始化或重新初始化。 值為**1**時，表示訂閱的發行項已標示為要初始化或重新初始化。|  
|**nosync_type**|**tinyint**|訂閱初始化的類型：<br /><br /> **0** = 自動（快照集）<br /><br /> **1** = 僅複寫支援<br /><br /> **2** = 使用備份進行初始化<br /><br /> **3** = 從記錄序號初始化（LSN）<br /><br /> 如需詳細資訊，請參閱[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)的** \@ sync_type**參數。|  
|**srvname**|**sysname**|訂閱者的名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
