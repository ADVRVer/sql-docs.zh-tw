---
title: sp_query_store_force_plan （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SP_QUERY_STORE_FORCE_PLAN
- SP_QUERY_STORE_FORCE_PLAN
- SYS.SP_QUERY_STORE_FORCE_PLAN_TSQL
- SP_QUERY_STORE_FORCE_PLAN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_query_store_force_plan
- sp_query_store_force_plan
ms.assetid: 0068f258-b998-4e4e-b47b-e375157c8213
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b34cf94a2ab6cfec601d41b02bf32b00f0eb3b41
ms.sourcegitcommit: 816ff47eeab157c66e0f75f18897a63dc8033502
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71207719"
---
# <a name="sp_query_store_force_plan-transact-sql"></a>sp_query_store_force_plan （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  針對特定查詢啟用強制特定計劃。  
  
 針對特定查詢強制執行計畫時，每次 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 遇到查詢時，它會嘗試在查詢最佳化工具中強制計畫。 如果計畫強制失敗，則會引發擴充事件，並指示查詢最佳化工具以正常方式進行優化。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
sp_query_store_force_plan [ @query_id = ] query_id , [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>引數  
`[ @query_id = ] query_id` 是查詢的識別碼。 *query_id*是**Bigint**，沒有預設值。  
  
`[ @plan_id = ] plan_id` 是要強制執行之查詢計劃的識別碼。 *plan_id*是**Bigint**，沒有預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="remarks"></a>Remarks  
  
## <a name="permissions"></a>Permissions  
 需要資料庫的**ALTER**許可權。
  
## <a name="examples"></a>範例  
 下列範例會傳回查詢存放區中查詢的相關資訊。  
  
```sql  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 在您識別要強制執行的 query_id 和 plan_id 之後，請使用下列範例來強制查詢使用計畫。  
  
```sql  
EXEC sp_query_store_force_plan 3, 3;  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_remove_query &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [查詢存放區目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [使用查詢存放區  監視效能](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)       
 [使用查詢存放區的最佳作法](../../relational-databases/performance/best-practice-with-the-query-store.md#CheckForced)    
  
  
