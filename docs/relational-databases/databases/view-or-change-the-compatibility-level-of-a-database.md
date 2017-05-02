---
title: "檢視或變更資料庫的相容性層級 | Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility levels [SQL Server], viewing
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], changing
ms.assetid: 579867ec-57cb-4cb8-af35-9688c1e9e15d
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fa6785003c2e66f446cdc3a41960c5e3d18fad69
ms.lasthandoff: 04/11/2017

---
# <a name="view-or-change-the-compatibility-level-of-a-database"></a>檢視或變更資料庫的相容性層級
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視或變更資料庫的相容性層級。 在變更資料庫的相容性層級之前，您應該先了解此變更對應用程式的影響。 如需詳細資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [安全性](#Security)  
  
-   **使用下列方法檢視或變更資料庫的相容性層級：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要資料庫的 ALTER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-compatibility-level-of-a-database"></a>檢視或變更資料庫的相容性層級  
  
1.  連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，請在 [物件總管] 中按一下伺服器名稱。  
  
2.  展開 **[資料庫]**，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。  
  
3.  以滑鼠右鍵按一下此資料庫，然後按一下 [屬性]****。  
  
     **[資料庫屬性]** 對話方塊隨即開啟。  
  
4.  在 **[選取頁面]** 窗格中，按一下 **[選項]**。  
  
     目前的相容性層級會顯示在 **[相容性層級]** 清單方塊中。  
  
5.  若要變更相容性層級，請從清單中選取其他選項。 這些選項包括 [SQL Server 2008 (100)]****、[SQL Server 2012 (110)]**** 或 [SQL Server 2014 (120)]****。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-view-the-compatibility-level-of-a-database"></a>檢視資料庫的相容性層級  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 這個範例會傳回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的相容性層級。  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-compatibility-level-of-a-database"></a>變更資料庫的相容性層級  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 這個範例會將 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的相容性層級變更為 `120,` ，亦即 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]的相容性層級。  
  
```tsql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
  
