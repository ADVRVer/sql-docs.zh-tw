---
title: 設定 remote data archive 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b5817b5a-f39a-4faf-b11e-a47b54fd9f32
author: rothja
ms.author: jroth
ms.openlocfilehash: fda2594b2dc61a78eb5900ef6d1b735dac5b44e4
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "68012335"
---
# <a name="configure-the-remote-data-archive-server-configuration-option"></a>設定遠端資料封存伺服器組態選項
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  使用 [遠端資料封存]  選項，指定是否在伺服器上啟用資料庫和資料表進行「延伸」。 如需詳細資訊，請參閱 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)。  
  
 [遠端資料封存]  選項可以有下列值。  
  
|值|描述|  
|-----------|-----------------|  
|0|無法在伺服器上啟用資料庫和資料表進行「延伸」。|  
|1|可以在伺服器上啟用資料庫和資料表進行「延伸」。|  
  
 執行 **sp_configure** 以設定 [遠端資料封存]  選項的值需要 sysadmin 或 serveradmin 權限。  
  
## <a name="example"></a>範例  
 下列範例首先顯示 [遠端資料封存]  選項的目前設定。 此範例會將 [遠端資料封存]  選項的值設為 1 來啟用它。  
  
```  
EXEC sp_configure 'remote data archive';  
GO  
EXEC sp_configure 'remote data archive' , '1';  
GO  
RECONFIGURE;  
GO  
```  
  
 若要停用此選項，請將值設定為 0。  
  
## <a name="see-also"></a>另請參閱  
 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
