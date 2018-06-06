---
title: 變更採礦模型中的資料行的離散化 |Microsoft 文件
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e9d6b2c75becad147e196534bb4d366dff01a13d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>變更採礦模型中的資料行離散化
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在某些情況下會自動離散化值，也就是說，它會在數值資料行中分類收納資料。 例如，如果您的資料包含連續數值資料，而且您要建立決策樹模型，則連續資料的每一個資料行都將會自動分類收納 (視資料的分佈而定)。 如果您想要控制資料離散化的方式，您必須在採礦結構資料行上，變更可控制資料在模型內之使用方式的屬性。  
  
 如需如何在採礦模型中設定屬性的一般資訊，請參閱 [採礦模型資料行](../../analysis-services/data-mining/mining-model-columns.md)。  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>顯示採礦模型資料行的屬性  
  
1.  在資料採礦設計師的 [採礦模型] 索引標籤上，以滑鼠右鍵按一下包含採礦模型名稱的資料行標頭，或是方格中包含採礦演算法名稱的資料列，然後選取 [屬性]。  
  
     **[屬性]** 視窗會顯示在整體上與採礦模型相關聯的屬性。  
  
2.  在靠近螢幕左邊的 **[結構]** 資料行中，按一下包含您想要離散化之連續數值資料的資料行。  
  
     **[屬性]** 視窗會變更，以便只顯示與該資料行有關聯的屬性。  
  
### <a name="to-change-the-discretization-method"></a>變更離散化方法  
  
1.  在 **[採礦屬性]** 視窗中，按一下 **[內容]** 旁邊的文字方塊，然後從下拉式清單中選取 **Discretized** 。  
  
     <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 和 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 屬性現在就會啟用。  
  
2.  在**屬性**視窗中，按一下文字方塊旁邊<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A>並選取下列值之一：**自動**， **EqualAreas**，或**叢集**。  
  
    > [!NOTE]  
    >  如果資料行使用方式是設定為 [忽略]，則資料行的 [屬性] 視窗為空白。  
  
     您在設計師中選取其他元素時，新值就會生效。  
  
3.  在**屬性**視窗中，按一下文字方塊旁邊<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>輸入數字的值。  
  
    > [!NOTE]  
    >  如果您變更這些屬性，就必須重新處理此結構，連同您想要使用新設定的任何模型。  
  
## <a name="see-also"></a>另請參閱  
 [採礦模型的工作與操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
