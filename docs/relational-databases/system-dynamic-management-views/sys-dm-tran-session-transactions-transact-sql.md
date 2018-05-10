---
title: sys.dm_tran_session_transactions (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_tran_session_transactions
- sys.dm_tran_session_transactions
- sys.dm_tran_session_transactions_TSQL
- dm_tran_session_transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_session_transactions dynamic management view
ms.assetid: c7157491-58c2-49fe-87d7-0c9723113adf
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4df6afdab47fc0da07412223b394ad0dc77a81f7
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmtransessiontransactions-transact-sql"></a>sys.dm_tran_session_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回相關聯交易和工作階段的相互關聯資訊。  
  
> [!NOTE]  
>  若要呼叫從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名稱**sys.dm_pdw_nodes_tran_session_transactions**。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|執行交易所在的工作階段識別碼。|  
|transaction_id|**bigint**|交易的識別碼。|  
|transaction_descriptor|**binary(8)**|與用戶端驅動程式通訊時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的交易識別碼。|  
|enlist_count|**int**|在工作階段中處理交易的作用中要求數目。|  
|is_user_transaction|**bit**|1 = 交易由使用者要求起始。<br /><br /> 0 = 系統交易。|  
|is_local|**bit**|1 = 本機交易。<br /><br /> 0 = 分散式交易或編列的已繫結工作階段交易。|  
|is_enlisted|**bit**|1 = 編列的分散式交易。<br /><br /> 0 = 非編列的分散式交易。|  
|is_bound|**bit**|1 = 交易透過繫結工作階段而作用於工作階段中。<br /><br /> 0 = 交易透過繫結工作階段而未作用於工作階段中。|  
|open_transaction_count||每個工作階段開啟中的交易數目。|  
|pdw_node_id|**int**|**適用於**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此發行版本上的節點識別碼。|  
  
## <a name="permissions"></a>Permissions

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`資料庫的權限。   

## <a name="remarks"></a>備註  
 透過繫結工作階段和分散式交易，交易可在一個以上的工作階段中執行。 在這些情況下，sys.dm_tran_session_transactions 將針對相同的 transaction_id 顯示多個資料列，針對執行交易所在的每一個工作階段，各顯示一個資料列。  
  
 在自動認可模式中使用 Multiple Active Result Set (MARS) 來執行多項要求，就可以使單一工作階段中有一個以上的作用中交易。 在這些情況下，sys.dm_tran_session_transactions 將針對相同的 session_id 顯示多個資料列，針對在該工作階段下執行的每一項交易，各顯示一個資料列。  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [交易相關的動態管理檢視和函數 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


