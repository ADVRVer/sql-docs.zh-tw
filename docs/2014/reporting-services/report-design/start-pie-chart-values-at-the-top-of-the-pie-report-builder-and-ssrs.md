---
title: 從圓形圖頂端開始繪製圓形圖值 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 74eb4008ad9de17c8da8ced5f70d9eba4b0a85a9
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56291546"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>從圓形圖頂端開始繪製圓形圖值 (報表產生器及 SSRS)
  根據預設，在圓形圖中，資料集的第一個值是從 90 度開始 (從圓形圖頂端算起)。 您可能希望第一個值是從頂端開始繪製。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>若要從圓形圖頂端開始繪製圓形圖  
  
1.  按一下圓形圖本身。  
  
2.  如果 [屬性] 窗格沒有開啟，請按一下 [檢視] 索引標籤上的 [屬性]。  
  
3.  在 [屬性] 窗格的 [自訂屬性] 底下，將 [PieStartAngle] 從 **0** 變更為 **270**。  
  
4.  按一下 [執行] 以預覽報表。  
  
 第一個值現在從圓形圖的頂端開始繪製。  
  
## <a name="see-also"></a>另請參閱  
 [格式化圖表 &#40;報表產生器及 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [圓形圖 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
