---
description: sp_clean_db_file_free_space (Transact-SQL)
title: sp_clean_db_file_free_space (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_clean_db_file_free_space
- sp_clean_db_file_free_space_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ghost records
- sp_clean_db_file_free_space
ms.assetid: 3eb53a67-969d-4cb8-9681-b1c8e6fd55b6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 834521f77db142d8aba63f5638df05bd83b64811
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486177"
---
# <a name="sp_clean_db_file_free_space-transact-sql"></a>sp_clean_db_file_free_space (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  移除資料庫頁面上因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中資料修改例行工作所留下的剩餘資訊。 sp_clean_db_file_free_space 只會清除資料庫的一個檔案中的所有頁面。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```syntaxsql  
sp_clean_db_file_free_space   
  [ @dbname = ] 'database_name'   
  , [ @fileid = ] 'file_number'   
  [ , [ @cleaning_delay = ] 'delay_in_seconds' ] [;]  
```  
  
## <a name="arguments"></a>引數  
 @dbname = '*database_name*'  
 這是要清除的資料庫名稱。 *dbname* 是 **sysname** ，不能是 Null。  
  
 @fileid = '*file_number*'  
 這是要清除的資料檔案識別碼。 *file_number* 是 **int** ，不能是 Null。  
  
 @cleaning_delay = '*delay_in_seconds*'  
 指定頁面清除之間的延遲間隔。 如此有助於減少對 I/O 系統的影響。 *delay_in_seconds* 是 **int** ，預設值是0。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
 資料表中的刪除作業或是造成資料列移動的更新作業可以立即釋放頁面上的空間，其方式是移除資料列的參考。 但是在某些情況下，此資料列可以當做準刪除記錄實際存留在資料頁上。 背景處理序會定期移除準刪除記錄。 回應查詢時，不會傳回這 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 項剩餘資料。 但是，在資料或備份檔案的實體安全性有風險的環境中，您可以使用 `sp_clean_db_file_free_space` 清除這些准刪除記錄。 若要一次對所有資料庫檔案執行此作業，請使用 [sp_clean_db_free_space (transact-sql) ](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md)。 
  
 執行 sp_clean_db_file_free_space 所需的時間長度取決於檔案的大小、可用的空間及磁碟的容量。 因為 `sp_clean_db_file_free_space` 執行可能會大幅影響 i/o 活動，所以我們建議您在平常的作業時間以外執行此程式。  
  
 在執行之前 `sp_clean_db_file_free_space` ，建議您先建立完整的資料庫備份。  
  
 相關的 [sp_clean_db_free_space](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md) 預存程式會清除資料庫中的所有檔案。  
  
## <a name="permissions"></a>權限  
 需要資料庫角色中的成員資格 `db_owner` 。  
  
## <a name="examples"></a>範例  
 下列範例會從 `AdventureWorks2012` 資料庫的主要資料檔中清除所有剩餘資訊。  
  
```sql  
USE master;  
GO  
EXEC sp_clean_db_file_free_space @dbname = N'AdventureWorks2012', @fileid = 1;  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的資料庫引擎預存程式 ](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [准刪除清除流程指南](../ghost-record-cleanup-process-guide.md)    
 [sp_clean_db_free_space (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-clean-db-free-space-transact-sql.md)
   
