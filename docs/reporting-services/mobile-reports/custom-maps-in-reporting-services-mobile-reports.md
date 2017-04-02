---
title: "Reporting Services 行動報表中的自訂地圖 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59a4ebad-587a-4770-afcd-c69216b8afd9
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Reporting Services 行動報表中的自訂地圖
[!INCLUDE[PRODUCT_NAME](../../includes/product-name.md)] 的地理對應定義格式，稱為 *ESRI 形狀檔*。  
  
最初由私人公司設計，這是現在大部分 GIS 應用程式廣泛使用的半開放式格式。 為配合這種格式，在定義對應時，[!INCLUDE[PRODUCT_NAME](../../includes/short-product-name.md)] 需要有下列兩個檔案︰  
  
- 用於圖形幾何的 .SHP 檔案  
- 用於中繼資料的 .DBF 檔案  
  
基底檔案名稱必須相符 (例如 *canada.shp* 和 *canada.dbf*)。 中繼資料必須包含 [名稱] 欄位和對應的圖形名稱值 (索引鍵)，以在對應中填入資料時使用。  
  
> **注意**︰SHP 和 DBF 這兩個對應檔案相加不能大於 512 KB。 如果地圖檔案太大，請使用 [http://mapshaper.org/](http://mapshaper.org/) 之類的工具減少其大小。  
  
請參閱如何[將自訂地圖加入行動報表](../../reporting-services/mobile-reports/add-a-custom-map-to-a-reporting-services-mobile-report.md)。  
  
## 技術資訊  
  
- 官方規格︰[http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- Wikipedia 形狀檔：[http://en.wikipedia.org/wiki/Shapefile](http://en.wikipedia.org/wiki/Shapefile)  
  
## 建立及編輯對應幾何  
  
建立和編輯形狀檔是複雜的程序，已超出本文討論範圍。 以下是一些可協助您開始的資源和應用程式︰  
  
- ArcGIS：[http://www.arcgis.com/](http://www.arcgis.com/)  
- MAPublisher plug-in for Adobe Illustrator：[http://www.avenza.com/mapublisher](http://www.avenza.com/mapublisher)  
- QuantumGIS (免費)：[http://www.qgis.org/](http://www.qgis.org/)  
- Manco 形狀檔編輯器：[http://www.mancosoftware.com/ShapeFileEditor](http://www.mancosoftware.com/ShapeFileEditor)  
  
## 現有的形狀檔  
  
網路上有很多現成的形狀檔可以下載，例如︰  
  
- Diva-GIS：[http://www.diva-gis.org/Data](http://www.diva-gis.org/Data)  
- OpenStreetMap：[http://openstreetmapdata.com/data](http://openstreetmapdata.com/data)  
- GeoCommons：[http://www.geocommons.com/](http://www.geocommons.com/)  
  
### 另請參閱  
- [Reporting Services 行動報表中的地圖](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [使用 SQL Server 行動報表發行工具建立與發行行動報表](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
