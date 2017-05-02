---
title: "使用自訂運算式摘要或彙總值 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3d3f44a6e6d80dafc9567ddc146e90b7d258b730
ms.lasthandoff: 04/11/2017

---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a>使用自訂運算式摘要或彙總值 (Visual Database Tools)
除了使用彙總函式彙總資料以外，您也可以建立自訂運算式產生彙總值。 您可以使用自訂運算式取代彙總查詢中任何位置的彙總函式。  
  
例如，在 `titles` 資料表中，您可能想要建立查詢，以同時顯示平均價格與折扣後的平均價格。  
  
不可包含只計算資料表中個別資料列的運算式；運算式必須以彙總值做為基礎，因為在計算運算式時只有彙總值可以使用。  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a>若要指定摘要值的自訂運算式  
  
1.  為您的查詢指定群組。 如需詳細資訊，請參閱[群組查詢結果中的資料列 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/group-rows-in-query-results-visual-database-tools.md)。  
  
2.  移至 [準則] 窗格的空白資料列，然後在 [資料行]**** 資料行輸入運算式。  
  
    [查詢和檢視表設計工具](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md)會自動指派資料行別名給運算式，以便在查詢輸出中建立有用的資料行標題。 如需詳細資訊，請參閱[建立資料行別名 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md)。  
  
3.  在運算式的 [群組依據]**** 資料行中，選取 [Expression]****。  
  
4.  執行查詢。  
  
## <a name="see-also"></a>另請參閱  
[排序及分組查詢結果 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[摘要查詢結果 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
  

