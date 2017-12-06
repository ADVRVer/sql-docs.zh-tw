---
title: "報表伺服器系統屬性 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- report servers [Reporting Services], properties
- system-specific properties [Reporting Services]
ms.assetid: cd874117-00e5-4ae6-8629-eb9ba9f40478
caps.latest.revision: "55"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f53a913a1e326d7e39843aeae4c45de4cca88f98
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2017
---
# <a name="reporting-services-properties---report-server-system-properties"></a>Reporting Services 屬性 - 報表伺服器系統屬性
  下列系統屬性名稱會保留。 您無法建立具有相同名稱的使用者定義屬性。 您可以使用 Web 服務方法，來讀取或是修改大部分屬性。  
  
## <a name="properties"></a>屬性  
  
|屬性|Description|  
|--------------|-----------------|  
|SiteName|顯示在使用者介面上的報表伺服器網站名稱。 預設值為 **Microsoft 報表伺服器**。 這個屬性可以是空字串。 最大長度是 8,000 個字元。|  
|SystemSnapshotLimit|針對報表所儲存之快照集的最大數目。 有效值是 **-1** 到 **2**,**147**,**483**,**647**。 如果此值為 **-1**，表示沒有任何快照集限制。|  
|SystemReportTimeout|在報表伺服器命名空間中管理之所有報表的預設報表處理逾時值 (以秒為單位)。 在報表層級可以覆寫這個值。 如果已設定此屬性，當指定的時間已過期時，報表伺服器就會嘗試停止處理報表。 有效值是 **-1** 到 **2**,**147**,**483**,**647**。 如果此值為 **-1**，命名空間中的報表就不會在處理期間逾時。 預設值是 **1800**秒。|  
|UseSessionCookies|指出報表伺服器與用戶端瀏覽器通訊時是否應該使用工作階段 Cookie。 預設值為 **true**。|  
|SessionTimeout|工作階段維持作用中狀態的時間長度 (以秒為單位)。 預設值是 **600**秒。|  
|EnableMyReports|指出 [我的報表] 功能是否已啟用。 值若為 **true** 表示此功能已啟用。|  
|MyReportsRole|在使用者之 [我的報表] 資料夾上建立安全性原則時所使用的角色名稱。 預設值是 **My Reports Role**秒。|  
|EnableExecutionLogging|指出報表執行記錄是否已啟用。 預設值為 **true**。|  
|ExecutionLogDaysKept|要將報表執行資訊保留在執行記錄中的天數。 這個屬性的有效值包括 **0** 至 **2**、**147**、**483**和**647**。 如果此值為 **0** ，系統就不會從執行記錄資料表中刪除項目。 預設值是 **60**秒。|  
|SnapshotCompression|定義快照集的壓縮方式。 預設值是 **SQL**秒。 有效值如下：<br /><br /> **SQL** = 當快照集儲存在報表伺服器資料庫時，系統會壓縮快照集。 這是目前的行為。<br /><br /> **無 =** 系統不會壓縮快照集。<br /><br /> **全部** = 系統會針對所有儲存選項壓縮快照集，包括報表伺服器資料庫或是檔案系統。|  
|EnableClientPrinting|決定是否可從報表伺服器下載 RSClientPrint ActiveX 控制項。 有效值為 **true** 和 **false**。 預設值為 **true**。 如需此控制項所需之其他設定的詳細資訊，請參閱 [啟用和停用 Reporting Services 的用戶端列印功能](../../../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)。|  
|EnableIntegratedSecurity|決定整合式安全性是否支援報表資料來源連接。 預設值為 **True**。 有效值如下：<br /><br /> **True** = 整合式安全性已啟用。<br /><br /> **False** = 整合式安全性未啟用。 設定為使用整合式安全性的報表資料來源不會執行。|  
|EnableRemoteErrors|包含外部錯誤資訊 (例如，有關報表資料來源的錯誤資訊) 以及針對從遠端電腦要求報表之使用者傳回的錯誤訊息。 有效值為 **true** 和 **false**。 預設值是 **false**秒。 如需詳細資訊，請參閱[啟用遠端錯誤 &#40;Reporting Services&#41;](../../../reporting-services/report-server/enable-remote-errors-reporting-services.md)。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>   
 <xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>   
 [使用 Web 服務和 .NET Framework 建置應用程式](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [報表伺服器 Web 服務](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [技術參考 &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
