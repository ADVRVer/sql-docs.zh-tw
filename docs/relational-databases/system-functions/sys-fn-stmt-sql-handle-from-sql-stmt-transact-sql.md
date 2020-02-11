---
title: sys.databases fn_stmt_sql_handle_from_sql_stmt （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 6794e073-0895-4507-aba3-c3545acc843f
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 92ebff45c8599e6257ad22f563da6af5067d8e3c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68059276"
---
# <a name="sysfn_stmt_sql_handle_from_sql_stmt-transact-sql"></a>sys.fn_stmt_sql_handle_from_sql_stmt (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  取得指定**** 參數化型[!INCLUDE[tsql](../../includes/tsql-md.md)]別（simple 或強制）下之語句的 stmt_sql_handle。 這可讓您在知道儲存在查詢存放區中的查詢，方法是在您知道其文字時使用它們的**stmt_sql_handle** 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
sys.fn_stmt_sql_handle_from_sql_stmt   
(  
    'query_sql_text',   
    [ query_param_type   
) [;]  
```  
  
## <a name="arguments"></a>引數  
 *query_sql_text*  
 這是您想要其控制碼之查詢存放區中查詢的文字。 *query_sql_text*是**Nvarchar （max）**，沒有預設值。  
  
 *query_param_type*  
 這是查詢的參數類型。 *query_param_type*是**Tinyint**。 可能的值為：  
  
-   Null-預設為0  
  
-   0 - 無  
  
-   1-使用者  
  
-   2-簡單  
  
-   3-強制  
  
## <a name="columns-returned"></a>傳回的資料行  
 下表列出 sys.databases fn_stmt_sql_handle_from_sql_stmt 傳回的資料行。  
  
|資料行名稱|類型|描述|  
|-----------------|----------|-----------------|  
|**statement_sql_handle**|**Varbinary （64）**|SQL 控制碼。|  
|**query_sql_text**|**nvarchar(max)**|[!INCLUDE[tsql](../../includes/tsql-md.md)]語句的文字。|  
|**query_parameterization_type**|**tinyint**|查詢參數化型別。|  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>備註  
  
## <a name="permissions"></a>權限  
 需要資料庫的**EXECUTE**許可權，以及查詢存放區目錄檢視的**刪除**許可權。  
  
## <a name="examples"></a>範例  
 下列範例會執行語句，然後使用`sys.fn_stmt_sql_handle_from_sql_stmt`傳回該語句的 SQL 控制碼。  
  
```  
SELECT * FROM sys.databases;   
SELECT * FROM sys.fn_stmt_sql_handle_from_sql_stmt('SELECT * FROM sys.databases', NULL);  
```  
  
 使用函數，將查詢存放區資料與其他動態管理檢視相互關聯。 下列範例︰  
  
```  
SELECT qt.query_text_id, q.query_id, qt.query_sql_text, qt.statement_sql_handle,  
q.context_settings_id, qs.statement_context_id   
FROM sys.query_store_query_text AS qt  
JOIN sys.query_store_query AS q   
    ON qt.query_text_id = q.query_id  
CROSS APPLY sys.fn_stmt_sql_handle_from_sql_stmt (qt.query_sql_text, null) AS fn_handle_from_stmt  
JOIN sys.dm_exec_query_stats AS qs   
    ON fn_handle_from_stmt.statement_sql_handle = qs.statement_sql_handle;  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_query_store_force_plan &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;Transct-sql-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [sp_query_store_remove_query &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [查詢存放區目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
