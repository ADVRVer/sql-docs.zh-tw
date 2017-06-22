---
title: "指定搜尋準則 (Visual Database Tools) | Microsoft Docs"
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
- Query Designer [SQL Server], Criteria pane
- queries [Visual Database Tools]
- criteria for search conditions
- search conditions [SQL Server], search criteria
- View Designer, Criteria pane
- row return limitations [SQL Server]
- Criteria pane
- restricting rows returned
- search criteria [SQL Server]
- Visual Database Tools [SQL Server], queries
- limiting rows returned
ms.assetid: 25fb4e31-6dbf-4cf6-8e47-0dd0998c836c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 944b81ceb8f0fd07284364818b58366099ba19f5
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="specify-search-criteria-visual-database-tools"></a>指定搜尋準則 (Visual Database Tools)
您可以使用搜尋準則來限制查詢所傳回的資料列數目。  
  
如需建立搜尋準則的特殊步驟的詳細資訊，請參閱下表所列的主題。  
  
## <a name="in-this-section"></a>本節內容  
[輸入搜尋值的規則 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
說明如何輸入文字、數字、日期或邏輯值。  
  
[在條件窗格中合併搜尋條件的慣例 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
說明使用 AND 和 OR 運算子的概念。  
  
[指定搜尋條件 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/specify-search-conditions-visual-database-tools.md)  
說明選擇搜尋準則以取得所要資料的基本概念。  
  
[指定單一資料行的多重搜尋條件 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/specify-multiple-search-conditions-for-one-column-visual-database-tools.md)  
說明如何在同一資料行中建立多重搜尋條件。  
  
[指定多重資料行的多重搜尋條件 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
說明如何在查詢搜尋條件中包含數個資料行。  
  
[在查詢中指定 TOP 子句 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/specify-the-top-clause-in-queries-visual-database-tools.md)  
說明如何只傳回特定數目或百分比的資料列。  
  
[在相同查詢中使用 HAVING 和 WHERE 子句 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/use-having-and-where-clauses-in-the-same-query-visual-database-tools.md)  
說明在查詢中同時使用這些子句的方法及原因。  
  
[選取不符合某值的資料列 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/select-rows-that-do-not-match-a-value-visual-database-tools.md)  
說明如何在特定資料行的數值未符合您在查詢陳述式中所提供的數值時，傳回所有的資料列。  
  
[包含或排除資料列 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/include-or-exclude-rows-visual-database-tools.md)  
說明在查詢中所使用之子句和運算子的基本概念。  
  
[排除重複的資料列 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/exclude-duplicate-rows-visual-database-tools.md)  
說明如何利用選取查詢來篩選重複的資料列。  
  
[在 AND 具有優先權時結合條件 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/combine-conditions-when-and-has-precedence-visual-database-tools.md)  
說明使用 AND 運算子來篩選查詢結果的原因及方法。  
  
[在 OR 具有優先權時結合條件 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/combine-conditions-when-or-has-precedence-visual-database-tools.md)  
說明使用 OR 運算子來篩選查詢結果的原因及方法。  
  
[建立子查詢 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/create-subqueries-visual-database-tools.md)  
說明如何建立子查詢或巢狀查詢。  
  
## <a name="related-sections"></a>相關章節  
[執行查詢的基本作業 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
提供最常見查詢工作之主題及步驟的連結。  
  
[查詢類型 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
提供可說明所支援查詢類型之主題的連結。  
  
[排序及分組查詢結果 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
提供排序和分組查詢結果之主題及步驟的連結。  
  
[摘要查詢結果 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
提供彙總包含 NULL 和非數值資料列結果之主題及步驟的連結。  
  
[設計查詢和檢視使用說明主題 &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
提供使用 [查詢和檢視表設計工具] 進行查詢及檢視時可執行工作之主題及章節的連結。  
  

