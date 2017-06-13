---
title: "Reporting Services 行動報表中加入自訂地圖 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e38a8b7a03c79a596d2c795b3ee992e974f604cb
ms.contentlocale: zh-tw
ms.lasthandoff: 06/13/2017

---
# <a name="add-a-custom-map-to-a-reporting-services-mobile-report"></a>將自訂地圖加入 Reporting Services 行動報表
自訂地圖需要兩個檔案︰  
* 用於圖形幾何的 .SHP 檔案  
* 用於中繼資料的 .DBF 檔案  
  
請閱讀 [Reporting Services 行動報表中的自訂地圖](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)。  
  
將這兩個檔案儲存在相同的資料夾中。 兩者的檔案名稱必須相符 (例如 canada.shp 和 canada.dbf)。 中繼資料 (DBF file) 必須包含 [名稱] 欄位和地圖的圖形名稱值 (索引鍵)，以在地圖中填入資料時使用。   
  
## <a name="load-a-custom-map"></a>載入自訂地圖  
  
1. 在 [配置] 索引標籤上選取地圖類型：[漸層熱度圖]、[範圍停止熱度圖] 或 [泡泡圖]，將其拖曳至設計介面，並調整為您想要的大小。  
  
   ![SSMRP_MapsGallery](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
2. 在 [配置] 檢視 > [視覺屬性] 面板 > [地圖] 中，選取 [Custom Map From File] (檔案的自訂地圖)。   
  
   ![SSMRP_SelectCustomMap](../../reporting-services/mobile-reports/media/ssmrp-selectcustommap.png)  
  
3. 在 [開啟] 對話方塊中，瀏覽至 SHP 和 DBF 檔案的位置，然後選取兩者。   
  
   ![SSMRP_SelectDBFandSHP](../../reporting-services/mobile-reports/media/ssmrp-selectdbfandshp.png)  
  
## <a name="connect-data-to-a-custom-map"></a>將資料連接至自訂地圖  
當您首次將自訂地圖加入報表時， [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] 會將模擬的地理資料填入其中。  
  
![SSMRP_MapsData](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
在自訂地圖中顯示實際資料如同在內建地圖中顯示資料。 請遵循 [Reporting Services 行動報表中的地圖](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md) 中的步驟，來顯示資料。  
  
### <a name="see-also"></a>另請參閱  
- [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Reporting Services 行動報表中的地圖](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [使用 SQL Server 行動報表發行工具建立與發行行動報表](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  

