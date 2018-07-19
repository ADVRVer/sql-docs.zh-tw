---
title: 變更採礦模型的屬性 |Microsoft 文件
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a3650b284e8817c2b7f8aee6a0beca71c275d6a1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34014845"
---
# <a name="change-the-properties-of-a-mining-model"></a>變更採礦模型的屬性
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  有些採礦模型屬性可套用至整個模型，有些模型屬性只套用至個別資料行。 例如， **Drillthrough** 屬性可套用至整個模型，它指定案例資料是否應該可用於查詢， **Description** 屬性也是這類屬性。 套用至資料行的屬性包含 **Usage** 和 **ModelingFlags**，它們控制資料行中的資料在模型內的使用方式。  
  
 下列模型屬性具有可用於建立運算式或設定複雜模型屬性的進階編輯器。 下列屬性提供：  
  
-   **Filter**：開啟 [[資料集篩選器] 或 [模型篩選器] 對話方塊](http://msdn.microsoft.com/library/a9602174-b7e2-4e16-8ded-dfd8eb9264d7)。  
  
-   **AlgorithmParameters** 屬性︰開啟 [[演算法參數] 對話方塊 &#40;採礦模型檢視&#41;](http://msdn.microsoft.com/library/57f9f6f8-8ca4-4a6e-8f18-85f0571b7060)。  
  
 如需如何在採礦模型中設定屬性的資訊，請參閱[採礦模型資料行](../../analysis-services/data-mining/mining-model-columns.md)。  
  
### <a name="to-change-the-properties-of-a-mining-model"></a>若要變更採礦模型的屬性  
  
1.  在資料採礦設計師的 [採礦模型] 索引標籤中，以滑鼠右鍵按一下包含採礦模型名稱的資料行標題，或方格中包含採礦演算法名稱的資料列，然後選取 [屬性]。  
  
2.  在畫面右側的 [屬性] 視窗中，反白顯示對應到您要變更之屬性的值，然後輸入新值。  
  
     您在設計師中選取其他元素時，新值就會生效。  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a>變更採礦模型資料行的屬性  
  
1.  在資料採礦設計師的 [採礦模型] 索引標籤中，以滑鼠右鍵按一下採礦結構資料行和採礦模型交集方格中的資料格，然後選取 [屬性]。  
  
2.  在畫面右側的 [屬性] 視窗中，反白顯示對應到您要變更之屬性的值，然後輸入新值。  
  
    > [!NOTE]  
    >  如果資料行使用方式是設定為 [忽略]，則資料行的 [屬性] 視窗為空白。  
  
     您在設計師中選取其他元素時，新值就會生效。  
  
## <a name="see-also"></a>另請參閱  
 [採礦模型的工作與操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
