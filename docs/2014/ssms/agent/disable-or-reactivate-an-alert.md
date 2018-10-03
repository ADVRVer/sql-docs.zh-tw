---
title: 停用或重新啟用警示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], reactivating
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- alerts [SQL Server], disabling
- reactivating alerts
- removing alerts
ms.assetid: 4cb37dc6-1134-405d-8590-58b44dcf63b2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2df2f98e092f44b56e2ab16f775248ff0f3bb65
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163218"
---
# <a name="disable-or-reactivate-an-alert"></a>停用或重新啟動警示
  此主題描述如何使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中停用或重新啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [Security](#Security)  
  
-   **若要使用下列項目停用或重新啟動警示：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 依預設， **系統管理員 (sysadmin)** 固定伺服器角色的成員可以編輯警示中的資訊。 其他使用者必須被授與 **msdb** 資料庫的 **SQLAgentOperatorRole** 固定資料庫角色。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-disable-or-reactivate-an-alert"></a>若要停用或重新啟動警示  
  
1.  在 **[物件總管]** 中，按一下加號，展開包含您想要停用或重新啟動之警示的伺服器。  
  
2.  按一下加號展開 **[SQL Server Agent]**。  
  
3.  按一下加號展開 **[警示]** 資料夾。  
  
4.  以滑鼠右鍵按一下您想要啟用的警示，然後選取 [啟用]。若要停用警示，請以滑鼠右鍵按一下您想要停用的警示，然後選取 [停用]。  
  
5.  畫面上會顯示 **[停用警示]** 或 **[啟用警示]** 對話方塊，並顯示處理的狀態。 完成後，請按一下 **[關閉]**。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-disable-or-reactivate-an-alert"></a>若要停用或重新啟動警示  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]**。  
  
3.  複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]**。  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 如需詳細資訊，請參閱 < [sp_update_alert &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)。  
  
  
