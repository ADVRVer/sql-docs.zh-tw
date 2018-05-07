---
title: sys.dm_exec_cached_plans (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cached_plans
- dm_exec_cached_plans
- dm_exec_cached_plans_TSQL
- sys.dm_exec_cached_plans_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_cached_plans dynamic management view
ms.assetid: 95b707d3-3a93-407f-8e88-4515d4f2039d
caps.latest.revision: 44
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a51f46b0576a6c57748a345ab2584540ad89c2ae
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexeccachedplans-transact-sql"></a>sys.dm_exec_cached_plans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 快取的每個查詢計畫傳回一個資料列，加快查詢執行的速度。 您可以使用這個動態管理檢視尋找快取的查詢計畫、快取的查詢文字、快取計畫所使用的記憶體，以及快取計畫的重複使用計數。  
  
 在 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]，動態管理檢視不可以公開可能會影響資料庫內含項目的資訊或公開有關使用者可存取之其他資料庫的資訊。 為了避免公開此資訊，包含不屬於連接租用戶之資料的每個資料列都會被篩選出來。此外，資料行的值**memory_object_address**和**pool_id**會篩選出來; 資料行值設為 NULL。  
  
> [!NOTE]  
>  若要呼叫從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名稱**sys.dm_pdw_nodes_exec_cached_plans**。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|bucketid|**int**|這是快取項目的雜湊值區識別碼。 這個值的範圍從 0 開始，一直到該快取類型的雜湊資料表大小。<br /><br /> 若為 SQL 計畫和物件計畫快取，雜湊資料表在 32 位元系統上最大為 10007，在 64 位元系統上最大為 40009。 若為 Bound Trees 快取，雜湊資料表在 32 位元系統上最大為 1009，在 64 位元系統上最大為 4001。 若為擴充預存程序快取，雜湊資料表在 32 位元和 64 位元系統上最大為 127。|  
|refcounts|**int**|參考這個快取物件的快取物件數目。 **Refcounts**必須至少為 1，快取中項目。|  
|usecounts|**int**|已經查閱快取物件的次數。 當參數化查詢在快取中找到計畫時，不會累加。 但是，使用執行程序表時，可能會累加多次。|  
|size_in_bytes|**int**|快取物件所耗用的位元組數目。|  
|memory_object_address|**varbinary(8)**|快取項目的記憶體位址。 這個值可以搭配[sys.dm_os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)取得的記憶體細分，快取計畫與[sys.dm_os_memory_cache_entries](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)一起，以取得快取項目的成本。|  
|cacheobjtype|**nvarchar(34)**|快取中的物件類型。 這個值可以是下列值之一：<br /><br /> 編譯的計畫<br /><br /> 已編譯計畫虛設常式<br /><br /> 剖析樹狀結構<br /><br /> 擴充程序<br /><br /> CLR 編譯的函數<br /><br /> CLR 編譯的程序|  
|objtype|**nvarchar(16)**|物件的類型。 以下是可能的值和其相對應的描述。<br /><br /> 程序： 預存程序<br />已備妥： 備妥的陳述式<br />臨機操作： 臨機操作查詢。 是指[!INCLUDE[tsql](../../includes/tsql-md.md)]提交為語言事件使用**osql**或**sqlcmd**而非遠端程序呼叫。<br />ReplProc： 複寫篩選器的程序<br />觸發程序： 觸發程序<br />檢視： 檢視<br />預設值： Default<br />UsrTab： 使用者資料表<br />SysTab： 系統資料表<br />檢查： 檢查條件約束<br />規則： 規則|  
|plan_handle|**varbinary(64)**|記憶體中計畫的識別碼。 這個識別碼是暫時性的，只有當計畫留在快取時才會保留。 這個值可以與下列動態管理函數一起使用：<br /><br /> [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)<br /><br /> [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)<br /><br /> [sys.dm_exec_plan_attributes](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)|  
|pool_id|**int**|計算此計畫記憶體使用量代表之資源集區的識別碼。|  
|pdw_node_id|**int**|**適用於**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此發行版本上的節點識別碼。|  
  
 <sup>1</sup>  
  
## <a name="permissions"></a>Permissions

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`資料庫的權限。   

## <a name="examples"></a>範例  
  
### <a name="a-returning-the-batch-text-of-cached-entries-that-are-reused"></a>A. 傳回重複使用之快取項目的批次文字  
 下列範例會針對使用超過一次的所有快取項目，傳回其 SQL 文字。  
  
```  
SELECT usecounts, cacheobjtype, objtype, text   
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_sql_text(plan_handle)   
WHERE usecounts > 1   
ORDER BY usecounts DESC;  
GO  
```  
  
### <a name="b-returning-query-plans-for-all-cached-triggers"></a>B. 傳回所有快取觸發程序的查詢計畫  
 下列範例會傳回所有快取觸發程序的快取計畫。  
  
```  
SELECT plan_handle, query_plan, objtype   
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_query_plan(plan_handle)   
WHERE objtype ='Trigger';  
GO  
```  
  
### <a name="c-returning-the-set-options-with-which-the-plan-was-compiled"></a>C. 傳回編譯計畫所用的 SET 選項  
 下列範例會傳回編譯計畫所用的 SET 選項。 `sql_handle`也傳回計畫。 PIVOT 運算子可用來輸出`set_options`和`sql_handle`屬性做為資料行，而不是資料列。 如需有關中傳回的值`set_options`，請參閱[sys.dm_exec_plan_attributes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)。  
  
```  
SELECT plan_handle, pvt.set_options, pvt.sql_handle  
FROM (  
      SELECT plan_handle, epa.attribute, epa.value   
      FROM sys.dm_exec_cached_plans   
      OUTER APPLY sys.dm_exec_plan_attributes(plan_handle) AS epa  
      WHERE cacheobjtype = 'Compiled Plan'  
      ) AS ecpa   
PIVOT (MAX(ecpa.value) FOR ecpa.attribute IN ("set_options", "sql_handle")) AS pvt;  
GO  
```  
  
### <a name="d-returning-the-memory-breakdown-of-all-cached-compiled-plans"></a>D. 傳回所有快取編譯計畫的記憶體細分  
 下列範例會傳回快取中所有編譯計畫所用細分的記憶體。  
  
```  
SELECT plan_handle, ecp.memory_object_address AS CompiledPlan_MemoryObject,   
    omo.memory_object_address, type, page_size_in_bytes   
FROM sys.dm_exec_cached_plans AS ecp   
JOIN sys.dm_os_memory_objects AS omo   
    ON ecp.memory_object_address = omo.memory_object_address   
    OR ecp.memory_object_address = omo.parent_address  
WHERE cacheobjtype = 'Compiled Plan';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [執行相關動態管理檢視和函數&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)   
 [sys.dm_exec_plan_attributes &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_os_memory_objects &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)   
 [sys.dm_os_memory_cache_entries &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)  
  
  


