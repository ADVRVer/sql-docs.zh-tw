---
title: 刪除檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7e727451fb0f9dc7a3d0726a2cb0fa2d6adf997
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68196412"
---
# <a name="delete-views"></a>刪除檢視
  您可以在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中刪除 (卸除) 檢視，方法是使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  

  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   當您卸除檢視時，也會從系統目錄中刪除檢視的定義和檢視的其他相關資訊。 檢視的所有權限也都會刪除。  
  
-   在利用 `DROP TABLE` 來卸除的資料表中，您必須利用 `DROP VIEW`來明確卸除任何檢視。  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> 權限  
 需要 SCHEMA 的 ALTER 權限或 OBJECT 的 CONTROL 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-delete-a-view-from-a-database"></a>若要從資料庫刪除檢視  
  
1.  在 **[物件總管]** 中，展開資料庫，此資料庫包含您要刪除的檢視，然後展開 **[檢視]** 資料夾。  
  
2.  以滑鼠右鍵按一下您要刪除的檢視，然後按一下 [刪除]  。  
  
3.  在 **[刪除物件]** 對話方塊中，按一下 **[確定]** 。  
  
    > [!IMPORTANT]  
    >  按一下 [**刪除物件**] 對話方塊中的 [**顯示**相依性]，開啟 [ _view_name_相依**性] 對話方塊**。 這就會顯示相依於檢視的所有物件以及檢視所相依的所有物件。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-delete-a-view-from-a-database"></a>若要從資料庫刪除檢視  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]** 。  
  
3.  複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。 此範例只在指定的檢視已存在時才會予以刪除。  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 如需詳細資訊，請參閱 [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql)。  
  
  
