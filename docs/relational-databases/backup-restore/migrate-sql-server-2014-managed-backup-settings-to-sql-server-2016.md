---
title: "將 SQL Server 2014 Managed Backup 設定移轉到 SQL Server 2016 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae937ebb-24ff-4a33-be3c-8f85328dfc75
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6df945737348bf0f8e158b375d6af1ebcbfb6784
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="migrate-sql-server-2014-managed-backup-settings-to-sql-server-2016"></a>將 SQL Server 2014 管理的備份設定移轉到 SQL Server 2016
  本主題涵蓋當從 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 升級到 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 時， [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]的移轉考量。  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 中 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]的程序和基礎行為已變更。 下列章節將說明功能上的變更及其隱含式。  
  
## <a name="overview"></a>概觀  
 下表描述 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 與 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 之間的部分 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]主要功能差異。  
  
|區域|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|----------|---------------------------|---------------------------|  
|**命名空間：**|smart_admin|managed_backup|  
|**系統預存程序：**|sp_set_db_backup<br /><br /> sp_set_instance_backup|[managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)<br /><br /> [sp_backup_config_advanced](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)<br /><br /> [sp_backup_config_schedule](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)|  
|**安全性：**|SQL 認證使用 Microsoft Azure 儲存體帳戶和存取金鑰。|SQL 認證使用 Microsoft Azure 共用存取簽章 (SAS) 權杖。|  
|**基礎儲存體︰**|Microsoft Azure 儲存體使用分頁 Blob。|Microsoft Azure 儲存體使用區塊 Blob。|  
  
## <a name="benefits"></a>優點  
 使用 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]中新功能的好處有很多。  
  
-   區塊 Blob 的儲存成本較低。  
  
-   只要使用等量，您就可以儲存更大的備份 (12 TB 對比 1 TB 的分頁 Blob)。  
  
-   等量也可以改善大型資料庫的還原時間  
  
-   如需 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 中 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]的其他改進功能，請參閱 [SQL Server Managed Backup 到 Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)。  
  
## <a name="considerations"></a>考量  
 從 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]升級之後，請注意下列 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 考量︰  
  
-   先前所設定的任何 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 上之 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 資料庫仍將繼續使用 **上的** smart_admin [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]系統程序以及基礎行為。  
  
-   **上的任何新** 組態不支援 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] smart_admin [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]程序。 您必須使用新的 **managed_backup** 程序和功能。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Managed Backup to Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
