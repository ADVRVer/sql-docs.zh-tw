---
title: 收益圖 (Analysis Services-資料採礦) |Microsoft 文件
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- accuracy, charting
- revenue, estimating
- benefits, estimating
- charts [Analysis Services]
- profit charts [Analysis Services]
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 852352be5b6648e4877a4d44ff4a9cbc1566e2fb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="profit-chart-analysis-services---data-mining"></a>收益圖 (Analysis Services - 資料採礦)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  收益圖會顯示與使用採礦模型有關聯的預估獲利率。 例如，假設您的模型是預測公司應該在某個商務案例中連絡哪些客戶。 在此情況下，您的收益圖就要加入與執行目標郵寄促銷活動的成本有關的資訊。 然後，您便能在完成的圖表中看到正確鎖定目標客戶相較於隨機連絡客戶的預估收益。  
  
## <a name="build-a-profit-chart"></a>建置收益圖  
 收益圖類似於增益圖。 您首先要建立增益圖，然後再加入成本和收益資訊。  
  
 若要建置收益圖，您必須已有現存的模型。  
  
 本範例使用的是目標郵寄決策樹模型。 此模型識別了可能購買自行車的客戶。 您可以套用 [收益圖] 來判斷能夠達到最高收益的目標客戶數。  
  
 若您並沒有範例模型，則可使用[資料採礦基本教學課程](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)予以建立。  
  
1.  開啟採礦精確度圖表產生器。  
  
    -   在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 [檢視增益圖]。  
  
    -   在 SQL Server Data Tools 中，開啟您已在其中建立模型的專案，然後按一下 [採礦精確度圖表] 索引標籤。  
  
2.  在 [輸入選擇] 索引標籤上，選取模型並選擇可預測的屬性值。  
  
     就這個特定案例而言，您只有興趣知道能準確預測此值的獲利率：[Bike Buyer] =1。  
  
     不過，您也一樣重視能準確預測 false 值的其他案例。 例如，醫療診斷檢驗誤判的成本可能很高，以致必須將這項因素計入獲利率預測，而誤否定的成本也是如此。 在這類情況下，您就要測量所有結果。  
  
3.  選取要測試的資料集。 針對本範例，請選取測試資料集。  
  
4.  接著，按一下 [增益圖] 索引標籤。  
  
     隨即會自動產生增益圖。  
  
5.  從 [圖表類型] 清單中選取 [收益圖]，以將其變更為收益圖。  
  
6.  只要您選擇了收益圖作為圖表類型，即會自動開啟 [收益圖設定] 對話方塊。  
  
     此對話方塊可協助您指定與目標郵寄促銷活動相關的成本與效益。 針對這些範例中所示的圖表，我們使用下列值：  
  
    |設定|Value|註解|  
    |-------------|-----------|--------------|  
    |**母體**|20,000|設定總目標母體的值<br /><br /> 您的資料庫可能包含許多客戶，但是為了省下郵寄支出，您可以選擇只鎖定最有可能回應的 20,000 名目標客戶。 藉由執行預測查詢，並依預測模型所輸出的機率排序，即可取得這份清單。|  
    |**固定成本**|500|輸入為 20,000 人設定目標郵寄促銷活動的單次成本。 這可能包括印刷品，或是設定電子郵件促銷活動的成本。|  
    |**單位成本**|3|輸入目標郵寄促銷活動的每單位成本。<br /><br /> 這個金額將會乘以小於或等於 20000 的數字，端視模型預測多少客戶為良好潛在客戶而定。|  
    |**每個別營收**|400|輸入代表預期可從成功的結果獲得的收益或收入金額值。 本案例假設每郵寄一份型錄而促成購買配件或自行車的平均金額為 $400 美元。<br /><br /> 此金額將會用來預估與高機率案例有關的總收益。|  
  
7.  在您設定妥必要的參數之後，按一下 [確定]。  
  
8.  圖表隨即更新，以顯示收益曲線。  
  
## <a name="understanding-the-profit-chart"></a>了解收益圖  
 下圖顯示以這些參數為基礎的圖表。 圖表的 Y 軸代表收益，而 X 軸則代表目標郵寄促銷活動所連絡的客戶百分比。  
  
 如下所示，使用收益圖能讓您比較多個模型，只要這些模型都預測相同的離散屬性即可。  
  
 ![收益圖表比較三個模型](../../analysis-services/data-mining/media/dm14-profitchartupdated.gif "收益圖表比較三個模型")  
  
 請注意圖表中的灰色垂直線。 當您按一下並拖曳這條線時，工具提示便會顯示曲線底下於各點位置所包括的目標母體的百分比。  
  
 隨著您拖曳這條線，[採礦圖例] 也將更新以顯示百分比值、收益分數以及此灰色垂直線上與母體百分比有關的預測機率。  
  
 例如，若您使用此模型決定要將促銷文宣寄給哪些人，您可能就會根據預測機率而決定以母體的 25% 為目標。不過，圖表的收益曲線底下介於 40% 到 70% 之間的面積最大，表示就算整體百分比回應偏低，郵寄的人數愈多還是能夠獲得愈高的報酬。  
  
## <a name="saving-charts"></a>儲存圖表  
 當您建立精確度圖表或收益圖時，在伺服器上並不會建立任何物件。 但是，此時會對現有的模型執行查詢，再由檢視器轉譯結果。 如果您需要儲存結果，則必須將圖表或結果複製到 Excel 或其他檔案。  
  
## <a name="related-content"></a>相關內容  
 下列主題包含您可以如何建立及使用精確度圖表的詳細資訊。  
  
|主題|連結|  
|------------|-----------|  
|提供如何為此目標郵寄模型建立增益圖的逐步解說。|[基本資料採礦教學課程](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)<br /><br /> [使用增益圖 &#40;測試精確度基本資料採礦教學課程&#41;](http://msdn.microsoft.com/library/822d414b-4a39-473f-80c3-53476e30655a)|  
|說明相關的圖表類型。|[增益圖 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)<br /><br /> [分類矩陣 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)<br /><br /> [散佈圖 & #40;Analysis Services-資料採礦 & #41;](../../analysis-services/data-mining/scatter-plot-analysis-services-data-mining.md)|  
|描述採礦模型和採礦結構的交叉驗證。|[交叉驗證 &#40;Analysis Services - 資料採礦&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)|  
|描述建立增益圖及其他精確度圖表的步驟。|[測試和驗證工作及操作方式 &#40;資料採礦&#41;](../../analysis-services/data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a>另請參閱  
 [測試及驗證 & #40; 資料採礦 & #41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [使用增益圖 &#40;測試精確度基本資料採礦教學課程&#41;](http://msdn.microsoft.com/library/822d414b-4a39-473f-80c3-53476e30655a)  
  
  
