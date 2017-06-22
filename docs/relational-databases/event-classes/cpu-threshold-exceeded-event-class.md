---
title: "CPU Threshold Exceeded 事件類別 | Microsoft 文件"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 294c3b54c0bba8af05fa7fee98dacbf1598f263a
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="cpu-threshold-exceeded-event-class"></a>CPU Threshold Exceeded 事件類別
  CPU Threshold Exceeded 事件類別會指出資源管理員偵測到某個查詢已經超過針對 REQUEST_MAX_CPU_TIME_SEC 所指定的 CPU 臨界值。  
  
> [!NOTE]  
>  這個事件的偵測間隔為五秒。 這樣會保證如果某個查詢超過指定的限制至少達五秒，就會產生事件。 不過，如果某個查詢超過指定的臨界值少於五秒，根據查詢的時間和上一次偵測清除的時間，可能會遺漏偵測。  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>CPU Threshold Exceeded 資料行  
  
|資料行名稱|資料類型|描述|資料行識別碼|可篩選|  
|----------------------|---------------|-----------------|---------------|----------------|  
|CPU|**int**|CPU 使用量 (以毫秒為單位)。|18|是|  
|EventClass|**int**|214|27|否|  
|EventSubClass|**int**|CPU 限制違規。|21|是|  
|GroupID|**int**|發生違規的群組識別碼。|66|是|  
|OwnerID|**int**|導致違規之處理序的 SPID。|58|是|  
|SPID|**int**|引發此事件之伺服器處理序的識別碼。<br /><br /> 注意：如果系統執行緒將 CPU 使用量驗證為背景工作，這個識別碼可能會與實際的使用者 SPID 不同。|12|是|  
|StartTime|**datetime**|引發此事件的時間。|14|是|  
  
## <a name="see-also"></a>另請參閱  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
