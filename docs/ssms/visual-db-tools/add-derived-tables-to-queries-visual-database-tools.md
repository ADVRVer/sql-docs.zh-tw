---
description: 將衍生資料表加入查詢 (Visual Database Tools)
title: 將衍生資料表新增到查詢
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: ec4389810e09af78f61e99762dbb30862919f1d1
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037181"
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a>將衍生資料表加入查詢 (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
衍生資料表是用作查詢中資料表來源的結果集。 您可以加入衍生資料表至 [圖表窗格]**** 中的查詢。  
  
### <a name="to-add-a-derived-table-to-a-query"></a>將衍生資料表加入查詢  
  
1.  開啟現有查詢或建立新查詢。  
  
2.  以滑鼠右鍵按一下 [圖表窗格]****，然後選擇 [新增衍生資料表]****。  
  
    隨即加入名稱為 derivedtbl_*N* 的新資料表，衍生資料表的 SELECT 陳述式也加入查詢的 FROM 子句中。  
  
## <a name="see-also"></a>另請參閱  
[使用查詢執行基本作業 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[建立查詢 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-queries-visual-database-tools.md)  
[開啟查詢 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/open-queries-visual-database-tools.md)  
[SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
