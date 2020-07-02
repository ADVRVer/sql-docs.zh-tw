---
title: sys.databases dm_broker_activated_tasks （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_activated_tasks
- sys.dm_broker_activated_tasks_TSQL
- dm_broker_activated_tasks
- dm_broker_activated_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_activated_tasks dynamic management view
ms.assetid: 17e6f87f-8f56-489d-9aed-216afc8ef310
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9a8d8c7d8c78af63afbd3c0343c855289d40e97b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85677799"
---
# <a name="sysdm_broker_activated_tasks-transact-sql"></a>sys.dm_broker_activated_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  針對 Service Broker 所啟動的每個預存程序，各傳回一個資料列。  
 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**spid**|**int**|啟動的預存程序之工作階段識別碼。 NULLABLE。|  
|**database_id**|**smallint**|佇列定義所在的資料庫識別碼。 NULLABLE。|  
|**queue_id**|**int**|啟動的預存程序所針對之佇列的物件識別碼。 NULLABLE。|  
|**procedure_name**|**Nvarchar （650）**|啟動的預存程序名稱。 NULLABLE。|  
|**execute_as**|**int**|預存程序執行身分的使用者識別碼。 NULLABLE。|  
  
## <a name="permissions"></a>權限  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="physical-joins"></a>實體聯結  
 ![sys.dm_broker_activated_tasks 的聯結](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-activated-tasks-1.gif "sys.dm_broker_activated_tasks 的聯結")  
  
## <a name="relationship-cardinalities"></a>關聯性基數  
  
|從|至|關聯性|  
|----------|--------|------------------|  
|dm_broker_activated_tasks.spid|dm_exec_sessions.session_id|一對一|  
  
## <a name="see-also"></a>另請參閱  
 [動態管理 Views 和函數 &#40;Transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 相關的動態管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

