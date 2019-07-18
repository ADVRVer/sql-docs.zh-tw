---
title: sys.fn_db_backup_file_snapshots & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 06/03/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 45010ff2-219f-4086-9ea4-016a6c17cddd
author: rothja
ms.author: jroth
ms.openlocfilehash: 5159b72cb91cfdcf21129c6216cab4cf0e8d4dea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68120265"
---
# <a name="sysfndbbackupfilesnapshots-transact-sql"></a>sys.fn_db_backup_file_snapshots & Amp;#40;transact-SQL&AMP;#41;
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  傳回與資料庫檔案相關聯的 Azure 快照集。 如果找不到指定的資料庫或資料庫檔案不會儲存在 Microsoft Azure Blob 儲存體服務，則會不傳回任何資料列。 搭配使用這個系統函數**sys.sp_delete_backup_file_snapshot**系統預存程序來找出並刪除孤立的備份快照集。 如需詳細資訊，請參閱 [Azure 中資料庫檔案的檔案快照集備份](../../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.fn_db_backup_file_snapshots   
   [ ( database_name ) ]  
```  
  
## <a name="arguments"></a>引數  
 *Database_name*  
 正在查詢之資料庫的名稱。 如果是 NULL，此函式會執行目前的資料庫範圍內。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|file_id|**int**|資料庫的檔案識別碼。 不可為 Null。|  
|snapshot_time|**nvarchar(260)**|REST API 所傳回的時間戳記，因為它的快照集。 如果沒有快照集存在，則傳回 NULL。|  
|snapshot_url|**nvarchar(360)**|檔案快照集完整 URL。 傳回 NULL，如果沒有快照集存在。|  
  
## <a name="permissions"></a>Permissions  
 需要資料庫的 VIEW DATABASE STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [sp_delete_backup_file_snapshot &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup-file-snapshot.md)   
 [sp_delete_backup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/snapshot-backup-sp-delete-backup.md)  
  
  
