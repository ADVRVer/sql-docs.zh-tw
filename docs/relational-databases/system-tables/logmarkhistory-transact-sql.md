---
title: logmarkhistory （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- logmarkhistory
- logmarkhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ef8a263edfb6902cd4f050cbe27b99062e5b5c20
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750141"
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  針對已認可的每個標示交易，各包含一個資料列。 此資料表會儲存在**msdb**資料庫中。  
  

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|發生標示的交易之本機資料庫。|  
|**mark_name**|**nvarchar(128)**|使用者提供的標示交易名稱。|  
|**description**|**nvarchar(255)**|使用者提供的標示交易描述。 可以是 NULL。|  
|**user_name**|**nvarchar(128)**|執行標示交易的資料庫使用者名稱。 可以是 NULL。|  
|**lsn**|**numeric(25,0)**|標示所在之交易記錄的記錄序號。|  
|**mark_time**|**datetime**|標示的交易之認可時間 (本機時間)。|  
  
## <a name="see-also"></a>另請參閱  
 [還原資料庫至標示的交易 &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [使用標示的異動以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [系統資料表 &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
