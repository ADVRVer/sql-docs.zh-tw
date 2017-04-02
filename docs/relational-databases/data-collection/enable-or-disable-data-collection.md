---
title: "啟用或停用資料收集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料收集器 [SQL Server], 停用"
  - "資料收集器 [SQL Server], 啟用"
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# 啟用或停用資料收集
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中啟用或停用資料收集。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [安全性](#Security)  
  
-   **若要使用下列項目啟用或停用資料收集：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要 **dc_admin** 或 **dc_operator** (具有 EXECUTE 權限) 固定資料庫角色中的成員資格，才能執行此程序。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### 若要啟用資料收集器  
  
1.  在 [物件總管] 中，展開 **[管理]** 節點。  
  
2.  以滑鼠右鍵按一下 [資料收集]，然後按一下 [啟用資料收集]。  
  
#### 若要停用資料收集器  
  
1.  在 [物件總管] 中，展開 **[管理]** 節點。  
  
2.  以滑鼠右鍵按一下 [資料收集]，然後按一下 [停用資料收集]。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### 若要啟用資料收集器  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 此範例使用 [sp_syscollector_enable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md) 啟用資料收集器。  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### 若要停用資料收集器  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 此範例使用 [sp_syscollector_disable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql.md) 停用資料收集器。  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## 另請參閱  
 [資料收集](../../relational-databases/data-collection/data-collection.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  