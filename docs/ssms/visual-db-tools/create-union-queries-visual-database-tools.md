---
description: 建立 UNION 查詢 (Visual Database Tools)
title: 建立 UNION 查詢
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: b6d4d7618b3130e2b06d3efb8e9e2a35bc7ca0ee
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038371"
---
# <a name="create-union-queries-visual-database-tools"></a>建立 UNION 查詢 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
UNION 關鍵字讓您可以在所產生的單一資料表中，包含 2 個 SELECT 陳述式的結果。 由任一 SELECT 陳述式所傳回的所有資料列，會被結合為 UNION 運算式的結果。 如需範例，請參閱 [SELECT 範例 (Transact-SQL)](../../t-sql/queries/select-examples-transact-sql.md)。  
  
> [!NOTE]  
> 圖表窗格只能顯示單一 SELECT 子句。 因此，當您使用 UNION 查詢時，查詢設計工具會隱藏資料表運算窗格。  
  
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
  
3.  在 [查詢設計工具]**** 功能表中，按一下 [執行 SQL]**** 來執行查詢。  
  
    查詢設計工具目前已格式化您的 UNION 查詢。  
  
## <a name="see-also"></a>另請參閱  
[支援的查詢類型](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[設計查詢與檢視表操作說明主題](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[執行查詢的基本作業](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](../../t-sql/language-elements/set-operators-union-transact-sql.md)