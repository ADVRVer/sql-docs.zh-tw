---
title: "使用特定查詢字串參數開啟行動報表 | Microsoft Docs"
ms.custom: 
ms.date: 10/25/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: mobile-reports
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4eeb3204-e207-4ac0-aff3-bfc4926e5754
caps.latest.revision: "5"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6f7b4c90b317cbf31ce1414a9910798e149b5794
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="open-a-mobile-report-with-specific-query-string-parameters--reporting-services"></a>使用特定查詢字串參數開啟行動報表 | Reporting Services
如果您的 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 行動報表具有參數與 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] 資料來源，則可以在報表 URL 中包括查詢字串參數，以使用您所指定的值自動開啟報表。 
1.  建立 [含參數的行動報表](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)。

2. 在行動報表發行工具中開啟報表，然後選取 [資料] 索引標籤。 

2. 在資料表底部的索引標籤上尋找資料集的名稱，以及您要的欄位名稱。 
    
    ![mobile-report-publisher-parameter-data-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-data-view.png)
    
2.  URL 的語法取決於您的資料來源。 

     **針對 SQL Server Analysis Services 資料來源**：使用此格式建置具有查詢字串參數的 URL：

    `http://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.<field-name>=<parameter-value>`

    例如：
    
    `http://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.category=Clothing` 
    
     **針對 SQL Server 資料來源**：查詢字串參數大致相同，但是在欄位名稱前要有 @ 符號：

    `http://<servername>/reports/<report-folder-name>/<report-name>?<dataset-name>.@<field-name>=<parameter-value>`

    例如：
    
      `http://sampleserver/reports/adventureworks-reports/adventureworks-load-on-demand?TimeChartLoD.@category=Clothing` 

    
3.  此 URL 會在伺服器上開啟報表，並自動篩選至您指定的參數值。

    ![mobile-report-publisher-parameter-web-portal-view](../../reporting-services/mobile-reports/media/mobile-report-publisher-parameter-web-portal-view.png)

### <a name="see-also"></a>另請參閱

[將參數加入行動報表中](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)

