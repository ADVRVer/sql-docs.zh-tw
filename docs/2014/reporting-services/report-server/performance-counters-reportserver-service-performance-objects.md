---
title: 'Reportserver: Service 和 reportserversharepoint: Service 效能物件的效能計數器 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Server service, performance counters
ms.assetid: 2bcacab2-3a4f-4aae-b123-19d756b9b9ed
caps.latest.revision: 23
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c0573346427258d9b79188852c8d6e13af1cb8d1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238388"
---
# <a name="performance-counters-for-the-reportserverservice--and-reportserversharepointservice-performance-objects"></a>ReportServer:Service 和 ReportServerSharePoint:Service 效能物件的效能計數器
  本主題描述下列 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 效能物件的效能計數器：  
  
-   `ReportServer:Service`  
  
-   `ReportServerSharePoint:Service`  
  
> [!NOTE]  
>  效能物件是用來監視本機報表伺服器的事件。 如果您是在向外延展部署中執行報表伺服器，則計數會套用到目前的伺服器，而非整個向外延展部署。  
  
 Windows 效能監視器 (**Perfmon.exe**) 中提供了效能物件。 如需詳細資訊，請參閱 Windows 文件集。 [執行階段分析](http://msdn.microsoft.com/library/w4bz2147.aspx) (http://msdn.microsoft.com/library/w4bz2147.aspx)。  
  
 本主題內容：  
  
-   [ReportServer:Service 效能計數器 (原生模式報表伺服器)](#bkmk_ReportServer)  
  
-   [ReportServerSharePoint:Service (SharePoint 模式報表伺服器)](#bkmk_ReportServerSharePoint)  
  
-   [使用 PowerShell 指令程式傳回清單](#bkmk_powershell)  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式 |原生模式。  
  
##  <a name="bkmk_ReportServer"></a> ReportServer:Service 效能計數器 (原生模式報表伺服器)  
 `ReportServer:Service` 效能物件包含一組計數器集合，用來追蹤報表伺服器執行個體的 HTTP 相關事件和記憶體相關事件。 此效能物件會出現一次，每個[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]執行個體的電腦，然後您可以新增或移除每個執行個體的效能物件計數器。 預設執行個體的計數器會以 `ReportServer:Service` 格式顯示。 計數器會以具名執行個體出現在格式`ReportServer$<` *instance_name*`>:Service`。  
  
 `ReportServer:Service`效能物件的新功能[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]，並提供已使用網際網路資訊服務 (IIS) 中包含的計數器子集並[!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]在舊版的[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]。 這些新的計數器是 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 特有的，而且它們會追蹤報表伺服器的 HTTP 相關事件，例如要求、連接和登入嘗試。 此外，這個效能物件包含可追蹤記憶體管理事件的計數器。  
  
 下表列出中包含的計數器`ReportServer:Service`效能物件。  
  
 ![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容") 以下 Windows PowerShell 指令碼將會傳回 CounterSetName 的效能計數器清單。  
  
```  
(get-counter -listset "ReportServer:Service").paths  
```  
  
|計數器|描述|  
|-------------|-----------------|  
|`Active connections`|目前在伺服器上作用中的連接數目。|  
|`Bytes Received Total`|伺服器所接收的位元組數目。 這個計數器會計算報表管理員和報表伺服器所接收的原始位元組總計。|  
|`Bytes Received/sec`|伺服器每秒所接收的位元組數目。 只有當傳送完成時，才會更新這個計數器。 這表示此計數器會維持 0，然後此值在傳送完成之後才會增加。|  
|`Bytes Sent Total`|伺服器所傳送的位元組數目。 這個計數器會計算報表管理員和報表伺服器所傳送的原始位元組總計。|  
|`Bytes Sent/sec`|伺服器每秒所傳送的位元組數目。 只有當傳送完成時，才會更新這個計數器。 這表示此計數器會維持 0，然後此值在傳送完成之後才會增加。|  
|`Errors Total`|在處理 HTTP 要求期間發生的錯誤總數。 這些錯誤包括 400s 和 500s 中的 HTTP 狀態碼。|  
|`Errors/sec`|在處理 HTTP 要求期間每秒發生的錯誤總數。 這些錯誤包括 400s 和 500s 中的 HTTP 狀態碼。|  
|`Logon Attempts Total`|RSWindows 驗證類型已經嘗試登入的次數。 RSWindows 驗證類型包括 RSWindowsNegotiate、RSWindowsNTLM、RSWindowsKerberos 和 RSWindowsBasic。 值為零 (0) 表示自訂驗證。|  
|`Logon Attempts/sec`|嘗試登入的速率。|  
|`Logon Successes Total`|RSWindows 驗證類型成功登入的次數。 RSWindows 驗證類型包括 RSWindowsNegotiate、RSWindowsNTLM、RSWindowsKerberos 和 RSWindowsBasic。 值為零 (0) 表示自訂驗證。|  
|`Logon Successes/sec`|成功登入的速率。|  
|`Memory Pressure State`|下列其中一個數字 (從 1 到 5)，表示伺服器目前的記憶體狀態：<br /><br /> 1：沒有壓力<br /><br /> 2：低度壓力<br /><br /> 3：中度壓力<br /><br /> 4：高度壓力<br /><br /> 5：壓力過高|  
|`Memory Shrink Amount`|伺服器要求壓縮使用中記憶體的位元組數目。|  
|`Memory Shrink Notifications/sec`|伺服器在上一秒發出以壓縮使用中記憶體的通知數目。 這個值表示伺服器遇到記憶體壓力的頻率。|  
|`Requests Disconnected`|由於通訊失敗而造成中斷連接的要求數目。|  
|`Requests Executing`|目前正在處理的要求數目。|  
|`Requests Not Authorized`|失敗而且出現 HTTP 401 狀態碼的要求數目。|  
|`Requests Rejected`|由於伺服器資源不足而未處理的要求總數。 這個計數器表示傳回 HTTP 503 狀態碼 (表示伺服器太過忙碌) 的要求數目。|  
|`Requests Total`|報表伺服器服務啟動以來所收到的要求總數。 這個計數器會計算傳送至報表管理員的要求，以及從報表管理員傳送至報表伺服器的要求。|  
|`Requests/sec`|每秒處理的要求數目。 這個值代表應用程式目前的輸送量。|  
|`Tasks Queued`|等候執行緒成為可用於處理的工作數目。 對報表伺服器提出的每一要求會對應到一個或多個工作。 這個計數器只表示準備進行處理的工作數目，並不包括目前執行中的工作數目。|  
  
##  <a name="bkmk_ReportServerSharePoint"></a> ReportServerSharePoint:Service (SharePoint 模式報表伺服器)  
 `ReportServerSharePoint:Service`效能物件中已新增[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]。  
  
 ![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容") 以下 Windows PowerShell 指令碼將會傳回 CounterSetName 的效能計數器清單。  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
|計數器|  
|-------------|  
|`Memory Pressure State`|  
|`Memory Shrink Amount`|  
|`Memory Shrink Notifications/Sec`|  
  
##  <a name="bkmk_powershell"></a> 使用 PowerShell 指令程式傳回清單  
 ![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容") 以下 Windows PowerShell 指令碼將會傳回 CounterSetName “ReportServerSharePoint:Service” 的效能計數器清單：  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
## <a name="see-also"></a>另請參閱  
 [監視報表伺服器效能](monitoring-report-server-performance.md)   
 [MSRS 2014 Web 服務和 MSRS 2014 Windows 服務效能物件的效能計數器&#40;原生模式&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)   
 [效能計數器 MSRS 2014 Web 服務 SharePoint 模式和 MSRS 2014 Windows 服務 SharePoint 模式效能物件&#40;SharePoint 模式&#41;].../ performance-counters-msrs-2011-sharepoint-mode-performance-objects.md）  
  
  
