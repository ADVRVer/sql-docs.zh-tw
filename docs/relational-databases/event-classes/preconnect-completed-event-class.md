---
title: "PreConnect:Completed 事件類別 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5f6bba668ddd25925ede8fe8cf71e4f1775f3dd9
ms.lasthandoff: 04/11/2017

---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed 事件類別
  PreConnect:Completedevent 類別會指出 LOGON 觸發程序或資源管理員分類函數執行完成。  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>PreConnect:Completed 事件類別資料行  
  
|資料行名稱|資料類型|描述|資料行識別碼|可篩選|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|216|27|否|  
|SPID|**int**|引發此事件之伺服器處理序的識別碼。|12|是|  
|EventSubClass|**int**|1 代表使用者定義的分類函數。|21|是|  
|StartTime|**datetime**|使用者定義分類函數啟動的時間。|14|是|  
|EndTime|**datetime**|使用者定義分類函數啟動的時間。|15|是|  
|有效期間|**bigint**|分類函數使用的時間量 (以百萬分之一秒為單位)。|13|是|  
|ObjectID|**int**|使用者定義之分類物件的識別碼。|22|是|  
|CPU|**int**|CPU 使用量 (以毫秒為單位)。|18|是|  
|Reads|**int**|邏輯讀取的數目。|16|是|  
|Writes|**int**|邏輯寫入的數目。|17|是|  
|GroupID|**int**|分類工作負載群組的識別碼。|66|是|  
|錯誤|**int**|如果使用者定義的分類函數無法執行，就是上一個錯誤號碼。|31|是|  
|State|**int**|上一個錯誤的狀態。|30|是|  
|TargetUserName|**sysname**|如果系統找不到對應的作用中群組，就是使用者定義分類函數的傳回值 (工作負載群組名稱)。 否則，這個資料行會設定為 NULL。|39|是|  
|ObjectName|**nvarchar(256)**|使用者定義之分類函數的兩段式名稱。 例如，dbo.classifier。|34|是|  
  
## <a name="see-also"></a>另請參閱  
 [擴充事件](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Starting 事件類別](../../relational-databases/event-classes/preconnect-starting-event-class.md)   
 [資源管理員](../../relational-databases/resource-governor/resource-governor.md)  
  
  
