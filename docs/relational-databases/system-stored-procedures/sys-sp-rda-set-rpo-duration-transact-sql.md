---
title: sys.sp_rda_set_rpo_duration (Transact-SQL) | Microsoft Docs
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f46dd0bbedfebec5e21800b477a23d664446bf24
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982950"
---
# <a name="syssprdasetrpoduration-transact-sql"></a>sys.sp_rda_set_rpo_duration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  設定的 SQL Server 會保留已移轉資料的時數，以協助確保完整還原遠端的 Azure 資料庫中，如果需要還原時間點的臨時資料表中。    
    
 如需詳細資訊，請參閱 < [Stretch Database 透過暫時保留已移轉的資料列來減少您的 Azure 資料的資料遺失的風險](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)。  
   
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>語法    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>引數    
 [ @duration_hrs = ] *duration_hrs*    
 是的小時數 （非 null 的整數值） 的移轉的資料，您想要保留的 SQL Server 目前已啟用 Stretch 的資料庫。 預設值和最小值是 8 小時。    
 
 > [!NOTE]
 > 較高的值需要 SQL Server 上的更多儲存空間。
    
## <a name="permissions"></a>Permissions    
 需要 db_owner 權限。    
    
## <a name="remarks"></a>備註    
 取得目前的值，藉由執行[sys.sp_rda_get_rpo_duration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)。    
    
## <a name="see-also"></a>另請參閱    
 [sys.sp_rda_get_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [還原已啟用 Stretch 的資料庫 (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
