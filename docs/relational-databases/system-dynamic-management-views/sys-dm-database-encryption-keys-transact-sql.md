---
title: sys.dm_database_encryption_keys (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_database_encryption_keys
- sys.dm_database_encryption_keys_TSQL
- dm_database_encryption_keys
- dm_database_encryption_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_database_encryption_keys dynamic management view
ms.assetid: 56fee8f3-06eb-4fff-969e-abeaa0c4b8e4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c041ea8aff23a3b601695236681fda3081def1fa
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494072"
---
# <a name="sysdmdatabaseencryptionkeys-transact-sql"></a>sys.dm_database_encryption_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回關於資料庫加密狀態及其相關聯之資料庫加密金鑰的資訊。 如需資料庫加密的詳細資訊，請參閱[透明資料加密 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)。  
 
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|database_id|**int**|資料庫的識別碼。|  
|encryption_state|**int**|指出資料庫已加密或未加密。<br /><br /> 0 = 沒有資料庫加密金鑰存在，未加密<br /><br /> 1 = 未加密<br /><br /> 2 = 加密進行中<br /><br /> 3 = 已加密<br /><br /> 4 = 金鑰變更進行中<br /><br /> 5 = 解密進行中<br /><br /> 6 = 保護變更進行中 (正在變更用於加密資料庫加密金鑰的憑證或非對稱金鑰)。|  
|create_date|**datetime**|將日期顯示建立加密金鑰 （以 utc 表示）。|  
|regenerate_date|**datetime**|顯示的日期 （於 UTC) 已重新產生加密金鑰。|  
|modify_date|**datetime**|顯示的日期 （以 utc 表示） 修改加密金鑰。|  
|set_date|**datetime**|顯示的日期 （以 utc 格式） 的加密金鑰已套用至資料庫。|  
|opened_date|**datetime**|顯示上次開啟資料庫索引鍵 （以 utc 表示）。|  
|key_algorithm|**nvarchar(32)**|顯示用於金鑰的演算法。|  
|key_length|**int**|顯示金鑰的長度。|  
|encryptor_thumbprint|**varbinary(20)**|顯示加密程式的指模。|  
|encryptor_type|**nvarchar(32)**|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [目前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658))。<br /><br /> 描述加密程式。|  
|percent_complete|**real**|資料庫加密狀態變更的完成百分比。 如果沒有狀態變更，這將會是 0。|
|encryption_state_desc|**nvarchar(32)**|**適用於**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]和更新版本。<br><br> 指出資料庫是否已加密，或未加密的字串。<br><br>無<br><br>未加密<br><br>加密<br><br>DECRYPTION_IN_PROGRESS<br><br>ENCRYPTION_IN_PROGRESS<br><br>KEY_CHANGE_IN_PROGRESS<br><br>PROTECTION_CHANGE_IN_PROGRESS|
|encryption_scan_state|**int**|**適用於**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]和更新版本。<br><br>表示加密掃描的目前狀態。 <br><br>0 = 否在起始掃描，未啟用 TDE<br><br>1 = 掃描正在進行中。<br><br>2 = 掃描正在進行中，但已暫停也無妨，使用者可以繼續。<br><br>3 = 已順利完成掃描，啟用 TDE 加密已完成。<br><br>4 = 掃描已中止，因為某些原因，則需要手動操作。 如需更多協助，請連絡 Microsoft 支援服務。|
|encryption_scan_state_desc|**nvarchar(32)**|**適用於**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]和更新版本。<br><br>字串，表示加密掃描的目前狀態。<br><br> 無<br><br>RUNNING<br><br>SUSPENDED<br><br>完成<br><br>ABORTED|
|encryption_scan_modify_date|**datetime**|**適用於**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]和更新版本。<br><br> 將日期顯示上次修改加密掃描狀態 （以 utc 表示）。|
  
## <a name="permissions"></a>Permissions

在  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在  [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`資料庫的權限。   

## <a name="see-also"></a>另請參閱  

 [安全性相關的動態管理檢視和函數 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)   
 [透明資料加密 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)   
 [SQL Server 加密](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [SQL Server 和資料庫加密金鑰 &#40;Database Engine&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-encryption-key-transact-sql.md)   
 [ALTER DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-encryption-key-transact-sql.md)   
 [DROP DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-encryption-key-transact-sql.md)  
  
  
