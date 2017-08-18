---
title: "查詢和檢視表設計工具 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.querydesigner
- vdt.pane.diagram
- vdt.pane.grid
- vdt.dlgbox.querybuilder
- vdt.pane.sql
- vdt.pane.results
helpviewer_keywords:
- Query Designer [SQL Server], panes
- View Designer, panes
- Query Designer [SQL Server], components
- View Designer, components
ms.assetid: 12e4b5a5-b793-4b6c-a0e5-c450c49bf26f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 45b05e606f083b20fa7b1ba9e8a25b4defcf7c7c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/18/2017

---
# <a name="query-and-view-designer-tools-visual-database-tools"></a>查詢和檢視設計工具 (Visual Database Tools)
設計查詢、檢視、內嵌函數或單一陳述式預存程序時，您所使用的設計工具將由四個窗格組成：[圖表] 窗格、[準則] 窗格、[SQL] 窗格和 [結果] 窗格。  
  
![查詢設計工具](../../ssms/visual-db-tools/media/vs_queryviewdsgpanes.gif "查詢設計工具")  
  
-   [圖表] 窗格將顯示您進行查詢的資料表和其他資料表值物件。 每一個矩形代表一個資料表或資料表值物件，並顯示可用的資料行。 矩形間的行即代表聯結 (Join)。 如需詳細資訊，請參閱[圖表窗格 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)。  
  
-   [準則] 窗格含有類似工作表的方格，您可以在該窗格中指定選項，如要顯示的資料行、要選取的資料列、如何將資料列群組化等等。 如需詳細資訊，請參閱[準則窗格 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)。  
  
-   [SQL] 窗格顯示查詢或檢視的 SQL 陳述式。 您可以編輯設計工具建立的 SQL 陳述式，或輸入您自己的 SQL 陳述式。 當您要輸入無法使用 [圖表] 和 [準則] 窗格建立的 SQL 陳述式時 (如聯結查詢)，這項功能便很有用。 如需詳細資訊，請參閱 [SQL 窗格 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)。  
  
-   [結果] 窗格顯示查詢或檢視擷取的資料格。 在 [查詢和檢視設計師] 中，該窗格顯示的是最近執行 SELECT 查詢的結果。 您可以編輯資料格方格中的值以及加入或刪除資料列來修改資料庫。 如需詳細資訊，請參閱[結果窗格 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/results-pane-visual-database-tools.md)。  
  
您可以在其中任何一個窗格中建立查詢或檢視：您可以在 [圖表] 窗格中選擇要指定顯示的資料行、將資料行輸入 [準則] 窗格，或使之成為 [SQL] 窗格中 SQL 陳述式的一部份。  
  
## <a name="displaying-and-hiding-panes"></a>顯示及隱藏窗格  
若要隱藏窗格或顯示看不見的窗格，請以滑鼠右鍵按一下設計介面，指向 [窗格]，然後按一下窗格名稱。 如果在查詢設計工具模式中開啟 查詢和檢視表設計工具，則無法使用 結果 窗格。  
  
## <a name="see-also"></a>另請參閱  
[設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[開啟查詢和檢視表設計工具 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/open-the-query-and-view-designer-visual-database-tools.md)  
[SQL 編輯器 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sql-editor-visual-database-tools.md)  
  

