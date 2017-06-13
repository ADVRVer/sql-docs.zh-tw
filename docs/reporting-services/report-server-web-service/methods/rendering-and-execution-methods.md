---
title: "轉譯及執行方法 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c56c8b0a0fc4e2cb6f6bc78710e6fd4ed8e77cff
ms.contentlocale: zh-tw
ms.lasthandoff: 06/13/2017

---
# <a name="rendering-and-execution-methods"></a>轉譯及執行方法
  您可以使用這些方法來管理項目執行和快取，以及報表轉譯。  
  
|方法|動作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|使項目的快取失效。|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|傳回項目的快取組態，以及描述項目快取複本到期時間的設定。|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|傳回個別項目的執行選項及相關聯的設定。|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|傳回支援的執行設定清單。|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|處理指定的報表，並依照指定的格式轉譯該報表。|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|設定要快取的項目，並提供指定項目快取複本到期時間的設定。|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|設定指定之項目的執行選項及相關聯的執行屬性。|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|產生指定之項目的項目執行快照集。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 Web 服務和.NET Framework 建置應用程式](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [報表伺服器 Web 服務](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [報表伺服器 Web 服務方法](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [技術參考 &#40;SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
