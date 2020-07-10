---
title: dm_pdw_exec_connections (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7f47fb9d9047e02fde6a7e8a7f758e455e3fc789
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197113"
---
# <a name="sysdm_pdw_exec_connections-transact-sql"></a>dm_pdw_exec_connections (Transact-sql) 
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  傳回有關與這個 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 執行個體建立之連接及每一個連接之詳細資料的資訊。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|session_id|**int**|識別這項連接的相關工作階段。 使用傳回 `SESSION_ID()` `session_id` 目前連接的。|  
|connect_time|**datetime**|建立連接的時間戳記。 不可為 Null。|  
|encrypt_option|**nvarchar(40)**|表示 (連接已加密) 或 FALSE (未 enctypred) 連接。|  
|auth_scheme|**nvarchar(40)**|指定搭配這個連接使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows 驗證配置。 不可為 Null。|  
|client_id|**varchar(48)**|連接到這部伺服器之用戶端的 IP 位址。 可為 Null。|  
|sql_spid|**int**|連接的伺服器處理序識別碼。 使用傳回 `@@SPID` `sql_spid` 目前連接的。對於大部分的制定目的，請改用 `session_id` 。|  
  
## <a name="permissions"></a>權限  
 需要伺服器的**VIEW SERVER STATE**許可權。  
  
## <a name="relationship-cardinalities"></a>關聯性基數  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions。 session_id|dm_pdw_exec_connections。 session_id|一對一|  
|dm_pdw_exec_requests。 connection_id|dm_pdw_exec_connections。 connection_id|多對一|  
  
## <a name="examples-sssdwfull-and-sspdw"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 收集查詢自有連接相關資訊的典型查詢。  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理 Views &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

