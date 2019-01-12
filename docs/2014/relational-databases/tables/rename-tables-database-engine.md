---
title: 重新命名資料表 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3fc62dc5f0e716273df257aba7fdc137391d3055
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124588"
---
# <a name="rename-tables-database-engine"></a>重新命名資料表 (Database Engine)
  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新命名資料表。  
  
> [!CAUTION]  
>  在重新命名資料表之前請仔細考慮。 如果現有的查詢、檢視表、使用者定義函數、預存程序或程式參考此資料表，則名稱修改將會使這些物件失效。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **若要使用下列項目來重新命名資料表：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
 重新命名資料表不會自動重新命名該資料表的參考。 您必須手動修改任何參考重新命名之資料表的物件。 例如，如果您重新命名了資料表，而且觸發程序參考該資料表，您就必須修改觸發程序來反映新的資料表名稱。 在重新命名資料表之前，請使用 [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) 列出其相依性。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 需要資料表的 ALTER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-rename-a-table"></a>重新命名資料表  
  
1.  在物件總管中，以滑鼠右鍵按一下想要重新命名的資料表，然後從快速鍵功能表選擇 [設計]。  
  
2.  從 **[檢視]** 功能表中選擇 **[屬性]**。  
  
3.  在 **[屬性]** 視窗中的 **[名稱]** 值欄位中，輸入資料表的新名稱。  
  
4.  若要取消這個動作，請在離開這個欄位之前按 ESC 鍵。  
  
5.  從 [檔案] 功能表中，選擇 [儲存 _table name_]。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-rename-a-table"></a>重新命名資料表  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]**。  
  
3.  下列範例會將 `SalesTerritory` 資料表重新命名為 `SalesTerr` 結構描述中的 `Sales` 。 將下列範例複製並貼入查詢視窗中，然後按一下 [執行] 。  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 如需其他範例，請參閱 [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。  
  
  
