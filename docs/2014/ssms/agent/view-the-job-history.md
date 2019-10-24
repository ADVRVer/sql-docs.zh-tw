---
title: 檢視作業記錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- viewing job history
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
- displaying job history
ms.assetid: 3bbd1556-abdb-48a3-b249-546eace76343
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ba38b6a3c425972ef0b893d302df78e3d835f85
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783393"
---
# <a name="view-the-job-history"></a>檢視作業記錄
  此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)] 或 SQL Server 管理物件，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中檢視 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業記錄。  
  
-   **開始之前：**  
  
     [Security](#Security)  
  
-   **若要使用下列項目檢視作業記錄：**  
  
     [Transact-SQL](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理物件](#SMO)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> Security  
 如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。  
  
##  <a name="SSMS"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-view-the-job-history-log"></a>若要檢視作業記錄  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。  
  
2.  展開 **[SQL Server Agent]** ，然後展開 **[作業]** 。  
  
3.  以滑鼠右鍵按一下作業，然後按一下 **[檢視記錄]** 。  
  
4.  在 [記錄檔檢視器] 中檢視作業記錄。  
  
5.  若要更新作業記錄，請按一下 **[重新整理]** 。 若要檢視較少的資料列，請按一下 **[篩選]** 按鈕，並輸入篩選參數。  
  
##  <a name="TSQL"></a> 使用 Transact-SQL  
  
#### <a name="to-view-the-job-history-log"></a>若要檢視作業記錄  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]** 。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。  
  
    ```sql
    -- lists all job information for the NightlyBackups job.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobhistory   
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 如需詳細資訊，請參閱[sp_help_jobhistory &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql)。  
  
##  <a name="SMO"></a>使用 SQL Server 管理物件  
 **若要檢視作業記錄**  
  
 使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，呼叫 `EnumHistory` 類別的 `Job` 方法。 如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。  
