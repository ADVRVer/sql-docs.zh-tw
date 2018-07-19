---
title: 散佈圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2520ae24-0609-4890-807d-3267018aba8e
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 36f9a03b98c46cdd8f1cba5e62e6e448e0df8efb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282644"
---
# <a name="scatter-charts-report-builder-and-ssrs"></a>散佈圖 (報表產生器及 SSRS)
  散佈圖會將數列顯示成一組點。 這些值會以點在圖表上的位置來表示。 類別目錄會由圖表上不同的標記來表示。 散佈圖通常用來比較跨越類別目錄的彙總資料。 如需有關如何將資料加入至散佈圖的詳細資訊，請參閱 <<c0> [ 圖表&#40;報表產生器及 SSRS&#41;</c0>](charts-report-builder-and-ssrs.md)  
  
 下圖顯示散佈圖的範例。  
  
 ![散佈圖](../media/rs-scatterchart.gif "散佈圖")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>變數  
  
-   **泡泡圖。** 泡泡圖會根據泡泡的大小，顯示資料點的兩個值之間的差異。 較大的泡泡，也就是兩個值之間較大的差異。  
  
-   **立體泡泡圖**。 泡泡圖以立體方式顯示。  
  
## <a name="data-considerations-for-a-scatter-chart"></a>散佈圖的資料考量  
  
-   散佈圖通常用於顯示與比較數值，例如，科學、統計與工程資料。  
  
-   當您想要在不管時間的情況下比較大量資料點時，請使用散佈圖。 您在散佈圖中包含越多資料，您就可以達到越好的比較結果。  
  
-   泡泡圖的每個資料點都需要兩個值 (頂端和底部)。  
  
-   散佈圖適合處理值的分佈與資料點的群集。 如果您的資料集包含許多點 (例如，數千個點)，則這是最佳的圖表類型。 在點圖上顯示多個數列會擾亂視覺，應該予以避免。 在此狀況下，請考慮使用折線圖。  
  
-   根據預設，散佈圖會將資料點顯示為圓形。 如果您在散佈圖上有多個數列，請考慮將每個點的標記形狀變更為正方形、三角形、菱形或其他形狀。  
  
## <a name="see-also"></a>另請參閱  
 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [折線圖&#40;報表產生器及 SSRS&#41;](line-charts-report-builder-and-ssrs.md)  
  
  
