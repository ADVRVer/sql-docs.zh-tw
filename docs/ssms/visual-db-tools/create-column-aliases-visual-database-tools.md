---
title: 建立資料行別名
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: ecf5cbcac382bc088c5a04595d554e4d8ea124ba
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "75254365"
---
# <a name="create-column-aliases-visual-database-tools"></a>建立資料行別名 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
您可以建立資料行名稱的別名，來更輕鬆地使用資料行名稱、計算和彙總值。 例如，您可以建立資料行別名來：  
  
-   針對諸如 `(quantity * unit_price)` 的運算式或彙總函式，建立一個如 Total Amount (總數量) 的資料行名稱。  
  
-   建立資料行名稱的縮短形式，例如， `"d_id"` 代表 `"discounts.stor_id."`  
  
在定義資料行別名後，您可以在選取查詢中使用別名，來指定查詢的輸出項目。  
  
### <a name="to-create-a-column-alias"></a>若要建立資料行別名  
  
1.  在 [準則窗格]  中，找出包含您想要建立別名之資料行的資料列，並且視輸出需要標示該資料列。 如果資料行不在方格中，將其加入。  
  
2.  在該資料列的 [別名]  資料行中，輸入別名。 別名必須遵循所有 SQL 的命名慣例。 如果所輸入的別名包含空白字元，[查詢和檢視設計師] 會自動在別名前後加入分隔符號。  
  
## <a name="see-also"></a>另請參閱  
[將資料行新增至查詢 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)  
[排序及分組查詢結果 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[摘要查詢結果 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[使用查詢執行基本作業 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
