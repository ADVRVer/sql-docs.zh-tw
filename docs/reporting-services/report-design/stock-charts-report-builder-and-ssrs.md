---
title: 股票圖 (報表產生器) | Microsoft Docs
description: 在報表產生器中透過標記 (例如線條或三角形)，針對每個資料點使用最多四個值，以顯示財務或科學資料。
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: f75ca11e-b7f5-4ac0-ba17-fe6f82742dad
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 40a9ab1568ab2b61a1582f3dfbc62badbd480a1f
ms.sourcegitcommit: f898aa83561e94626024916932568ab05e73b656
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84012426"
---
# <a name="stock-charts-report-builder-and-ssrs"></a>股票圖 (報表產生器及 SSRS)

  股票圖是特別針對每個資料點最多使用四個值的財務或科學資料而設計的。 這些值會讓用於繪製財務股票資料的最高值、最低值、開盤值與收盤值排成一列。 此圖表類型會使用標記 (通常是線條或三角形) 來顯示開盤值與收盤值。 在下列範例中，開盤值以左方的標記顯示，而收盤值以右方的標記顯示。  
  
 ![股票圖](../../reporting-services/report-design/media/rs-stockchart.gif "股票圖")  
  
 股票圖的例子可從範例報表產生器報表取得。 如需下載這個範例報表及其他項目的詳細資訊，請參閱 [報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)：  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>變化  
  
-   **K 線圖**： K 線圖是一種特殊形式的股票圖，其中的方塊用於顯示開盤值與收盤值之間的範圍。 K 線圖就像股票圖一樣，最多可以在每個資料點顯示四個值。  
  
## <a name="data-considerations-for-stock-charts"></a>股票圖的資料考量  
  
-   顯示多個股票資料點 (例如，年股價趨勢) 時，很難區分每個資料點的每個開盤值、收盤值、最高值與最低值。 在此狀況下，請考慮使用折線圖而非股票圖。  
  
-   產生軸標籤時，標記通常會從零開始。  一般而言，股價的變動程度與其他資料集的變動程度不同。 因此，您可能想要停用從零開始的軸標籤，才能得到較佳的資料檢視。 若要這樣做，請在 **[軸屬性]** 對話方塊或 [屬性] 視窗中，將 **IncludeZero** 設定為 **false** 。 如需圖表如何產生軸標籤的詳細資訊，請參閱[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供許多計算公式搭配股票圖使用，包括「價格指標」、「相對強弱指標 (Relative Strength Index)」、MACD 等等。  

## <a name="next-steps"></a>後續步驟

[範圍圖表](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md)   
[圖表](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[格式化圖表](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
[軸屬性對話方塊、軸選項](https://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)  

更多問題嗎？ [請嘗試詢問 Reporting Services 論壇](https://go.microsoft.com/fwlink/?LinkId=620231)
