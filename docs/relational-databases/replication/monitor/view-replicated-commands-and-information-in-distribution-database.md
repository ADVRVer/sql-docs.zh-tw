---
title: 檢視散發資料庫中複寫的命令和資訊 | Microsoft 文件
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e13c7fe6f0ed19b218ba0a229238050c2d6f4bdf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="view-replicated-commands-and-information-in-distribution-database"></a>檢視散發資料庫中複寫的命令和資訊
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  在使用異動複寫時，交易命令在傳播到所有「訂閱者」之前或在「訂閱者」端的「散發代理程式」 您可以使用複寫預存程序，以程式設計的方式檢視散發資料庫中的這些暫止命令。 如需詳細資訊，請參閱[複寫預存程序 &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)。  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>若要在散發資料庫中檢視從所有交易式發行集所複寫的命令  
  
1.  在散發資料庫的「散發者」端，執行 [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md)。  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>若要在散發資料庫中，檢視從使用異動複寫所發行之特定發行項或特定資料庫複寫的命令  
  
1.  (選擇性) 在發行集資料庫的「發行者」端，執行 [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)。 指定 **@publication** 和 **@article**＞。 請注意結果集中 **article id** 的值。  
  
2.  在散發資料庫的「散發者」端，執行 [sp_browsereplcmds](../../../relational-databases/system-stored-procedures/sp-browsereplcmds-transact-sql.md)。 (選擇性) 針對 **@article_id**＞。 (選擇性) 針對 **@publisher_database_id**指定發行集資料庫的識別碼，此識別碼可從 **sys.databases** 目錄檢視中的 [database_id](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 資料行取得。  
  
## <a name="see-also"></a>另請參閱  
 [以程式設計方式監視複寫](../../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
