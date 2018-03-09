---
title: "backupfile (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- backupfile
- backupfile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- file backups [SQL Server], backupfile system table
- backupfile system table
ms.assetid: f1a7fc0a-f4b4-47eb-9138-eebf930dc9ac
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 84b26ca09b8cd537ed40f0af8844f3f0c7627c86
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="backupfile-transact-sql"></a>backupfile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對資料庫的每個資料或記錄檔，各包含一個資料列。 這些資料行用來描述取得備份時的檔案組態。 是否在備份中包含的檔案由**is_present**資料行。 這份資料表儲存在**msdb**資料庫。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|備份組所在檔案的唯一識別碼。 參考**backupset （backup_set_id)**。|  
|**first_family_number**|**tinyint**|這個備份檔所在的第一個媒體的家族號碼。 可以是 NULL。|  
|**first_media_number**|**smallint**|這個備份檔所在的第一個媒體的媒體號碼。 可以是 NULL。|  
|**filegroup_name**|**nvarchar(128)**|備份的資料庫檔所在之檔案群組的名稱。 可以是 NULL。|  
|**page_size**|**int**|頁面的大小 (以位元組為單位)。|  
|**file_number**|**numeric(10,0)**|在資料庫內的唯一檔案識別碼 (對應至**sys.database_files**。**file_id**)。|  
|**backed_up_page_count**|**numeric(10,0)**|備份的頁數。 可以是 NULL。|  
|**file_type**|**char(1)**|這是備份的檔案，它有下列幾種：<br /><br /> D = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料檔。<br /><br /> L = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄檔。<br /><br /> F = 全文檢索目錄。<br /><br /> 可以是 NULL。|  
|**source_file_block_size**|**numeric(10,0)**|備份資料或記錄檔時，原始資料或記錄檔所在的裝置。 可以是 NULL。|  
|**file_size**|**numeric(20,0)**|備份檔案的長度 (以位元組為單位)。 可以是 NULL。|  
|**logical_name**|**nvarchar(128)**|備份檔案的邏輯名稱。 可以是 NULL。|  
|**physical_drive**|**nvarchar(260)**|實體磁碟機或分割區名稱。 可以是 NULL。|  
|**physical_name**|**nvarchar(260)**|實體 (作業系統) 檔案名稱的其餘部份。 可以是 NULL。|  
|**狀態**|**tinyint**|這是檔案的狀態，它有下列幾種：<br /><br /> 0 = ONLINE <br /><br /> 1 = RESTORING<br /><br /> 2 = RECOVERING<br /><br /> 3 = RECOVERY PENDING<br /><br /> 4 = SUSPECT<br /><br /> 6 = OFFLINE<br /><br /> 7 = DEFUNCT<br /><br /> 8 = 卸除<br /><br /> 注意： 的值是 5 略過，讓這些值對應至資料庫狀態的值。|  
|**state_desc**|**nvarchar(64)**|這是檔案狀態的描述，它有下列幾種：<br /><br /> ONLINE RESTORING <br /><br /> RECOVERING<br /><br /> RECOVERY_PENDING<br /><br /> SUSPECT OFFLINE DEFUNCT|  
|**create_lsn**|**numeric(25,0)**|建立檔案的記錄序號。|  
|**drop_lsn**|**numeric(25,0)**|卸除檔案的記錄序號。 可以是 NULL。<br /><br /> 如果檔案尚未卸除，這個值就是 NULL。|  
|**file_guid**|**uniqueidentifier**|檔案的唯一識別碼。|  
|**read_only_lsn**|**numeric(25,0)**|包含從讀寫改成唯讀 (最近的變更) 的檔案之檔案群組所在的記錄序號。 可以是 NULL。|  
|**read_write_lsn**|**numeric(25,0)**|包含從唯讀改成讀寫 (最近的變更) 的檔案之檔案群組所在的記錄序號。 可以是 NULL。|  
|**differential_base_lsn**|**numeric(25,0)**|差異備份的基底 LSN。 差異備份包含僅記錄序號的資料範圍數目等於或大於**differential_base_lsn**。<br /><br /> 如果是其他備份類型，這個值就是 NULL。|  
|**differential_base_guid**|**uniqueidentifier**|如果是差異備份，便是形成檔案差異基底之最近資料備份的唯一識別碼；如果是 NULL 值，就表示檔案已併入差異備份中，但它是在建立基底之後才加入。<br /><br /> 如果是其他備份類型，這個值就是 NULL。|  
|**backup_size**|**numeric(20,0)**|這個檔案的備份大小 (以位元組為單位)。|  
|**filegroup_guid**|**uniqueidentifier**|檔案群組的識別碼。 若要在 backupfilegroup 資料表中尋找的檔案群組資訊，請使用**filegroup_guid**與**backup_set_id**。|  
|**is_readonly**|**bit**|1 = 檔案唯讀。|  
|**is_present**|**bit**|1 = 檔案包含在備份組中。|  
  
## <a name="remarks"></a>備註  
 RESTORE VERIFYONLY FROM *backup_device* WITH LOADHISTORY 會的資料行**backupmediaset**媒體集標頭的適當值的資料表。  
  
 若要減少此資料表和其他備份和記錄資料表中的資料列數目，請執行[sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [備份及還原資料表 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [系統資料表 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
