---
title: "使用從模型檢視器鑽研 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5e065ad-c688-4c2c-8c82-7f3038e04915
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ed4254b34f570f37761001542d67e94c02e70a84
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="use-drillthrough-from-the-model-viewers"></a>從模型檢視器使用鑽研
  根據模型類型，您可以從資料採礦設計師的 [採礦模型檢視器] 索引標籤上的瀏覽檢視器中使用鑽研，以瀏覽採礦模型中使用的案例或查看採礦結構中的其他資料行。 雖然因為模型中的模式無法直接連結到特定案例，導致許多模型類型不支援鑽研，但下列模型類型支援鑽研。  
  
 請注意，模型上必須已啟用鑽研，而且您必須擁有適當的權限。 無論模型是否以前已處理並具有內容，如果模型處於未處理狀態，鑽研選項也可能會停用。 若要透過使用鑽研擷取模型案例資料，結構和模型的快取必須是最新狀態。  
  
### <a name="use-drillthrough-in-the-microsoft-tree-viewer"></a>在 Microsoft 樹狀檢視器中使用鑽研  
  
1.  在資料採礦設計師中，選取決策樹模型，然後選取 [瀏覽模型]，在 [Microsoft 樹狀檢視器] 中開啟模型。 在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 [瀏覽]  
  
2.  以滑鼠右鍵按一下樹狀圖表中的任何節點，然後選取 [鑽研]。  
  
3.  選取下列其中一個選項：[僅模型資料行] 或 [模型和結構資料行]。 如果您沒有權限，選項可能無法使用。  
  
4.  [鑽研] 對話方塊隨即開啟，並顯示案例資料和/或結構資料。 對話方塊的標題列也包含說明，識別執行鑽研查詢的節點。  
  
5.  以滑鼠右鍵按一下結果中的任何位置，然後選取 [全部複製]，將結果儲存至剪貼簿。  
  
### <a name="use-drillthrough-in-the-microsoft-cluster-viewer"></a>在 Microsoft 叢集檢視器中使用鑽研  
  
1.  在資料採礦設計師中，選取叢集模型，然後選取 [瀏覽模型]，在 [Microsoft 叢集檢視器] 中開啟模型。 在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 [瀏覽]。  
  
2.  在 [叢集] 索引標籤上，以滑鼠右鍵按一下任何節點。  
  
3.  選取 [鑽研]，然後選取下列其中一個選項：[僅模型資料行] 或 [模型和結構資料行]。 如果您沒有權限，選項可能無法使用。  
  
4.  [鑽研] 對話方塊隨即開啟，並顯示案例資料和/或結構資料。 對話方塊的標題列也包含識別案例叢集的說明。  
  
5.  以滑鼠右鍵按一下結果中的任何位置，然後選取 [全部複製]，將結果儲存至剪貼簿。  
  
### <a name="use-drillthrough-in-the-microsoft-association-rules-viewer"></a>在 Microsoft 關聯規則檢視器中使用鑽研  
  
1.  在資料採礦設計師中，選取關聯模型，然後選取 [瀏覽模型]，在 [Microsoft 關聯規則檢視器] 中開啟模型。 在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 [瀏覽]  
  
2.  在 [規則] 索引標籤上，以滑鼠右鍵按一下表示規則的任何資料列。 在 [項目集] 索引標籤上，按一下包含項目集的任何資料列。  
  
3.  選取 [鑽研]，然後選取下列其中一個選項：[僅模型資料行] 或 [模型和結構資料行]。 如果您沒有權限，選項可能無法使用。  
  
4.  [鑽研] 對話方塊隨即開啟，並顯示案例資料和/或結構資料。 對話方塊的標題列也包含識別規則名稱的說明。  
  
5.  以滑鼠右鍵按一下結果中的任何位置，然後選取 [全部複製]，將完整案例結果儲存至剪貼簿。 您也可以選取 [複製]，只複製選取的案例。 如果模型包含巢狀資料表資料行，只會貼上巢狀資料表資料行的名稱；若要擷取每個案例的巢狀資料表資料行內的資料值，您必須對模型內容建立查詢。  
  
### <a name="use-drillthrough-in-the-microsoft-sequence-cluster-viewer"></a>在 Microsoft 時序叢集檢視器中使用鑽研  
  
1.  在資料採礦設計師中，選取叢集模型，然後選取 [瀏覽模型]，在 [Microsoft 叢集檢視器] 中開啟模型。 在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 [瀏覽]。  
  
2.  在 [叢集圖表] 索引標籤上，以滑鼠右鍵按一下表示叢集的任何節點。 從 [叢集設定檔] 索引標籤，按一下叢集設定檔中或表示模型總母體之叢集中的任何位置。  
  
3.  選取 [鑽研]，然後選取下列其中一個選項：[僅模型資料行] 或 [模型和結構資料行]。 如果您沒有權限，選項可能無法使用。  
  
4.  [鑽研] 對話方塊隨即開啟，並顯示案例資料和/或結構資料。 對話方塊的標題列也包含識別案例叢集的說明。  
  
5.  以滑鼠右鍵按一下結果中的任何位置，然後選取 [全部複製]，將結果儲存至剪貼簿。 如果模型包含巢狀資料表資料行，只會貼上巢狀資料表資料行的名稱；若要擷取每個案例的巢狀資料表資料行內的資料值，您必須對模型內容建立查詢。  
  
## <a name="see-also"></a>請參閱＜  
 [採礦模型檢視器工作和使用說明](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [採礦模型的鑽研](../../analysis-services/data-mining/drillthrough-on-mining-models.md)   
 [採礦結構的鑽研](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  

