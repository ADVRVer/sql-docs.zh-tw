---
title: 正在載入資料 （MDS 增益集適用於 Excel） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 465b14ab5cb96f3f587222427ea793bbaf225b01
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923913"
---
# <a name="loading-data-mds-add-in-for-excel"></a>載入資料 (適用於 Excel 的 MDS 增益集)
  在  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]，您必須將資料從 MDS 儲存機制載入使用中的 Excel 工作表之前，您可以使用它。 當您使用資料完成之後，請將它發行至 MDS 儲存機制，讓其他使用者能夠共用資料。  
  
 您可以載入的資料限制為您有權存取的資料。 存取資料的權限是在 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式中設定，或以程式設計方式設定。  
  
 當您載入大量資料時，可以設定資料載入時間可能很長時所顯示的警告。 若要這樣做，請按一下 [選項] 群組中的 [設定]。 在 [資料] 索引標籤上，選取 [顯示大型資料集的篩選警告]。  
  
> [!WARNING]  
>  啟用 MDS 的活頁簿僅能在 Excel 中使用適用於 Excel 的 MDS 增益集開啟並更新。 不支援在未安裝 MDS Excel 增益集所在電腦上的 Excel 中開啟啟用 MDS 的活頁簿，而且可能會造成活頁簿檔案損毀。 如果您要與其他人共用資料，請以電子郵件傳送捷徑查詢檔案給他們，而不要儲存工作表後以電子郵件傳送該工作表。 如需查詢的詳細資訊，請參閱[以電子郵件傳送捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)。  
  
## <a name="filtering-data"></a>篩選資料  
 您可以限制即將下載的資料量在載入之前篩選資料。 這包括選擇您想要載入的屬性 (資料行)、您想要顯示屬性的順序，以及您想要使用的成員 (資料列)。 如需詳細資訊，請參閱[載入之前篩選資料&#40;MDS 增益集適用於 Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)。  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>自動連接並載入經常使用的資料  
 如果您想要永遠連接到相同的伺服器並且載入相同的資料集，可以建立包含連接和篩選資訊的捷徑查詢檔案。 如需查詢檔案的詳細資訊，請參閱 [捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;](shortcut-query-files-mds-add-in-for-excel.md)。  
  
## <a name="refreshing-data"></a>重新整理資料  
 其他使用者可能會在您載入之後更新 MDS 儲存機制中的資料。 您可以擷取這項資料，而不遺失已經對非 MDS 資料所做的變更。 如需詳細資訊，請參閱[重新整理資料 &#40;適用於 Excel 的 MDS 增益集&#41;](refreshing-data-mds-add-in-for-excel.md)。  
  
## <a name="related-tasks"></a>相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|在將 MDS 資料載入 Excel 之前篩選資料。|[載入之前篩選資料&#40;MDS 增益集的 Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|將 MDS 資料載入 Excel 中。|[將資料從 MDS 載入 Excel 中](export-data-to-excel-from-master-data-services.md)|  
|在下載資料之前變更資料行的順序。|[重新排序資料行 &#40;適用於 Excel 的 MDS 增益集&#41;](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>相關內容  
  
-   [連接 &#40;適用於 Excel 的 MDS 增益集&#41;](connections-mds-add-in-for-excel.md)  
  
-   [捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [適用於 Microsoft Excel 的 Master Data Services 增益集](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [安全性 &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  
