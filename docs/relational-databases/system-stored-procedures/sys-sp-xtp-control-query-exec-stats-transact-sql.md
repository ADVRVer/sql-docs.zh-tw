---
title: sys.databases sp_xtp_control_query_exec_stats （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_query_exec_stats_TSQL
- sys.sp_xtp_control_query_exec_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_query_exec_stats
ms.assetid: 4838125d-ad1e-479e-b7d2-42655e8f4f02
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 60d5967417698bc1970f02658fc28e8659201089
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82814440"
---
# <a name="syssp_xtp_control_query_exec_stats-transact-sql"></a>sys.sp_xtp_control_query_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  針對執行個體的所有原生編譯預存程序或是特定的原生編譯預存程序，啟用個別查詢統計資料收集。  
  
 啟用統計資料收集時，效能會降低。 如果您只需要對一個或少數幾個原生編譯的預存程序進行疑難排解，可以只針對這幾個原生編譯的預存程序啟用統計資料收集。  
  
 若要啟用所有原生編譯預存程式的程式層級的統計資料收集，請參閱[sys.databases &#40;transact-sql&#41;sp_xtp_control_proc_exec_stats ](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md)。  
  
## <a name="syntax"></a>語法  
  
```  
sp_xtp_control_query_exec_stats [ [ @new_collection_value = ] collection_value ],  
[ [ @database_id = ] database_id   
[ , [ @xtp_object_id = ] procedure_id ] ,   
[ @old_collection_value] ]  
```  
  
## <a name="arguments"></a>引數  
 @new_collection_value=*值*  
 決定程序層級統計資料收集為開啟 (1) 或關閉 (0)。  
  
 @new_collection_value當啟動時，會設定為零 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
 @database_id= = *database_id*， @xtp_object_id = *procedure_id*  
 原生編譯預存程序的資料庫識別碼和物件識別碼。 如果已針對實例啟用統計資料收集（[sp_xtp_control_proc_exec_stats sys.databases &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md)），則會收集原生編譯預存程式的統計資料。 關閉執行個體上的統計資料收集並不會關閉個別原生編譯預存程序的統計資料收集。  
  
 使用[sys.databases &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)、 [sys.databases &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)、 [DB_ID &#40;Transact-sql&#41;](../../t-sql/functions/db-id-transact-sql.md)或 OBJECT_ID &#40;transact-sql&#41;，以取得資料庫和預存[程式](../../t-sql/functions/object-id-transact-sql.md)的識別碼。  
  
 @old_collection_value=*值*  
 傳回目前狀態。  
  
## <a name="return-code"></a>傳回碼  
 0 代表成功。 非零代表失敗。  
  
## <a name="permissions"></a>權限  
 需要固定系統管理員 (sysadmin) 角色的成員資格。  
  
## <a name="code-sample"></a>程式碼範例  
 下列程式碼範例示範如何針對執行個體的所有原生編譯預存程序啟用統計資料收集，然後是針對特定的原生編譯預存程序啟用統計資料收集。  
  
```sql   
DECLARE @c bit  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1;  
  
EXEC sp_xtp_control_query_exec_stats @old_collection_value=@c output;  
SELECT @c AS 'collection status';  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1,   
@database_id = 5, @xtp_object_id = 341576255;  
  
EXEC sp_xtp_control_query_exec_stats @database_id = 5,   
@xtp_object_id = 341576255, @old_collection_value=@c output;  
  
SELECT @c AS 'collection status';  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的系統預存程式](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
