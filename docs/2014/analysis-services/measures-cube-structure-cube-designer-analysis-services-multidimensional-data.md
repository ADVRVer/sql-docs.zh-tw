---
title: 量值 （Cube 結構索引標籤，Cube 設計師） (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.measurespane.f1
ms.assetid: be70f63b-58f2-4eff-81bc-c86d8229e617
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 90042bb67b29b86941055ed0689a4c7043bfdd6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319458"
---
# <a name="measures-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a>量值 (Cube 結構索引標籤，Cube 設計師) (Analysis Services - 多維度資料)
  使用 **[量值]** 窗格，即可操作 Cube 設計師中之 **[Cube 結構]** 索引標籤上的量值群組和成員。  
  
## <a name="options"></a>選項。  
 [量值]  
 顯示 Cube 中所含的量值群組和量值，視選取的檢視而定：  
  
 trEE  
 顯示量值群組的樹狀檢視，以量值作為子節點。  
  
 展開量值群組以檢視量值。 按一下選取的量值群組或量值，即可分別重新命名量值群組或量值。  
  
 方格  
 顯示量值的方格及其最常存取的屬性。 按一下 **[加入新的量值]** ，即可顯示 **[新增量值]** 對話方塊，並將新的量值加入至方格。  
  
 方格包含下列資料行：  
  
 [量值]  
 鍵入量值的名稱。  
  
 量值群組  
 顯示包含量值的量值群組。  
  
 資料類型  
 選取量值的資料類型。  
  
 彙總  
 選取量值的彙總函式。  
  
## <a name="context-menu"></a>操作功能表  
 以滑鼠右鍵按一下 [量值] 窗格，即可顯示提供下列選項的操作功能表：  
  
 **新的量值**  
 選取即可顯示 [新增量值] 對話方塊，並將新的量值加入目前在 [量值] 窗格中選取的量值群組。  
  
 **新的量值群組**  
 選取即可顯示 [新增量值群組] 對話方塊，並將新的量值群組加入 [量值] 窗格。  
  
 **顯示在量值**  
 選取即可循環切換下列選項，或選取下列其中一個選項來變更 [量值] 窗格的檢視：  
  
|選項|定義|  
|------------|----------------|  
|**樹狀結構**|在樹狀檢視中顯示量值群組與量值。|  
|**方格**|在方格中顯示量值群組與量值。|  
  
 **重新命名**  
 選取即可重新命名選取的量值群組或量值。  
  
 **刪除**  
 選取即可顯示 [刪除物件] 對話方塊，並刪除在 [量值] 窗格中選取的物件。  
  
 **上移**  
 選取即可將選取的量值群組或量值上移一個位置。  
  
> [!NOTE]  
>  如果選取的項目無法上移，此選項會停用。  
  
 **下移**  
 選取即可將選取的量值群組或量值下移一個位置。  
  
> [!NOTE]  
>  如果選取的項目無法下移，此選項會停用。  
  
 **新增連結的物件**  
 按一下即可顯示 **[連結物件精靈]** 來連結其他 Cube 的量值群組和維度，以及匯入動作、KPI 和計算到所選取的 Cube 中。  
  
 **屬性**  
 選取即可顯示選取的量值群組或量值之 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [屬性] 視窗。  
  
## <a name="see-also"></a>另請參閱  
 [設定量值屬性](multidimensional-models/configure-measure-properties.md)   
 [量值和量值群組](multidimensional-models/measures-and-measure-groups.md)  
  
  
