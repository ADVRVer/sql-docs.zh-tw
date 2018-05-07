---
title: syssubscriptions (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- syssubscriptions_TSQL
- syssubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syssubscriptions system table
ms.assetid: 106c1707-e0e0-49b4-ba50-25380c40fab2
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 620cc0de62221ad784c4e38dbf51aba39eea5047
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="syssubscriptions-transact-sql"></a>syssubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對資料庫中的每項訂閱，各包含一個資料列。 這份資料表儲存在發行集資料庫中。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|發行項的唯一識別碼。|  
|**srvid**|**smallint**|訂閱者的伺服器識別碼。|  
|**dest_db**|**sysname**|目的地資料庫的名稱。|  
|**status**|**tinyint**|訂閱的狀態：<br /><br /> **0** = 非使用中。<br /><br /> **1** = 訂閱。<br /><br /> **2** = 使用。|  
|**sync_type**|**tinyint**|初始同步處理的類型：<br /><br /> **1** = 自動。<br /><br /> **2** = 無|  
|**login_name**|**sysname**|用來加入訂閱的登入名稱。|  
|**subscription_type**|**int**|訂閱的類型：<br /><br /> 0 = 發送 - 散發代理程式執行於散發者端。<br /><br /> 1 = 提取 - 散發代理程式執行於訂閱者端。|  
|**distribution_jobid**|**binary(16)**|散發代理程式的作業識別碼。|  
|**timestamp**|**timestamp**|時間戳記。|  
|**update_mode**|**tinyint**|更新模式：<br /><br /> **0** = 唯讀。<br /><br /> **1** = 立即更新。|  
|**loopback_detection**|**bit**|適用於雙向異動複寫拓撲中的訂閱。 回送偵測會判斷散發代理程式是否將起源於訂閱者端的交易傳回給訂閱者：<br /><br /> **0** = 傳回。<br /><br /> **1** = 不傳回。|  
|**queued_reinit**|**bit**|指定發行項是否標示初始化或重新初始化。 值為**1**指定標示初始化或重新初始化訂閱的發行項。|  
|**nosync_type**|**tinyint**|訂閱初始化的類型：<br /><br /> **0** = 自動 （快照集）<br /><br /> **1** = 僅支援複寫<br /><br /> **2** = 以備份初始化<br /><br /> **3** = 從記錄序號 (LSN) 初始化<br /><br /> 如需詳細資訊，請參閱**@sync_type**參數[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)。|  
|**srvname**|**sysname**|訂閱者的名稱。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
