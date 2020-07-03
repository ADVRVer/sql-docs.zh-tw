---
title: sys.databases dm_broker_forwarded_messages （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_forwarded_messages
- dm_broker_forwarded_messages
- sys.dm_broker_forwarded_messages_TSQL
- dm_broker_forwarded_messages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_forwarded_messages dynamic management view
ms.assetid: 5576376d-6364-417a-8475-aa770e060845
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2040eb35dbc44e319737525b74d6c23ccb77ff83
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893946"
---
# <a name="sysdm_broker_forwarded_messages-transact-sql"></a>sys.dm_broker_forwarded_messages (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體正在轉送的每一個 Service Broker 訊息，各傳回一個資料列。  
  

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**conversation_id**|**uniqueidentifier**|這則訊息所屬交談的識別碼。 NULLABLE。|  
|**is_initiator**|**bit**|指出這則訊息是否來自交談的起始端。  NULLABLE。<br /><br /> 0 = 不是來自起始端<br /><br /> 1 = 來自起始端|  
|**to_service_name**|**nvarchar(512)**|這則訊息所送往之服務的名稱。 NULLABLE。|  
|**to_broker_instance**|**nvarchar(512)**|主控這則訊息所送往之服務的 Broker 識別碼。 NULLABLE。|  
|**from_service_name**|**nvarchar(512)**|這則訊息的來源服務名稱。 NULLABLE。|  
|**from_broker_instance**|**nvarchar(512)**|主控這則訊息之來源服務的 Broker 識別碼。 NULLABLE。|  
|**adjacent_broker_address**|**nvarchar(512)**|這則訊息所送往的網路位址。 NULLABLE。|  
|**message_sequence_number**|**bigint**|對話方塊中訊息的序號。 NULLABLE。|  
|**message_fragment_number**|**int**|如果將對話訊息片段化，這即是這則傳輸訊息包含的片段號碼。 NULLABLE。|  
|**hops_remaining**|**tinyint**|在到達最後目的地之前可重新傳輸訊息的次數。 每次轉送訊息時，這個數字就會減 1。 NULLABLE。|  
|**time_to_live**|**int**|訊息保持作用中的最長時間。 當這個值到達 0 時，即捨棄訊息。 NULLABLE。|  
|**time_consumed**|**int**|訊息已在作用中的時間。 每次轉遞訊息時，這個數字就會加上轉遞訊息所花的時間。 不是 NULLABLE。|  
|**message_id**|**uniqueidentifier**|訊息的識別碼。 NULLABLE。|  
  
## <a name="permissions"></a>權限  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [動態管理 Views 和函數 &#40;Transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 相關的動態管理檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

