---
title: 刪除作業類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f939a713df2fb40f1b56fd0aee5f7b5c5876a4a0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196568"
---
# <a name="delete-a-job-category"></a>刪除作業類別目錄
  此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)] 或 SQL Server 管理物件，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中刪除 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業類別目錄。  
  
 作業類別目錄可幫助您組織作業，以便於篩選與分組。 例如，您可以將所有的資料庫備份作業整理在資料庫維護類別中。  
  

  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
 當您刪除使用者定義的作業類別目錄時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會提示您將已指定給該類別目錄的作業重新指定給其他作業類別目錄。 您只能刪除使用者定義的作業類別目錄。  
  
###  <a name="Security"></a> 安全性  
 如需詳細資訊，請參閱＜ [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)＞。  
  

  
##  <a name="SSMS"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-delete-a-job-category"></a>若要刪除作業類別目錄  
  
1.  在 **[物件總管]** 中，按一下加號展開要刪除作業類別目錄所在的伺服器。  
  
2.  按一下加號展開 **[SQL Server Agent]**。  
  
3.  以滑鼠右鍵按一下 [作業] 資料夾，然後選取 [管理作業類別目錄]。  
  
4.  在 [管理作業類別目錄 <伺服器名稱>] 對話方塊中，選取所要刪除的作業類別目錄。  
  
5.  按一下 **[刪除]**。  
  
6.  在 **[作業類別目錄]** 對話方塊中，按一下 **[是]**。  
  
7.  關閉 [管理作業類別目錄 <伺服器名稱>] 對話方塊。  
  

  
##  <a name="TSQL"></a> 使用 Transact-SQL  
  
#### <a name="to-delete-a-job-category"></a>若要刪除作業類別目錄  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在標準列上，按一下 **[新增查詢]**。  
  
3.  複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]**。  
  
    ```  
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 如需詳細資訊，請參閱 < [sp_delete_category &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql)。  
  

  
##  <a name="SMO"></a> 使用 SQL Server 管理物件  
 **若要刪除作業類別目錄**  
  
 呼叫`JobCategory`藉由使用您選擇，例如 Visual Basic、 Visual C# 或 PowerShell 的程式語言的類別。  
  

  
  
