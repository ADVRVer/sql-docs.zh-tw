---
title: 限制利用查詢與交叉分析篩選器軸 (MDX) 查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2a7d69055d3d60f8805a7cf7e8b9f1a98b9c01e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048179"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>利用查詢與 Slicer 軸限制查詢 (MDX)
  在以公式表示多維度運算式 (MDX) SELECT 陳述式時，應用程式一般會檢查 Cube，並將階層集合分割成兩個子集：  
  
-   **查詢座標軸**—為多個成員擷取的資料的階層集合。 如需查詢座標軸的詳細資訊，請參閱[指定查詢座標軸的內容 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)。  
  
-   **Slicer 軸**—為單一成員擷取的資料的階層集合。 如需 Slicer 軸的詳細資訊，請參閱[指定 Slicer 軸的內容 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)。  
  
 因為查詢座標軸與 Slicer 軸可以從即將查詢之 Cube 的多個階層建構，這些用語是用來區別即將查詢的 Cube 所採用的階層跟 MDX 查詢傳回的 Cube 中建立的階層。  
  
 若要查看使用查詢及 Slicer 軸的簡單範例，請參閱[在簡單的範例中使用查詢及 Slicer 軸 &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用成員、 Tuple 和集合&#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [MDX 查詢基礎觀念&#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
