---
title: "從範本建立單一預測查詢 |Microsoft 文件"
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
helpviewer_keywords: singleton query predictions [DMX]
ms.assetid: e0a68ab0-bece-4d25-b464-47f1719302e6
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7b455a9f4c8996ec2dd9e6d255f4e9f282d58df4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="create-a-singleton-prediction-query-from-a-template"></a>根據範本建立單一預測查詢
  如果您具有一個要用於預測的模型，但不希望將該模型對應至外部輸入資料集或產生大量預測，則單一查詢很有用。 使用單一查詢，您可以向模型提供一個或多個值，並且立即會看到預測值。  
  
 例如，下列 DMX 查詢表示針對目標郵寄模型 TM_Decision_Tree 的單一查詢。  
  
```  
SELECT * FROM [TM_Decision_tree] ;  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 下列程序描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的範本總管來快速建立此查詢。  
  
### <a name="to-open-the-analysis-services-templates-in-sql-server-management-studio"></a>在 SQL Server Management Studio 中開啟 Analysis Services 範本  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 [檢視]  功能表上，按一下 [範本總管] 。  
  
2.  按一下 Cube 圖示，即可開啟 [Analysis Server] 範本。  
  
### <a name="to-open-a-prediction-query-template"></a>開啟預測查詢範本  
  
1.  在**範本總管**中，於 Analysis Server 範本的清單內，展開 [DMX]，然後展開 [預測查詢]。  
  
2.  按兩下 [單一預測]。  
  
3.  在 [連接到 Analysis Services] 對話方塊中，輸入具有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體 (包含即將進行查詢的採礦模型) 的伺服器名稱。  
  
4.  按一下 **[連接]**。  
  
5.  此範本會在指定的資料庫中開啟，並提供採礦模型物件瀏覽器，其中包含資料採礦函數和資料採礦結構與相關模型的清單。  
  
### <a name="to-customize-the-singleton-query-template"></a>自訂單一查詢範本  
  
1.  在此範本中，按一下 [可用的資料庫] 下拉式清單，然後從清單中選取 Analysis Service 的執行個體。  
  
2.  在 [採礦模型] 清單中，選取您想要查詢的採礦模型。  
  
     採礦模型中的資料行清單會顯示在物件瀏覽器的 [中繼資料] 窗格中。  
  
3.  在 [查詢] 功能表上，選取 [指定範本參數的值]。  
  
4.  在 [選取清單] 資料列中，輸入 * 以便傳回所有資料行，或輸入資料行和運算式的逗號分隔清單以便傳回特定的資料行。  
  
     如果您輸入 *，就會傳回可預測資料行，以及您在步驟 6 中提供新值的任何資料行。  
  
     若為本主題開頭所顯示的範例程式碼，[選取清單] 資料列設定為 *。  
  
5.  在 [採礦模型] 資料列中，根據**物件總管**中顯示的採礦模型清單，輸入採礦模型的名稱。  
  
     若為本主題開頭所顯示的範例程式碼，[採礦模型] 資料列設定為 **TM_Decision_Tree** 名稱。  
  
6.  在 [值] 資料列中，針對您想要進行預測的項目輸入新資料值。  
  
     若為本主題開頭所顯示的範例程式碼，[值] 資料列設定為 **2**，以便根據家中子女人數來預測自行車購買行為。  
  
7.  在 [資料行] 資料列中，輸入新資料應該對應至採礦模型中的目標資料行名稱。  
  
     若為本主題開頭所顯示的範例程式碼，[資料行] 資料列設定為 **Number Children at Home**。  
  
    > [!NOTE]  
    >  當您使用 [指定範本參數的值] 對話方塊時，不需要在資料行名稱前後加上方括號。 系統會自動為您加入括號。  
  
8.  保留 [輸入別名] 為 **t**。  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. 在查詢文字窗格中，尋找逗號和省略符號底下的紅色不規則曲線，表示語法錯誤。 請刪除省略符號，然後加入所需的任何其他查詢條件。 如果您沒有加入任何其他條件，請刪除逗號。  
  
     若為本主題開頭所顯示的範例程式碼，其他查詢條件設定為 **'45' as [Age]**。  
  
11. 按一下 **[執行]**。  
  
## <a name="see-also"></a>請參閱＜  
 [建立預測 &#40;資料採礦基本教學課程&#41;](http://msdn.microsoft.com/library/a8410ed2-bb98-4d51-a9eb-b239be1201c2)  
  
  
