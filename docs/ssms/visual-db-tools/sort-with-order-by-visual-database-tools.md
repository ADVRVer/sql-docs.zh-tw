---
title: "使用 ORDER BY 排序 (Visual Database Tools) | Microsoft Docs"
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
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 01bb085d1946c5e6ac407c6baa8a9049892bc4df
ms.lasthandoff: 04/11/2017

---
# <a name="sort-with-order-by-visual-database-tools"></a>使用 ORDER BY 排序 (Visual Database Tools)
您可以使用 ORDER BY 子句，藉此根據傳回資料列中的一或多個資料行，排序查詢結果。 您可以在 [準則細節] 窗格中選擇選項，定義 ORDER BY 子句。  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>若要使用 ORDER BY 子句排序查詢  
  
1.  開啟查詢或建立新查詢。  
  
2.  在[準則窗格](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)中，針對對應到您要用來排序查詢結果之資料行的資料列，按一下 [排序類型]****。  
  
3.  從下拉式清單選擇 [遞增]** 或 [遞減]**。  
  
> [!NOTE]  
> 清除資料行的 [排序類型]**** 項目時，會從 ORDER BY 子句移除該資料行。  
  
請注意，使用 [準則] 窗格時，查詢的 UNION 子句會變更，以符合您最近的動作。  
  
> [!NOTE]  
> 使用多個資料行排序結果時，可使用 [排序次序]**** 欄位指定資料行相互之間搜尋的順序。 如需詳細資訊，請參閱**如何：對查詢中的多個資料行進行排序**。  
  
## <a name="see-also"></a>另請參閱  
[排序及分組查詢結果 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[摘要查詢結果 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[設計查詢和檢視使用說明主題 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  

