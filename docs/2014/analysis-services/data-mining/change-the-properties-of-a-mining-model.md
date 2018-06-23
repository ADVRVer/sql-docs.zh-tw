---
title: 變更採礦模型的屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 28e417708981a7184caa62ae74fe681397411d78
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36034068"
---
# <a name="change-the-properties-of-a-mining-model"></a>變更採礦模型的屬性
  有些採礦模型屬性可套用至整個模型，有些模型屬性只套用至個別資料行。 套用至整個模型屬性的範例是`Drillthrough`屬性，指定是否應該可用於查詢案例資料，而`Description`屬性。 套用至資料行的屬性包含 `Usage` 和 `ModelingFlags`，它們控制資料行中的資料在模型內的使用方式。  
  
 下列模型屬性具有可用於建立運算式或設定複雜模型屬性的進階編輯器。 下列屬性提供：  
  
-   `Filter` 屬性： 開啟[資料集篩選器或模型篩選器對話方塊](../data-set-filter-or-model-filter-dialog-box.md)。  
  
-   `AlgorithmParameters` 屬性： 開啟[演算法參數對話方塊&#40;採礦模型檢視&#41;](../algorithm-parameters-dialog-box-mining-models-view.md)。  
  
 如需如何在採礦模型中設定屬性的資訊，請參閱[採礦模型資料行](mining-model-columns.md)。  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>若要變更採礦模型的屬性  
  
1.  在資料採礦設計師的 [採礦模型] 索引標籤中，以滑鼠右鍵按一下包含採礦模型名稱的資料行標題，或方格中包含採礦演算法名稱的資料列，然後選取 [屬性]。  
  
2.  在畫面右側的 [屬性] 視窗中，反白顯示對應到您要變更之屬性的值，然後輸入新值。  
  
     您在設計師中選取其他元素時，新值就會生效。  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>變更採礦模型資料行的屬性  
  
1.  在資料採礦設計師的 [採礦模型] 索引標籤中，以滑鼠右鍵按一下採礦結構資料行和採礦模型交集方格中的資料格，然後選取 [屬性]。  
  
2.  在畫面右側的 [屬性] 視窗中，反白顯示對應到您要變更之屬性的值，然後輸入新值。  
  
    > [!NOTE]  
    >  如果資料行使用方式設為`Ignore`、**屬性**視窗資料行是空白。  
  
     您在設計師中選取其他元素時，新值就會生效。  
  
## <a name="see-also"></a>另請參閱  
 [採礦模型工作和操作說明](mining-model-tasks-and-how-tos.md)  
  
  