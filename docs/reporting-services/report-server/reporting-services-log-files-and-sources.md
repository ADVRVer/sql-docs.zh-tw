---
title: "Reporting Services 記錄檔和來源 |Microsoft 文件"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting [Reporting Services], log files
- logs [Reporting Services]
- logs [Reporting Services], about log files
- report servers [Reporting Services], log files
- report server log files
- files [Reporting Services], logs
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
caps.latest.revision: 49
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 08686f83b78c783e1d82c144e4a06f9ecd52bde0
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="reporting-services-log-files-and-sources"></a>Reporting Services 記錄檔和來源
  報表伺服器和報表伺服器環境會使用各種記錄目的地，以記錄有關伺服器作業與狀態的資訊。 記錄有兩個基本的類別目錄，也就是執行記錄和追蹤記錄。 執行記錄包含有關報表執行統計資料、稽核、效能診斷與最佳化的資訊。 追蹤記錄是有關錯誤訊息與一般診斷的資訊。  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式  
  
 下表提供有關每一個記錄檔之其他資訊的連結，包括記錄檔位置以及如何檢視記錄檔內容。  
  
|Log|說明|  
|---------|-----------------|  
|[報表伺服器執行記錄和 ExecutionLog3 檢視](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)|執行記錄檔是儲存在報表伺服器資料庫中的 SQL Server 檢視。<br /><br /> 報表伺服器執行記錄包含有關特定報表的資料，包括何時執行報表、誰執行、傳遞到何處及使用何種轉譯格式。|  
|SharePoint 追蹤記錄|如果是在 SharePoint 中執行的報表伺服器，SharePoint 追蹤記錄會包含 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資訊。 您也可以針對 SharePoint 統一記錄服務，設定 [!INCLUDE[ssRS](../../includes/ssrs-md.md)] 的特定資訊。 如需詳細資訊，請參閱[開啟 SharePoint 追蹤記錄的 Reporting Services 事件 &#40;ULS&#41;](../../reporting-services/report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)|  
|[報表伺服器服務追蹤記錄](../../reporting-services/report-server/report-server-service-trace-log.md)|服務追蹤記錄包含非常詳細的資訊，在您偵錯應用程式或調查問題或事件時很有用。 追蹤記錄檔是 ReportServerService_\<時間戳記 >.log 且位於下列資料夾：<br /><br /> `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles`|  
|[報表伺服器 HTTP 記錄](../../reporting-services/report-server/report-server-http-log.md)|HTTP 記錄檔包含報表伺服器 Web 服務和報表管理員所處理之所有 HTTP 要求與回應的記錄。|  
|[Windows 應用程式記錄檔](../../reporting-services/report-server/windows-application-log.md)|Microsoft Windows 應用程式記錄包含有關報表伺服器事件的資訊。|  
|Windows 效能記錄|Windows 效能記錄包含報表伺服器的效能資料。 您可以建立效能記錄，然後選擇計數器來決定要收集的資料。 如需詳細資訊，請參閱＜ [Monitoring Report Server Performance](../../reporting-services/report-server/monitoring-report-server-performance.md)＞。|  
|SQL Server 安裝程式記錄檔|記錄檔也是在安裝期間建立。 如果安裝失敗，或雖然成功但出現警告或其他訊息，您可以檢查記錄檔來排除問題。 如需詳細資訊，請參閱＜ [View and Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)＞。|  
|IIS 記錄|由 Microsoft Internet Information Services (IIS) 建立的記錄檔 如需詳細資訊，請參閱 [如何在 Internet Information Services (IIS) 中啟用記錄](http://support.microsoft.com/kb/313437) (http://support.microsoft.com/kb/313437)。|  
  
## <a name="see-also"></a>請參閱＜  
 [Reporting Services 報表伺服器 &#40;原生模式&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [錯誤和事件參考 &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
