---
title: "檢視作業步驟資訊 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 329d7dd7efdd2523b9a992c41654717c64d0d5f2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2017
---
# <a name="view-job-step-information"></a>View Job Step Information
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 本主題說明如何檢視 [作業步驟屬性] 對話方塊中的作業步驟詳細資料。 其中還包括檢視作業步驟輸出的相關資訊。  
  
-   **開始之前：**  
  
    [限制事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **若要使用下列項目檢視作業步驟資訊：**  
  
    [Transact-SQL](#SSMS)  
  
## <a name="BeforeYouBegin"></a>開始之前  
  
### <a name="Restrictions"></a>限制事項  
若作業步驟已設定為將輸出寫入資料表或檔案，且作業已至少執行一次，您就可以在 **[作業步驟屬性]** 對話方塊的 **[進階]** 頁面上檢視其輸出。 當作業或作業步驟被刪除後，輸出記錄檔也會自動刪除。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
若您不是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，就只能檢視您所擁有的作業。 此角色的成員可檢視所有作業與作業步驟詳細資料。  
  
## <a name="SSMS"></a>使用 SQL Server Management Studio  
  
#### <a name="to-view-job-step-information"></a>若要檢視作業步驟資訊  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]的執行個體，然後展開該執行個體。  
  
2.  依序展開 [SQL Server Agent] 和 [作業]、以滑鼠右鍵按一下包含要檢視之作業步驟的作業，然後按一下 [屬性]。  
  
3.  在 **[作業屬性]** 對話方塊中，按一下 **[步驟]** 頁面。  
  
4.  按一下所要檢視的作業步驟，再按一下 **[編輯]**。  
  
5.  在 **[作業步驟屬性]** 對話方塊的 **[一般]** 頁面上，您可以檢視作業步驟的類型及其功能。  
  
6.  按一下 **[進階]** 頁面，即可檢視下列項目： [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 在作業步驟成功或失敗時所應採取的動作、作業步驟應嘗試多少次、寫入作業步驟輸出的位置，以及執行作業步驟的使用者身分。  
  
#### <a name="to-view-job-step-output"></a>若要檢視作業步驟輸出  
  
1.  在 **[作業步驟屬性]** 對話方塊中，按一下 **[進階]** 頁面。  
  
2.  視您所連接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 版本之不同，您可以如下所示檢視作業步驟輸出檔案或資料表：  
  
    -   連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 或更新版本時，只有在已核取 **[記錄至資料表]** 時，才可以按一下 **[檢視]** 。 在這種情況下，作業步驟輸出會寫入 **msdb** 資料庫的 **sysjobstepslogs** 資料表。  
  
    -   若作業步驟輸出寫入檔案中， **[檢視]** 按鈕就會停用。 若要檢視作業步驟輸出檔，請使用 [記事本]。  
  
