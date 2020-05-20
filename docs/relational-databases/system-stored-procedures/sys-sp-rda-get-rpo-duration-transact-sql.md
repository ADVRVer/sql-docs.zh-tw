---
title: sys.databases sp_rda_get_rpo_duration （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_get_rpo_duration
- sys.sp_rda_get_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_get_rpo_duration stored procedure
ms.assetid: 35882067-3072-47ff-9024-ca453c0f49a7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d1e89e4901cf8e0bb5674038bfd8fe74bc637511
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82814747"
---
# <a name="syssp_rda_get_rpo_duration-transact-sql"></a>sys.databases sp_rda_get_rpo_duration （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  取得已遷移資料的時數，SQL Server 保留在臨時表中，以協助確保遠端 Azure 資料庫的完整還原（如果需要還原時間點）。 
  
  如需詳細資訊，請參閱[Stretch Database 會暫時保留遷移的資料列，以降低 Azure 資料遺失的風險](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)。  
    
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>語法    
    
```    
    
sp_rda_get_rpo_duration @durationinhours output    
    
```    
    
## <a name="output-parameter"></a>輸出參數    
 *\@durationinhours*    
  這是 SQL Server 保留目前已啟用 Stretch 之資料庫的已遷移資料的時數（非 null 整數值）。    
    
## <a name="permissions"></a>權限    
 需要 db_owner 許可權。    
    
## <a name="remarks"></a>備註    
 藉由執行[sys.databases sp_rda_set_rpo_duration &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)來變更值。    
    
## <a name="see-also"></a>另請參閱    
 [sp_rda_set_rpo_duration &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)     
 [還原已啟用 Stretch 的資料庫（Stretch Database）](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)    
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
