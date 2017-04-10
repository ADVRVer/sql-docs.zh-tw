---
title: "變更採礦模型中的資料行離散化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分隔 [Analysis Services]"
  - "採礦結構 [Analysis Services]，使用說明主題"
  - "離散化資料行 [資料採礦]"
  - "值區問題 [Analysis Services]"
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 14
---
# 變更採礦模型中的資料行離散化
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在某些情況下會自動離散化值，也就是說，它會在數值資料行中分類收納資料。 例如，如果您的資料包含連續數值資料，而且您要建立決策樹模型，則連續資料的每一個資料行都將會自動分類收納 (視資料的分佈而定)。 如果您想要控制資料離散化的方式，您必須在採礦結構資料行上，變更可控制資料在模型內之使用方式的屬性。  
  
 如需如何在採礦模型中設定屬性的一般資訊，請參閱[採礦模型資料行](../../analysis-services/data-mining/mining-model-columns.md)。  
  
### 顯示採礦模型資料行的屬性  
  
1.  在資料採礦設計師的 [採礦模型] 索引標籤上，以滑鼠右鍵按一下包含採礦模型名稱的資料行標頭，或是方格中包含採礦演算法名稱的資料列，然後選取 [屬性]。  
  
     **[屬性]** 視窗會顯示在整體上與採礦模型相關聯的屬性。  
  
2.  在靠近螢幕左邊的 **[結構]** 資料行中，按一下包含您想要離散化之連續數值資料的資料行。  
  
     **[屬性]** 視窗會變更，以便只顯示與該資料行有關聯的屬性。  
  
### 變更離散化方法  
  
1.  在 **[採礦屬性]** 視窗中，按一下 **[內容]**旁邊的文字方塊，然後從下拉式清單中選取 **Discretized** 。  
  
     <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 和 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 屬性現在就會啟用。  
  
2.  在 [屬性] 視窗中，按一下 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 旁邊的文字方塊，然後選取下列其中一個值：[Automatic]、[EqualAreas] 或 [Cluster]。  
  
    > [!NOTE]  
    >  如果資料行使用方式是設定為 [忽略]，則資料行的 [屬性] 視窗為空白。  
  
     您在設計師中選取其他元素時，新值就會生效。  
  
3.  在 [屬性] 視窗中，按一下 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 旁邊的文字方塊，然後輸入數值。  
  
    > [!NOTE]  
    >  如果您變更這些屬性，就必須重新處理此結構，連同您想要使用新設定的任何模型。  
  
## 請參閱＜  
 [採礦模型工作和使用說明](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  