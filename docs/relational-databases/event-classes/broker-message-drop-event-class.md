---
title: "Broker:Message Drop 事件類別 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker:Message Drop event class
ms.assetid: f532b7c9-ca34-4bac-8dc3-53f9895fd6af
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 47fd82b02e3d808d2609e5c9830099d11627795f
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="brokermessage-drop-event-class"></a>Broker:Message Drop 事件類別
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 當 Service Broker 無法保留其收到，且應於此執行個體中傳遞至服務的訊息時，會產生 **Broker:Message Drop** 事件。 對於應該已被轉送的訊息，請參閱 [Broker︰Forwarded Message Dropped 事件類別](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)。  
  
## <a name="brokermessage-drop-event-class-data-columns"></a>Broker:Message Drop 事件類別資料行  
  
|資料行|型別|說明|資料行編號|可篩選|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**Application Name**|**nvarchar**|建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體之連接的用戶端應用程式名稱。 這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。|10|是|  
|**BigintData1**|**bigint**|已卸除訊息的序號。|52|否|  
|**BigintData2**|**bigint**|成功確認的最後一個訊息之序號。|53|否|  
|**ClientProcessID**|**int**|主機電腦指派給用戶端應用程式執行中處理序的識別碼。 如果用戶端提供處理序識別碼，這個資料行就會擴展。|9|是|  
|**DatabaseID**|**int**|由 USE *database* 陳述式所指定的資料庫識別碼，或者如果沒有針對指定執行個體發出 USE *database* 陳述式，則是預設資料庫的識別碼。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 資料行，則 **ServerName** 會顯示資料庫的名稱。 請使用 DB_ID 函數判斷資料庫的值。|3|是|  
|**錯誤**|**int**|針對事件內文字的 **sys.messages** 中之訊息識別碼。|31|否|  
|**EventClass**|**int**|擷取的事件類別類型。 **Broker:MessageDrop** 的值永遠是 **160**。|27|否|  
|**EventSequence**|**int**|此事件的序號。|51|否|  
|**EventSubClass**|**nvarchar**|指出已卸除訊息是否為循序訊息。 為下列兩個值的其中一個值：<br /><br /> **Sequenced Message**。 已卸除的訊息為循序訊息。<br /><br /> **Unsequenced Message**。 已卸除的訊息不是循序訊息。|21|是|  
|**GUID**|**uniqueidentifier**|已卸除訊息所屬的交談之交談識別碼。 此識別碼是以訊息的一部份傳送，並在交談的兩端之間共用。|54|否|  
|**HostName**|**nvarchar**|執行用戶端的電腦名稱。 這個資料行會在用戶端提供主機名稱時填入。 若要判斷主機名稱，請使用 HOST_NAME 函數。|8|是|  
|**IntegerData**|**int**|已卸除訊息的片段編號。|25|否|  
|**IntegerData2**|**int**|正在確認的已卸除訊息之訊息片段編號。|55|否|  
|**IsSystem**|**int**|指出事件是發生在系統處理序或使用者處理序。 1 = 系統，0 = 使用者。|60|否|  
|**LoginName**|**nvarchar**|使用者的登入名稱 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性登入或 DOMAIN\Username 格式的 Windows 登入認證)。|11|否|  
|**LoginSid**|**image**|已登入之使用者的安全性識別碼 (SID)。 伺服器上的每一個登入之 SID 是唯一的。|41|是|  
|**NTDomainName**|**nvarchar**|使用者所隸屬的 Windows 網域。|7|是|  
|**NTUserName**|**nvarchar**|擁有產生此事件之連接的使用者名稱。|6|是|  
|**ObjectName**|**nvarchar**|對話的交談控制代碼。|34|否|  
|**RoleName**|**nvarchar**|交談控制代碼的角色。 為 **initiator** 或 **target**其中一個角色。|38|否|  
|**ServerName**|**nvarchar**|正在追蹤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。|26|否|  
|**Severity**|**int**|事件中文字的嚴重性編號。|29|否|  
|**SPID**|**int**|由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指派給用戶端關聯之處理序的伺服器處理序識別碼。|12|是|  
|**StartTime**|**datetime**|事件啟動的時間 (如果有的話)。|14|是|  
|**State**|**int**|指出產生事件的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原始程式碼內的位置。 每個可能產生此事件的位置都有不同的狀態碼。 Microsoft 支援工程師可以使用此狀態碼來尋找產生事件的位置。|30|否|  
|**TextData**|**ntext**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 卸除訊息的理由。|1|是|  
|**TransactionID**|**bigint**|系統指派的交易識別碼。|4|否|  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
