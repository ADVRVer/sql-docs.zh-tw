---
title: sys.dm_exec_input_buffer (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_input_buffer
- sys.dm_exec_input_buffer _tsql
- dm_exec_input_buffer
- dm_exec_input_buffer_tsql
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_input_buffer dynamic management function
ms.assetid: fb34a560-bde9-4ad9-aa96-0d4baa4fc104
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8531f33f2d027eba14d4416e9138560b25ead20e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013124"
---
# <a name="sysdmexecinputbuffer-transact-sql"></a>sys.dm_exec_input_buffer (Transact-SQL)
[!INCLUDE[tsql-appliesto-2014sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2014sp2-asdb-xxxx-xxx-md.md)]

  傳回陳述式的執行個體的相關資訊[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
sys.dm_exec_input_buffer ( session_id , request_id )
```  
  
## <a name="arguments"></a>引數  
*session_id*  
執行要查閱之批次的工作階段識別碼。 *session_id*已**smallint**。 *session_id*可以從下列動態管理物件取得：  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)   
  
*request_id*  
從 request_id [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)。 *request_id*已**int**。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**event_type**|**nvarchar(256)**|在指定的 spid 的輸入緩衝區中的事件類型。|  
|**parameters**|**smallint**|陳述式所提供的任何參數。|  
|**event_info**|**nvarchar(max)**|指定的 spid 的輸入緩衝區中的陳述式文字。|  
  
## <a name="permissions"></a>Permissions  
 在  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，如果使用者有 VIEW SERVER STATE 權限，使用者會看到所有執行的工作階段的執行個體上[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; 否則使用者會看到只有目前的工作階段。  
  
 在  [!INCLUDE[ssSDS](../../includes/sssds-md.md)]，如果使用者是資料庫擁有者，使用者會看到所有執行的工作階段[!INCLUDE[ssSDS](../../includes/sssds-md.md)]; 否則使用者會看到只有目前的工作階段。  
  
## <a name="remarks"></a>備註  
 此動態管理函數可供搭配 sys.dm_exec_sessions 或 sys.dm_exec_requests 這麼做**CROSS APPLY**。  
  
## <a name="examples"></a>範例  
  
### <a name="a-simple-example"></a>A. 簡單範例  
 下列範例示範如何將工作階段識別碼 (SPID) 和要求識別碼傳遞至函式。  
  
```sql  
SELECT * FROM sys.dm_exec_input_buffer (52, 0);
GO
```  
  
### <a name="b-using-cross-apply-to-additional-information"></a>B. 使用交叉套用的其他資訊  
 下列範例會列出與工作階段識別碼大於 50 的工作階段的輸入的緩衝區。  
  
```sql  
SELECT es.session_id, ib.event_info   
FROM sys.dm_exec_sessions AS es  
CROSS APPLY sys.dm_exec_input_buffer(es.session_id, NULL) AS ib  
WHERE es.session_id > 50;
GO
```  
  
## <a name="see-also"></a>另請參閱  
 [執行相關動態管理檢視和函式&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [DBCC INPUTBUFFER &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)  
