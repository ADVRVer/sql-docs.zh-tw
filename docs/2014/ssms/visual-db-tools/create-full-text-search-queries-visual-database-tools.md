---
title: 建立全文檢索搜尋查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 626c1c58cae7db7d07dae717b980c83292e11b7f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175127"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>建立全文檢索搜尋查詢 (Visual Database Tools)
  全文檢索搜尋會使用 CONTAINS 述詞 (Predicate)，找出在指定資料行中具有指定文字的資料列。 全文檢索搜尋只適用於具有現用全文檢索索引的資料行。 如果您嘗試在未具有目前現用全文檢索索引的資料行上使用 CONTAINS 子句，您會收到錯誤訊息。 如需有關全文檢索索引和 CONTAINS 子句的詳細資訊，請參閱 <<c0> [ 全文檢索搜尋](../../relational-databases/search/full-text-search.md)並[CONTAINS &#40;-&#41;](/sql/t-sql/queries/contains-transact-sql)。</c0>  
  
### <a name="to-create-a-full-text-search-query"></a>建立全文檢索搜尋查詢  
  
1.  在 [方案總管] 中開啟查詢或建立新查詢。  
  
2.  在查詢的 WHERE 子句中，使用 CONTAINS 函數來搜尋全文檢索資料行。  
  
## <a name="see-also"></a>另請參閱  
 [支援的查詢類型&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [設計查詢和檢視表的使用說明主題&#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [使用查詢執行基本作業 &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
