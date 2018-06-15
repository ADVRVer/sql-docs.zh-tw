---
title: sys.sp_xtp_bind_db_resource_pool (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 08/03/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_xtp_bind_db_resource_pool_TSQL
- sp_xtp_bind_db_resource_pool
- sys.sp_xtp_bind_db_resource_pool_TSQL
- sys.sp_xtp_bind_db_resource_pool
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xtp_bind_db_resource_pool
- sys.sp_xtp_bind_db_resource_pool
ms.assetid: c2a78073-626b-4159-996e-1808f6bfb6d2
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4ce8af4df2491d6b80acf931ae769b1a0299504b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260291"
---
# <a name="sysspxtpbinddbresourcepool-transact-sql"></a>sys.sp_xtp_bind_db_resource_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  將指定的 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資料庫繫結至指定的資源集區。 資料庫和資源集區都必須在執行 `sys.sp_xtp_bind_db_resource_pool` 之前存在。  
  
 這個系統程序會在 resource_pool_name 所識別的資源管理員集區與 database_name 所識別的資料庫之間建立繫結。 資料庫在繫結時不需要具有任何記憶體最佳化物件。 如果沒有記憶體最佳化物件，就不會從資源集區取得任何記憶體。 資源管理員將依照下列說明使用這個繫結來管理 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 配置器所配置的記憶體。  
  
 如果指定的資料庫原本已經有繫結，此程序就會傳回錯誤。  一個資料庫絕對不會有多個作用中繫結。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
  
## <a name="syntax"></a>語法  
  
```sql  
sys.sp_xtp_bind_db_resource_pool 'database_name', 'resource_pool_name'  
```  
  
## <a name="arguments"></a>引數  
 database_name  
 現有 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資料庫的名稱。  
  
 resource_pool_name  
 現有資源集區的名稱。  
  
## <a name="messages"></a>訊息  
 發生錯誤時，`sp_xtp_bind_db_resource_pool` 會傳回下列其中一則訊息。  
  
 **資料庫不存在**  
 Database_name 必須參考現有的資料庫。 如果指定之識別碼的資料庫不存在，就會傳回下列訊息：   
*資料庫識別碼 %d 不存在。請此繫結，使用有效的資料庫識別碼。*  
  
```  
Msg 911, Level 16, State 18, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Database 'Hekaton_DB213' does not exist. Make sure that the name is entered correctly.  
```  
  
**資料庫是系統資料庫**  
 無法在系統資料庫中建立 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資料表。  因此，針對這類資料庫建立 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 記憶體的繫結是無效的作法。  系統會傳回下列錯誤：  
*Database_name %s 指的是系統資料庫。資源集區可能只繫結至使用者資料庫。*  
  
```  
Msg 41371, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Binding to a resource pool is not supported for system database 'master'. This operation can only be performed on a user database.  
```  
  
**資源集區不存在**  
 resource_pool_name 所識別的資源集區必須在執行 `sp_xtp_bind_db_resource_pool` 之前存在。  如果指定之識別碼的集區不存在，就會傳回下列錯誤：  
*資源集區 %s 不存在。請輸入有效的資源集區名稱。*  
  
```  
Msg 41370, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Resource pool 'Pool_Hekaton' does not exist or resource governor has not been reconfigured.  
```  
  
**Pool_name 參考保留的系統集區**  
 集區名稱 “INTERNAL” 和 “DEFAULT” 已保留給系統集區。  將資料庫明確繫結至其中一個集區是無效的作法。  如果輸入系統集區名稱，就會傳回下列錯誤：  
*資源集區 %s 是系統資源集區。系統資源集區可能不明確繫結至資料庫，使用此程序。*  
  
```  
Msg 41373, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 51  
Database 'Hekaton_DB' cannot be explicitly bound to the resource pool 'internal'. A database can only be bound only to a user resource pool.  
```  
  
**資料庫已繫結至另一個資源集區**  
 一個資料庫在任何時候都只能繫結至一個資源集區。 您必須先明確移除資源集區的資料庫繫結，然後才能將它們繫結至其他集區。 請參閱[sys.sp_xtp_bind_db_resource_pool &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)。  
*資料庫 %s 已經繫結至資源集區 %s。您可以建立新的繫結之前，您必須解除連結。*  
  
```  
Msg 41372, Level 16, State 1, Procedure sp_xtp_bind_db_resource_pool_internal, Line 54  
Database 'Hekaton_DB' is currently bound to a resource pool. A database must be unbound before creating a new binding.  
```  
  
 成功時，`sp_xtp_bind_db_resource_pool` 會傳回下列訊息。  
  
**成功繫結**  
 成功時，此函數會傳回下列成功訊息，並記錄在 SQL ERRORLOG 中  
*具有識別碼 %d 資料庫與資源集區識別碼 %d 已成功建立資源繫結。*  
  
## <a name="examples"></a>範例  
A.  下列程式碼範例會將 Hekaton_DB 資料庫繫結至 Pool_Hekaton 資源集區。  
  
```sql  
sys.sp_xtp_bind_db_resource_pool N'Hekaton_DB', N'Pool_Hekaton'  
```  
 
 繫結會在下一次資料庫重新上線時生效。  
 
 B. 展開的範例包括一些基本檢查上面的範例。  執行下列[!INCLUDE[tsql](../../includes/tsql-md.md)]中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]\:
 
```sql
DECLARE @resourcePool sysname = N'Pool_Hekaton';
DECLARE @database sysname = N'Hekaton_DB';

-- Check whether resource pool exists
IF NOT EXISTS (
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = @resourcePool
    )
BEGIN
    SELECT N'Resource pool "' + @resourcePool + N'" does not exist or resource governor has not been reconfigured.';
END
-- Check whether database is already bound to a resource pool
ELSE IF EXISTS (
    SELECT p.name
    FROM sys.databases d
    JOIN sys.resource_governor_resource_pools p
    ON d.resource_pool_id = p.pool_id
    WHERE d.name = @database
    )
BEGIN
    SELECT N'Database "' + @database + N'" is currently bound to resource pool "' + @resourcePool  + N'". A database must be unbound before creating a new binding.';
END
-- Bind resource pool to database.
ELSE BEGIN
    EXEC sp_xtp_bind_db_resource_pool @database, @resourcePool; 
END 
``` 
  
## <a name="requirements"></a>需求  
  
-   `database_name` 所指定的資料庫與 `resource_pool_name` 所指定的資源集區都必須在繫結之前存在。  
  
-   需要 CONTROL SERVER 權限。  
  
## <a name="see-also"></a>另請參閱  
 [將包含記憶體最佳化資料表的資料庫繫結至資源集區](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool & #40;TRANSACT-SQL & #41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)  
  
  
