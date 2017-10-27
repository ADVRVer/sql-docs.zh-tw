---
title: "修改檢視 |Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-views
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- views [SQL Server], renaming
- views [SQL Server], modifying
- modifying views
- renaming views
ms.assetid: 2d3c14dc-43e5-4324-b8fb-f2692d330b16
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 242d7b946699560cf24c59a262e3a14a5c08b8d9
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="modify-views"></a>修改檢視
  定義檢視之後，可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改其定義，不需要卸除和重新建立檢視。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [安全性](#Security)  
  
-   **使用下列方法修改檢視：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   修改檢視不會影響任何相依物件，像是預存程序或觸發程序，除非檢視的定義變更導致相依物件不再有效。  
  
-   如果目前所用的檢視是利用 ALTER VIEW 來修改的， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會取得檢視的獨佔結構描述鎖定。 當授與鎖定時，檢視並沒有使用中的使用者， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會從程序快取中刪除檢視的所有副本。 現有參考這份檢視的計畫會保留在快取中，但在叫用它時，會重新編譯。  
  
-   您可以將 ALTER VIEW 套用在索引檢視上；不過，ALTER VIEW 會無條件地卸除檢視的所有索引。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 若要執行 ALTER VIEW，至少需要 OBJECT 的 ALTER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-modify-a-view"></a>若要修改檢視  
  
1.  在 **[物件總管]**中，按一下檢視表所在之資料庫旁邊的加號，然後按一下 **[檢視表]** 資料夾旁邊的加號。  
  
2.  以滑鼠右鍵按一下您要修改的檢視，然後選取 [設計]。  
  
3.  在查詢設計工具的圖表窗格中，以下列一個或多個方式變更檢視：  
  
    1.  對於您要加入或移除的任何元素，選取或清除核取方塊。  
  
    2.  以滑鼠右鍵按一下圖表窗格，並選取 [加入資料表]，然後從 [加入資料表] 對話方塊選取要加入檢視中的其他資料行。  
  
    3.  以滑鼠右鍵按一下您要移除之資料表的標題列，然後選取 [移除]。  
  
4.  在 [檔案]  功能表上，按一下 [儲存] *view name*。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-modify-a-view"></a>若要修改檢視  
  
1.  在 **[物件總管]**中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 此範例先建立檢視，然後透過使用 ALTER VIEW 修改此檢視。 檢視定義中會加入 WHERE 子句。  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    -- Create a view.  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
  
    -- Modify the view by adding a WHERE clause to limit the rows returned.  
    ALTER VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID  
    WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;   
    GO  
    ```  
  
 如需詳細資訊，請參閱 [ALTER VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/alter-view-transact-sql.md)。  
  
  

