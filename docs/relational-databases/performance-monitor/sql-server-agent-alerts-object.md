---
title: SQL Server Agent、Alerts 物件 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: a5a408ac1329c11054804902f3e751d6126afa4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67987349"
---
# <a name="sql-server-agent-alerts-object"></a>SQL Server Agent、Alerts 物件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  SQL Server Agent 的「 **警示** 」效能物件包含效能計數器，用來報告 SQL Server Agent 警示的詳細資訊。 下表列出這個物件包含的計數器。  
  
 下表包含 **SQLAgent:Alerts** 計數器。  
  
|[屬性]|Description|  
|----------|-----------------|  
|**Activated alerts**|這個計數器報告自從 SQL Server Agent 上次重新啟動後，SQL Server Agent 已啟動的警示總數。|  
|**Alerts activated/minute**|這個計數器報告 SQL Server Agent 在前一分鐘內所啟動的警示數目。|  
  
> [!NOTE]  
>  若要使用此 SQL Server Agent 物件，使用者必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員。  
  
## <a name="see-also"></a>另請參閱  
 [警示](../../ssms/agent/alerts.md)   
 [使用效能物件](../../ssms/agent/use-performance-objects.md)   
 [監視資源使用狀況 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
