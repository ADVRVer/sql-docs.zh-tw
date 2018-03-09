---
title: "部署資料處理延伸模組 | Microsoft Docs"
ms.custom: 
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
caps.latest.revision: "34"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b8bf715c5b1a5bc5bac5b1bfe31770035f41cfbc
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="deploying-a-data-processing-extension"></a>部署資料處理延伸模組
  一旦您撰寫 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 資料處理延伸模組並將其編譯成 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 程式庫之後，需要使其可供報表伺服器和報表設計師探索。 完成此項動作很簡單，只要將伸模組複製到適當的目錄，並將項目加入適當的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 組態檔即可。  
  
## <a name="configuration-file-extension-element"></a>組態檔延伸模組元素  
 部署到報表伺服器或是報表設計師的資料處理延伸模組，需要在設定檔中輸入成 **Extension** 項目。 這些檔案在報表伺服器中為 RSReportServer.config，在報表設計師中為 RSReportDesigner.config。  
  
 下表描述資料處理延伸模組之 **Extension** 項目的屬性。  
  
|attribute|描述|  
|---------------|-----------------|  
|**名稱**|例如，就延伸模組的維一名稱而言，"SQL" 為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料處理延伸模組，或者 "OLEDB" 為 OLE DB 資料處理延伸模組。 **Name** 屬性的最大長度為 255 個字元。 該名稱在組態檔之 **Extension** 元素的所有元素中，必須是唯一的。|  
|**型別**|以逗號分隔的清單，包括完整的命名空間以及組件的名稱。|  
|**Visible**|**false** 的值指出在使用者介面中應該看不到資料處理延伸模組。 如果沒有包括屬性，預設值是 **true**。|  
  
 如需 RSReportServer.config 或 RSReportDesigner.config 檔的詳細資訊，請參閱 [Reporting Services 設定檔](../../../reporting-services/report-server/reporting-services-configuration-files.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[如何：將資料處理延伸模組部署到報表伺服器](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-a-report-server.md)|描述如何將資料處理延伸模組部署到報表伺服器。|  
|[如何：將資料處理延伸模組部署到報表設計師](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md)|描述如何將資料處理延伸模組部署到報表設計師。|  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 延伸模組](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [實作資料處理延伸模組](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 延伸模組程式庫](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
