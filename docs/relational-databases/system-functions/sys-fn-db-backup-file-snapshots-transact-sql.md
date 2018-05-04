---
title: sys.fn_db_backup_file_snapshots (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a6a4fc88e778b7384487aab34203341a61ef2ed8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>sys.fn_db_backup_file_snapshots (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  傳回資料庫檔案與相關聯的 Azure 快照集。 如果找不到指定的資料庫或資料庫檔案不會儲存在 Microsoft Azure Blob 儲存體服務，則會不傳回任何資料列。 使用這個系統函數搭配**sys.sp_delete_backup_file_snapshot**系統預存程序來找出並刪除孤立的備份快照集。 如需詳細資訊，請參閱 [Azure 中資料庫檔案的檔案快照集備份](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>引數  
 *Database_name*  
 正在查詢之資料庫的名稱。 如果是 NULL，此函式會執行在目前的資料庫範圍內。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|file_id|**int**|資料庫的檔案識別碼。 不可為 Null。|  
|snapshot_time|**nvarchar(260)**|REST API 會傳回快照集，因為它的時間戳記。 如果沒有快照集存在，則傳回 NULL。|  
|snapshot_url|**nvarchar(360)**|檔案快照集的完整 URL。 傳回 NULL，如果沒有快照集存在。|  
  
## <a name="permissions"></a>Permissions  
 需要資料庫的 VIEW DATABASE STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [sp_delete_backup_file_snapshot &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
