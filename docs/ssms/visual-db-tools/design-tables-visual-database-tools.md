---
description: 建立及更新資料表
title: 建立及更新資料表
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Visual Database Tools [SQL Server], Table Designer
- Table Designer, designing tables
- opening tables
- opening Table Designer
- tables [SQL Server], opening
- Table Designer, opening
ms.assetid: c49e0155-5dcb-481f-9538-e1bde77105e2
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/25/2017
ms.openlocfilehash: 5a0bbc50ddef7baa1cd2f21211f692703f41b251
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491696"
---
# <a name="create-and-update-database-tables"></a>建立及更新資料表

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

資料表設計工具是視覺效果工具，您可在其中設計[資料庫資料表](../../relational-databases/tables/tables.md)並將其視覺化。 使用 SQL Server Management Studio (SSMS) 資料表設計工具來建立、編輯或刪除資料表、資料行、索引鍵、索引、關聯性及條件約束。  

## <a name="create-a-table"></a>建立資料表

1. 以滑鼠右鍵按一下資料庫中的 [資料表]  節點，然後選取 [新增]   > [資料表]  ：

    ![新增資料表](../media/design-tables/new-table.png)

2. 在資料表新增[資料行](column-properties-visual-database-tools.md)：

    ![設計資料表](../media/design-tables/new-table2.png)

3. 關閉設計工具並儲存變更。

## <a name="update-a-table"></a>更新資料表

1. 以滑鼠右鍵按一下資料庫中，[資料表]  節點下的資料表，然後選取 [設計]  ：

    ![更新資料表](../media/design-tables/update-table.png)

2. 更新想要的資料表設定：

    ![建立資料表](../media/design-tables/update-table2.png)

3. 關閉設計工具並儲存變更。

## <a name="see-also"></a>另請參閱

- [資料表](../../relational-databases/tables/tables.md)
- [資料表屬性 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/table-properties-visual-database-tools.md)
- [資料行屬性](column-properties-visual-database-tools.md)
- [在資料表新增資料行](../../relational-databases/tables/add-columns-to-a-table-database-engine.md)
- [主要與外部索引鍵](../../relational-databases/tables/primary-and-foreign-key-constraints.md)
- [索引數](../../relational-databases/indexes/indexes.md)
- [資料類型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)
- [下載 SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)
- [在 Visual Studio 中建立資料庫及新增資料表](/visualstudio/data-tools/create-a-sql-database-by-using-a-designer)
