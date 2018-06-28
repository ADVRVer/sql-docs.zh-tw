---
title: 測試篩選過的模型 （基本資料採礦教學課程） |Microsoft 文件
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0dfb4b3ae34b230c591071f02cdaa9b0984cf05e
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312546"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a>測試篩選過的模型 (基本資料採礦教學課程)
  既然您判斷出`TM_Decision_Tree`最精確的模型，您將自訂的模型，使其更符合的需求[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]目標郵寄促銷活動。 具體而言，行銷部門想要知道男性和女性客戶之間是否有任何差異。 資訊可協助他們決定哪些雜誌來登廣告使用和哪些產品當做郵寄活動的特色產品。  
  
## <a name="using-filters"></a>使用篩選  
 篩選可讓您輕鬆地根據資料子集來建立模型。 篩選只會套用到模型中，而且不會變更基礎資料來源。  
  
 在這一課，您將建立一個依性別篩選的模型，以便預測對於男性和女性購買行為最有影響力的特性。  
  
 第一次您將建立一份`TM_Decision_Tree`模型。  
  
#### <a name="to-copy-the-decision-tree-model"></a>若要複製決策樹模型  
  
1.  在[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]，在方案總管中，選取**BasicDataMining**。  
  
2.  按一下 **[採礦模型]** 索引標籤。  
  
3.  以滑鼠右鍵按一下`TM_Decision_Tree`模型，然後選取**新增採礦模型。**  
  
4.  在**模型名稱**欄位中，輸入`TM_Decision_Tree_Male`。  
  
5.  按一下 [確定] 。  
  
 接下來，建立一個篩選來選取此模型的客戶 (根據客戶的性別)。  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a>若要建立採礦模型的案例篩選  
  
1.  以滑鼠右鍵按一下`TM_Decision_Tree_Male`採礦模型，即可開啟快顯功能表。  
  
     -或-  
  
     選取此模型。 在 **[採礦模型]** 功能表上，選取 **[設定模型篩選器]**。  
  
2.  在 [模型篩選器] 對話方塊的 [採礦結構資料行] 文字方塊中，按一下方格中的上方資料列。  
  
     下拉式清單只會顯示該資料表中的資料行名稱。  
  
3.  在採礦結構資料行的文字方塊中，選取**性別**。  
  
     文字方塊左側的圖示會變更，指出選取的項目是資料表或資料行。  
  
4.  按一下**運算子**文字方塊並選取等於 （=） 運算子，從清單中。  
  
5.  按一下**值**文字方塊，然後輸入**M**。  
  
6.  在方格中，按下一個資料列。  
  
7.  按一下**確定**關閉**模型篩選器** 對話方塊。  
  
     篩選器會顯示在**屬性**視窗。 或者，您可以啟動**模型篩選器**對話方塊從**屬性**視窗。  
  
8.  重複上述步驟，但這次將模型`TM_Decision_Tree_Female`和型別**F**中**值**文字方塊。  
  
## <a name="process-the-filtered-models"></a>處理篩選過的模型  
 模型要等到部署及處理之後，才可以使用。 如需有關處理模型的詳細資訊，請參閱[目標郵寄結構中的 處理模型&#40;基本資料採礦教學課程&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)。  
  
#### <a name="to-process-the-filtered-model"></a>若要處理篩選過的模型  
  
1.  以滑鼠右鍵按一下`TM_Decision_Tree_Male`模型，並選取**處理採礦結構和所有模型**s  
  
2.  按一下**執行**處理新的模型。  
  
3.  已完成處理之後，請按一下**關閉**兩個處理視窗。  
  
     您現在有兩個新的模型顯示在**採礦模型** 索引標籤。  
  
## <a name="evaluate-the-results"></a>評估結果  
 檢視結果，並評估篩選過之模型的正確性，就像之前三個模型的處理方式一樣。 如需詳細資訊，請參閱：  
  
 [瀏覽決策樹模型&#40;基本資料採礦教學課程&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [使用增益圖測試精確度&#40;基本資料採礦教學課程&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a>若要探索篩選過的模型  
  
1.  選取**採礦模型檢視器**索引標籤中**資料採礦設計師**。  
  
2.  在採礦模型 方塊中，選取`TM_Decision_Tree_Male`。  
  
3.  投影片**顯示層級**至`3`。  
  
4.  變更**背景**值設定為`1`。  
  
5.  將游標放在標示為的節點上方**所有**以查看自行車買主與非自行車買主的數目。  
  
6.  重複步驟 1 至 5 `TM_Decision_Tree_Female`。  
  
7.  瀏覽的結果`TM_Decision_Tree`和性別篩選的模型。 與所有自行車買主相較之下，男性和女性自行車買主與未篩選的自行車買主具有一些共同的特性，但是這三種買主也有一些有趣的差異。 這是有用的資訊，[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]可用來開發他們的行銷活動。  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a>若要測試篩選過之模型的增益  
  
1.  切換至**採礦精確度圖表** 索引標籤中的資料採礦設計師中[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]選取**輸入選擇** 索引標籤。  
  
2.  在**選取要用於精確度圖表的資料集**群組方塊中，選取**使用採礦結構測試案例**。  
  
3.  在**輸入選擇**資料採礦設計師索引標籤底下**選取可預測的採礦模型資料行，以增益圖中顯示**，選取核取方塊**同步處理預測資料行和值**。  
  
4.  在**可預測資料行名稱**資料行中，確認**Bike Buyer**選取每個模型。  
  
5.  在**顯示**資料行中，選取每個模型。  
  
6.  在**預測值**欄中，選取`1`。  
  
7.  選取**增益圖**索引標籤，顯示增益圖。  
  
     您現在會注意到有三個決策樹模型與隨機猜測模型相較之下都有了顯著提升，而且也優於群集模型和貝氏機率分類模型。  
  
## <a name="related-tasks"></a>相關工作  
 如需有關篩選的詳細資訊，請參閱[採礦模型的篩選&#40;Analysis Services-Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)。  
  
 如需如何將篩選套用至巢狀資料表的範例，請參閱[中繼資料採礦教學課程&#40;Analysis Services-Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)。  
  
## <a name="previous-task-in-lesson"></a>本課程的前一項工作  
 [使用增益圖測試精確度&#40;基本資料採礦教學課程&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>下一課  
 [第 6 課： 建立及處理預測&#40;基本資料採礦教學課程&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料採礦教學課程&#40;Analysis Services-資料採礦&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [採礦模型的工作與操作方法](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [從採礦模型刪除篩選](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)   
 [採礦模型的篩選&#40;Analysis Services-資料採礦&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  