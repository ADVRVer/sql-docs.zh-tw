---
title: Reporting Services 行動報表資料 | Microsoft Docs
ms.date: 02/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b6131f6bce9cb6d1c87a4a75215a906b6d097c7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63129734"
---
# <a name="data-for-reporting-services-mobile-reports"></a>Reporting Services 行動報表資料
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] 資料模型十分簡單。 資料會以資料集的集合形式匯入至 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] 。 資料集之間的正式關聯性不是必要的。 只要符合索引鍵值，就會從某個資料集查閱到另一個資料集。 日期/時間彙總是由行動報表執行階段所處理，而且在不同的資料集之間會相符，即使資料集之間的日期/時間資料粒度不同也是一樣。   
  
您可以從兩種類型的來源匯入資料：   
  
* **本機 Excel 檔案**：選取 Excel 文件，並挑選要匯入的工作表。 匯入之後，會將資料儲存在行動報表定義內。 若要重新整理原始 Excel 檔案中的資料，請使用 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] [資料]  索引標籤右上角的 [重新整理資料]  命令。深入了解[準備 SSRS 行動報表的 Excel 資料](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md)。  
  
* **SQL Server 行動報表發行工具共用資料集**：瀏覽伺服器上的已發行資料集清單，並選取要新增至行動報表的已發行資料集。 根據伺服器資料的行動報表一律會保持連接至原始伺服器資料集，並反映伺服器上資料的最新狀態。 請參閱 [支援的資料來源清單](../report-data/data-sources-supported-by-reporting-services-ssrs.md)。   
  
  深入了解 [如何在行動報表發行工具中取得共用資料集的資料](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)。  
  
將資料匯入 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]之後，行動報表建立和設計經驗的其餘部分會相同，不論資料來源為何。   
  
## <a name="connect-mobile-report-elements-to-data"></a>將行動報表元素連接至資料 ##  
  
每個 SQL Server 行動報表發行工具項目都包含一或多個資料設定。 例如，星形量測計元素包含兩個資料設定︰[主要值] 和 [比較值]。 所有這些設定都只會指向特定資料集中的一個欄位 (資料行)。   
  
行動報表執行階段提供量測計的彙總值 (根據使用者選取)。 請注意，相同星形量測計執行個體的比較值可以繫結至不同資料集中的欄位。   
  
### <a name="see-also"></a>另請參閱  
-  [Prepare data for Reporting Services mobile reports (準備 Reporting Services 行動報表的資料)](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [使用 SQL Server 行動報表發行工具建立與發行行動報表](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [從共用資料集取得資料](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [保留行動報表中 Analysis Services 資料的日期格式](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  

