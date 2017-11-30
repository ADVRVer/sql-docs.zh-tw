---
title: "建立 Reporting Services 行動報表時應該設計優先還是資料優先 | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 02/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7b355fa-312b-4074-bc9b-776269d4fb51
caps.latest.revision: "17"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 4794afd8a2226271e9ba9db2ec4d7926c672d590
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="design-first-or-data-first-when-creating-in-reporting-services-mobile-reports"></a>建立 Reporting Services 行動報表時設計優先還是資料優先
  
您可以使用 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)]，在可調整方格資料列和資料行且具有彈性行動報表元素的設計介面上，快速建立適用於任何畫面大小的行動報表。   
  
建立行動報表時，您可以選擇兩種基本方法︰從資料優先開始或設計優先開始。 [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] 支援兩者。   
  
## <a name="design-first"></a>設計優先  
  
下圖顯示 [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] 版面配置檢視的元件：   
  
![SS_MRP_LayoutTab](../../reporting-services/mobile-reports/media/ss-mrp-layouttab.png)  
  
在設計優先方法中，您先建立行動報表版面配置，而未匯入任何資料。 這適合在不確定資料格式是否正確時建立行動報表。 如果沒有實際資料，圖庫元素會自動繫結至已產生的模擬資料，您可以匯出這些模擬資料，並將其作為描述所需資料的範本。  
  
## <a name="data-first"></a>資料優先  
資料優先方法是先匯入所有必要資料，接著設計行動報表，然後設定行動報表元素的資料屬性。 這樣做的優點是在將每個元素加入版面配置時，可以將其連接至實際資料。 使用資料優先方法時，實際資料的格式必須正確，才能與 [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)]搭配使用。   
  
 下圖顯示 [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] 資料檢視的所有元件：  
  
![SS_MRP_DataTab](../../reporting-services/mobile-reports/media/ss-mrp-datatab.png)  
  
### <a name="see-also"></a>另請參閱  
- [使用 SQL Server 行動報表發行工具建立與發行行動報表](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  在 [iPad app 中檢視 SQL Server 行動報表和 KPI](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI for iOS)  
-  請參閱 [在 iPhone 應用程式中檢視 SQL Server 行動報表和 KPI (iOS 版 Power BI)](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (iOS 版 Power BI)  
  
  
  
  

