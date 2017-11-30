---
title: "sys.fn_db_backup_file_snapshots (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/03/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30988d44e03a40ffcb8317a603b99633c21c8068
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
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
 *資料庫名稱*  
 正在查詢之資料庫的名稱。 如果是 NULL，此函式會執行在目前的資料庫範圍內。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|file_id|**int**|資料庫的檔案識別碼。 不可為 Null。|  
|snapshot_time|**nvarchar （260)**|REST API 會傳回快照集，因為它的時間戳記。 如果沒有快照集存在，則傳回 NULL。|  
|snapshot_url|**nvarchar(360)**|檔案快照集的完整 URL。 傳回 NULL，如果沒有快照集存在。|  
  
## <a name="permissions"></a>Permissions  
 需要資料庫的 VIEW DATABASE STATE 權限。  
  
## <a name="see-also"></a>請參閱  
 [sp_delete_backup_file_snapshot &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
