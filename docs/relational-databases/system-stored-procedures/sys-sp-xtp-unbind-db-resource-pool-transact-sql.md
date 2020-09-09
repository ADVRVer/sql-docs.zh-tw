---
description: sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)
title: sys. sp_xtp_unbind_db_resource_pool (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xtp_unbind_db_resource_pool_TSQL
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool_TSQL
- sys.sp_xtp_unbind_db_resource_pool
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool
ms.assetid: 695a796d-087e-4bc8-99d0-ddc342604c75
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 27d5d5efd923dfffd66054da48b8baf28b6f193b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551094"
---
# <a name="syssp_xtp_unbind_db_resource_pool-transact-sql"></a>sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  這個系統程序會移除資料庫與資源集區之間的現有繫結，以便追蹤 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 記憶體使用量。  如果目前沒有任何集區繫結至指定的資料庫，就會傳回成功。 當資料庫解除繫結時，先前配置給記憶體最佳化物件的記憶體仍然會配置給先前的資源集區。 您必須重新啟動資料庫以釋出配置的記憶體。 一旦資料庫與資源集區解除繫結之後，繫結就會指向 DEFAULT 資源集區。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```sql  
sys.sp_xtp_unbind_db_resource_pool 'database_name'  
```  
  
## <a name="arguments"></a>引數  
 database_name  
 現有 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資料庫的名稱。  
  
#### <a name="parameters"></a>參數  
  
## <a name="messages"></a>Messages  
 如果資料庫已繫結至具名的資源集區，此程序就會傳回成功。 不過，您必須重新啟動資料庫，才能讓解除繫結生效。  
 如果指定的資料庫沒有任何現有的繫結，`sp_xtp_unbind_db_resource_pool` 會傳回成功，但也會提供參考用訊息：  
  
```  
Msg 41374, Level 16, State 1, Procedure sp_xtp_unbind_db_resource_pool_internal, Line 140.  
Database 'Hekaton_DB' does not have a binding to a resource pool.  
  
```  
  
## <a name="example"></a>範例  
 下列程式碼會解除繫結 Hekaton_DB 資料庫與它所繫結的 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資源集區。  如果 Hekaton_DB 目前並未繫結至 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資源集區，就會提供一則訊息。 資料庫必須重新啟動，才能讓解除繫結生效。  
  
```sql  
sys.sp_xtp_unbind_db_resource_pool 'Hekaton_DB'  
```  
  
## <a name="requirements"></a>規格需求  
  
-   `database_name` 所指定的資料庫必須具有 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資源集區的繫結。  
  
-   需要 CONTROL SERVER 權限。  
  
## <a name="see-also"></a>另請參閱  
 [資料庫並繫結至資源集區的指引，請參閱](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)  
  
  
