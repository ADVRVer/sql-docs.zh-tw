---
title: sp_replrestart (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replrestart_TSQL
- sp_replrestart
helpviewer_keywords:
- sp_replrestart
ms.assetid: 111b3dbf-92f8-4670-b156-1468c63e4fc1
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 905726825618d1412528a0c3f543bd7886213e95
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="spreplrestart-transact-sql"></a>sp_replrestart (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在備份與還原期間，供異動複寫使用，以便同步處理散發者端的複寫資料和發行者端的資料。 這個預存程序執行於發行集資料庫的發行者端。  
  
> [!IMPORTANT]  
>  **sp_replrestart**是一個內部複寫預存程序，應該只用於 > 主題中的指示，異動複寫拓撲中還原資料庫發行時[Backing Up and Restoring 的策略快照式和異動複寫](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_replrestart  
```  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_replrestart**可在散發者端的最高的記錄序號 (lsn) 值符合在 「 發行者 」 的最大 LSN 值。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_replrestart**。  
  
## <a name="see-also"></a>另請參閱  
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
