---
title: "使用 Reporting Services 行動報表中的模擬資料 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6baabc36-58fb-4a98-bb9c-c42bafb16d0f
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# 使用 Reporting Services 行動報表中的模擬資料
當您將圖庫元素放在設計介面上時，[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] 會立即產生該元素的模擬資料。 建立行動報表時，這項資料會提供數個實用的用途。   
  
![SS_MRP_SimDataTreeMapProps](../../reporting-services/mobile-reports/media/ss-mrp-simdatatreemapprops.png)  
  
使用設計方法建立行動報表時，模擬資料很有幫助。 一開始即以模擬資料填入元素，可讓您快速建立行動報表原型，但不必處理特定的資料需求。 然後評估這些行動報表的整體美感和效率。  
  
## 使用模擬資料建立 Excel 檔案作為範本  
  
模擬資料也會提供一個範本，精確代表特定行動報表設計的資料需求。   
  
-  按一下 [資料檢視] 右上角的 [匯出所有資料]。   
  
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] 會產生包含模擬資料的 Excel 文件，允許快速替代實際資料以供匯入。   
  
## 模擬資料的運作方式  
  
產生的模擬資料是特別為您正在建立的行動報表所量身打造的。 當您將多個元素放在設計介面上時，相關聯的模擬資料就會成長並變更，在缺乏實際資料的狀況下提供可能的最佳體驗。 這項演進可確保在您以其他方式將額外的數列加入圖表視覺效果或擴充一或多個行動報表元素的範圍時，有額外的欄位和篩選可能性可用。  
  
如前文所述，您可以將模擬資料匯出到 Excel 檔案，為相關聯的行動報表建立完整的資料範本。 您可以將實際資料交換到 Excel 檔案，再將其匯回 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]。   
  
當所有控制項都繫結至實際資料後，行動報表中不再使用的模擬資料表就會自動移除。 您無法在設計介面上移除仍有元素參考的模擬資料表。  
  
>**注意**︰模擬資料不會加入整體行動報表的使用量中，因為它沒有和行動報表序列化，而是在執行階段動態產生的。  
  
### 另請參閱  
- [使用 SQL Server 行動報表發行工具建立與發行行動報表](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  在 [iPad app 中檢視 SQL Server 行動報表和 KPI](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports) (Power BI for iOS)  
-  請參閱 [在 iPhone 應用程式中檢視 SQL Server 行動報表和 KPI (iOS 版 Power BI)](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (iOS 版 Power BI)  
  
  
  
  
  
