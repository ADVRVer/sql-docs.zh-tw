---
description: 'managed_backup fn_get_parameter (Transact-sql) '
title: managed_backup fn_get_parameter (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_get_parameter_TSQL
- smart_admin.fn_get_parameter
- fn_get_parameter_TSQL
- fn_get_parameter
dev_langs:
- TSQL
helpviewer_keywords:
- fn_get_parameter
- smart_admin.fn_get_parameter
ms.assetid: ed94e54d-4516-4806-a8ce-f013d3a04122
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: da8c646cca92a5ef25fd12322fd8a6bd222a1c9e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419512"
---
# <a name="managed_backupfn_get_parameter-transact-sql"></a>managed_backup fn_get_parameter (Transact-sql) 
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  傳回內含 0、1 或更多資料列參數和值組的資料表。  
  
 使用此預存程序可檢閱 Smart Admin 的所有或特定組態設定。  
  
 如果從未設定過參數，該函數會傳回 0 個資料列。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```sql  
managed_backup.fn_get_parameter ('parameter_name' | '' | NULL )  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a> 引數  
 parameter_name  
 參數的名稱。 parameter_name 是 **NVARCHAR (128) **。 如果將 NULL 或空字串當做引數提供給函數，則會傳回所有設定之 Smart Admin 參數的名稱/值組。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|parameter_name|NVARCHAR(128)|參數的名稱。 以下是傳回的目前參數清單：<br/><br/>**FileRetentionDebugXevent**<br/><br/>**SSMBackup2WADebugXevent**<br/><br/>**>ssmbackup2wanotificationemailids**<br/><br/>**SSMBackup2WAEnableUserDefinedPolicy**<br/><br/>**SSMBackup2WAEverConfigured**<br/><br/>**StorageOperationDebugXevent**|  
|parameter_value|NVARCHAR(128)|參數的目前設定值。|  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>權限  
 需要函數的 SELECT 權限。  
  
## <a name="examples"></a>範例  
 下列範例會傳回至少設定過一次的所有參數及其目前值。  
  
```  
USE MSDB  
GO  
SELECT *   
FROM managed_backup.fn_get_parameter (NULL)  
  
```  
  
 下列範例會傳回指定接收錯誤通知的電子郵件識別碼。 如果沒有傳回任何資料列，則表示此電子郵件通知選項尚未啟用。  
  
```  
USE MSDB  
GO  
SELECT *  
FROM managed_backup.fn_get_parameter ('SSMBackup2WANotficationEmailIds')  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 受控備份到 Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
