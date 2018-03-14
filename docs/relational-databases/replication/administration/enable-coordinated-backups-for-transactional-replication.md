---
title: "為異動複寫啟用協調備份 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f57b57282b7fff5fbfb3cae2e422ae218049d7d3
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="enable-coordinated-backups-for-transactional-replication"></a>為異動複寫啟用協調備份
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  在啟用異動複寫的資料庫時，可以指定所有的交易必須先備份，才能傳遞到散發資料庫。 也可以在散發資料庫上啟用協調備份，如此在傳播到「散發者」的交易進行備份之前，發行集資料庫的交易記錄都不會遭到截斷。 如需詳細資訊，請參閱 [備份與還原快照式和異動複寫的策略](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)。  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a>若要為使用異動複寫所發行的資料庫啟用協調備份  
  
1.  在發行者端，使用 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../../t-sql/functions/databasepropertyex-transact-sql.md) 函式傳回發行集資料庫的 **IsSyncWithBackup** 屬性。 如果函數傳回 **1**，則已經為發行的資料庫啟用協調備份。  
  
2.  如果步驟 1 中的函式傳回 **0**，則請在發行集資料庫的發行者端執行 [sp_replicationdboption &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)。 為 **@optname** 指定 **@optname**的值，而為 **@value** 指定 **@value**＞。  
  
    > [!NOTE]  
    >  如果將 **sync with backup** 選項變更為 **false**，則在記錄讀取器執行後或在一個間隔後 (如果記錄讀取器持續執行)，發行集資料庫的截斷點就會更新。 最大間隔是由 **–MessageInterval** 代理程式參數 (預設值為 30 秒) 控制。  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a>若要啟用散發資料庫的協調備份  
  
1.  在散發者端，使用 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../../t-sql/functions/databasepropertyex-transact-sql.md) 函式傳回散發資料庫的 **IsSyncWithBackup** 屬性。 如果函數傳回 **1**，則已經為散發資料庫啟用協調備份。  
  
2.  如果步驟 1 中的函式傳回 **0**，則請在散發資料庫的散發者端執行 [sp_replicationdboption &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)。 為 **@optname** 指定 **@optname** 的值，而為 **@value** 指定 **@value**＞。  
  
### <a name="to-disable-coordinated-backups"></a>若要停用協調備份  
  
1.  在發行集資料庫的發行者端或散發資料庫的散發者端，執行 [sp_replicationdboption &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)。 為 **@optname** 指定 **@optname** 的值，而為 **false** 指定 **@value**＞。  
  
  
