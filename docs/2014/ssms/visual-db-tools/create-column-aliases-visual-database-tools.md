---
title: 建立資料行別名 (Visual Database Tools) | Microsoft Docs
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
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1c317fd581c97d8c48a5ccd92a0010c45be24493
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36032688"
---
# <a name="create-column-aliases-visual-database-tools"></a>建立資料行別名 (Visual Database Tools)
  您可以建立資料行名稱的別名，來更輕鬆地使用資料行名稱、計算和彙總值。 例如，您可以建立資料行別名來：  
  
-   針對諸如 `(quantity * unit_price)` 的運算式或彙總函式，建立一個如 Total Amount (總數量) 的資料行名稱。  
  
-   建立資料行名稱的縮短形式，例如， `"d_id"` 代表 `"discounts.stor_id."`  
  
 在定義資料行別名後，您可以在選取查詢中使用別名，來指定查詢的輸出項目。  
  
### <a name="to-create-a-column-alias"></a>若要建立資料行別名  
  
1.  在 [準則窗格] 中，找出包含您想要建立別名之資料行的資料列，並且視輸出需要標示該資料列。 如果資料行不在方格中，將其加入。  
  
2.  在該資料列的 [別名] 資料行中，輸入別名。 別名必須遵循所有 SQL 的命名慣例。 如果所輸入的別名包含空白字元，[查詢和檢視設計師] 會自動在別名前後加入分隔符號。  
  
## <a name="see-also"></a>另請參閱  
 [將資料行加入至查詢&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [排序及群組查詢結果&#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [摘要查詢結果&#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [使用查詢執行基本作業 &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  