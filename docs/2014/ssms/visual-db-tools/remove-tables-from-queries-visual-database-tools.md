---
title: 移除查詢的資料表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 131a7e5ad9837c795b8a7f3c7360b84f8858177a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36035369"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a>移除查詢的資料表 (Visual Database Tools)
  您可以從查詢移除資料表或任何資料表值物件。  
  
> [!NOTE]  
>  移除資料表或資料表值物件並不會從資料庫刪除任何東西，只是從目前的查詢中移除。 如需有關移除資料庫中資料表的詳細資訊，請參閱[刪除資料表&#40;Database Engine&#41;](../../relational-databases/tables/delete-tables-database-engine.md)。  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>若要移除資料表或表格化物件  
  
-   在 [圖表] 窗格中，選取資料表、檢視、使用者定義函數、同義資料表或查詢，然後按下 DELETE，或是在物件上按一下滑鼠右鍵，然後在出現的對話方塊中選擇 [移除]。 您可以一次選取並移除多個物件。  
  
     -或-  
  
-   在 [SQL] 窗格中移除物件的所有參考。  
  
 當您移除資料表或資料表值物件時，查詢和檢視表設計工具會自動移除涉及資料表或資料表值物件的聯結，並且移除與 [SQL] 窗格及 [條件] 窗格中物件資料行的參考。 但是，如果查詢包含牽涉到物件的複雜運算式，除非此物件的所有參考已經移除，否則物件將不會自動移除。  
  
## <a name="see-also"></a>另請參閱  
 [將資料表加入查詢&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [建立資料表別名&#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md)   
 [指定搜尋準則&#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [摘要查詢結果&#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [使用查詢執行基本作業 &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  