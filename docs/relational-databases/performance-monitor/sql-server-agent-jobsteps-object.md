---
title: SQL Server Agent、JobSteps 物件 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 21835671518515b1efe02698a0f01f4dcd051179
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32951813"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server Agent、JobSteps 物件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的 **JobSteps** 效能物件包含可報告 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟相關資訊的效能計數器。 下表列出這個物件包含的計數器。  
  
 下表包含 **SQLAgent:JobSteps** 計數器。  
  
|[屬性]|描述|  
|----------|-----------------|  
|**Active steps**|此計數器會報告目前在執行中的作業步驟數目。|  
|**Queued steps**|此計數器會報告準備供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行，但尚未開始執行的作業步驟數目。|  
|**Total step retries**|此計數器會報告自從伺服器上次重新啟動之後， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重試作業步驟的總次數。|  
  
 物件中的每個計數器均包含下列執行個體：  
  
|執行個體|描述|  
|--------------|-----------------|  
|**_Total**|所有作業步驟的資訊。|  
|**ActiveScripting**|使用 **ActiveScripting** 子系統之作業步驟的資訊。|  
|**ANALYSISCOMMAND**|使用 ANALYSISCOMMAND 子系統之作業步驟的資訊。|  
|**ANALYSISQUERY**|使用 ANALYSISQUERY 子系統之作業步驟的資訊。|  
|**CmdExec**|使用 **CmdExec** 子系統之作業步驟的資訊。|  
|**Distribution**|使用 **Distribution** 子系統之作業步驟的資訊。|  
|**Dts**|使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 子系統之作業步驟的資訊。|  
|**LogReader**|使用 **LogReader** 子系統之作業步驟的資訊。|  
|**合併式**|使用 **Merge** 子系統之作業步驟的資訊。|  
|**PowerShell**|使用 **PowerShell** 子系統之作業步驟的資訊。|  
|**QueueReader**|使用 **QueueReader** 子系統之作業步驟的資訊。|  
|**快照式**|使用 **Snapshot** 子系統之作業步驟的資訊。|  
|**TSQL**|執行 [!INCLUDE[tsql](../../includes/tsql-md.md)]之作業步驟的資訊。|  
  
## <a name="see-also"></a>另請參閱  
 [管理作業步驟](http://msdn.microsoft.com/library/51352afc-a0a4-428b-8985-f9e58bb57c31)   
 [使用效能物件](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [監視資源使用狀況 &#40;系統監視器&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
