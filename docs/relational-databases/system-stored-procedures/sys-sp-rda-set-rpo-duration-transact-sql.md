---
title: sys.databases sp_rda_set_rpo_duration （Transact-sql） |Microsoft Docs
description: 瞭解 sys.databases sp_rda_set_rpo_duration。 使用此預存程式，設定 SQL Server 保留在臨時表中的已遷移資料時數。
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e3dde1d29cd72ce62a306d43d40c067ec140007d
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243337"
---
# <a name="syssp_rda_set_rpo_duration-transact-sql"></a>sys.databases sp_rda_set_rpo_duration （Transact-sql）
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  設定 SQL Server 保留在臨時表中的已遷移資料時數，以協助確保在需要還原時間點時，遠端 Azure 資料庫的完整還原。    
    
 如需詳細資訊，請參閱[Stretch Database 會暫時保留遷移的資料列，以降低 Azure 資料遺失的風險](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)。  
   
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>語法    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>引數    
 [ @duration_hrs =] *duration_hrs*    
 這是您想要 SQL Server 保留給目前已啟用 Stretch 之資料庫的已遷移資料的時數（非 null 整數值）。 預設值和最小值為8小時。    
 
 > [!NOTE]
 > 較高的值在 SQL Server 上需要更多的儲存空間。
    
## <a name="permissions"></a>權限    
 需要 db_owner 許可權。    
    
## <a name="remarks"></a>備註    
 藉由執行[sys.databases sp_rda_get_rpo_duration &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)取得目前的值。    
    
## <a name="see-also"></a>另請參閱    
 [sp_rda_get_rpo_duration &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [還原已啟用 Stretch 的資料庫（Stretch Database）](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
