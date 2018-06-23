---
title: 建立 UNION 查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fbfe0de4422aba4a73a5cabf16c42566c272a7d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36131848"
---
# <a name="create-union-queries-visual-database-tools"></a>建立 UNION 查詢 (Visual Database Tools)
  UNION 關鍵字讓您可以在所產生的單一資料表中，包含 2 個 SELECT 陳述式的結果。 由任一 SELECT 陳述式所傳回的所有資料列，會被結合為 UNION 運算式的結果。 如需範例，請參閱[選取範例&#40;TRANSACT-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql)。  
  
> [!NOTE]  
>  圖表窗格只能顯示單一 SELECT 子句。 因此，當您使用 UNION 查詢時，查詢設計工具會隱藏資料表運算窗格。  
  
### <a name="to-create-a-merged-select-query"></a>建立合併的 SELECT 查詢  
  
1.  開啟查詢或建立新查詢。  
  
2.  在 SQL 窗格中，輸入有效的 UNION 運算式。  
  
     下列範例是有效的 UNION 運算式。  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  在 [查詢設計工具] 功能表中，按一下 [執行 SQL] 來執行查詢。  
  
     查詢設計工具目前已格式化您的 UNION 查詢。  
  
## <a name="see-also"></a>另請參閱  
 [支援的查詢類型&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [設計查詢和檢視表的使用說明主題&#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [執行基本查詢作業&#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)   
 [等位&#40;Transact SQL&#41;](/sql/t-sql/language-elements/set-operators-union-transact-sql)  
  
  
