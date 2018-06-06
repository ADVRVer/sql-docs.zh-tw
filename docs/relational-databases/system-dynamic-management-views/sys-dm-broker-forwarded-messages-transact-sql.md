---
title: sys.dm_broker_forwarded_messages (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a4a772419ba49436cefd1a135bed3859c5905ae2
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmbrokerforwardedmessages-transact-sql"></a>sys.dm_broker_forwarded_messages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體正在轉送的每一個 Service Broker 訊息，各傳回一個資料列。  
  

|資料行名稱|資料類型|Description|  
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
  
## <a name="permissions"></a>Permissions  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 相關的動態管理檢視 & #40;TRANSACT-SQL & #41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

