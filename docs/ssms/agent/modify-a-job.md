---
title: Modify a Job
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 006ba96e2d614be47c7298a2320df0cf03ec81f0
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2020
ms.locfileid: "75245216"
---
# <a name="modify-a-job"></a>Modify a Job

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支援多數 (但非全部) 的 SQL Server Agent 功能。 如需詳細資料，請參閱 [Azure SQL Database 受控執行個體與 SQL Server 之間的 T-SQL 差異](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

本主題描述如何使用 [!INCLUDE[msCoName](../../includes/msconame_md.md)]、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 SQL Server 管理物件，以在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中變更 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Agent 作業的屬性。  

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>開始之前  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>限制事項  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主要作業無法同時存在於本機和遠端伺服器內。  
  
### <a name="security"></a><a name="Security"></a>安全性  
除非您是系統管理員 ( **sysadmin** ) 固定伺服器角色的成員，否則您只能修改您所擁有的作業。 如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](../../ssms/agent/implement-sql-server-agent-security.md)＞。  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>使用 SQL Server Management Studio  
  
#### <a name="to-modify-a-job"></a>若要修改作業  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]的執行個體，然後展開該執行個體。  
  
2.  展開 [SQL Server Agent]  ，展開 [作業]  ，以滑鼠右鍵按一下要修改的作業，然後按一下 [屬性]  。  
  
3.  在 **[作業屬性]** 對話方塊中，利用相對應的頁面更新作業的屬性、步驟、排程、警示及通知。  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>使用 Transact-SQL  
  
#### <a name="to-modify-a-job"></a>若要修改作業  
  
1.  在 [物件總管] 中，連接到 Database Engine 的執行個體，然後展開該執行個體。  
  
2.  在工具列上，按一下 **[新增查詢]** 。  
  
3.  在查詢視窗中，使用下列系統預存程序修改作業。  
  
    -   執行 [sp_update_job (TRANSACT-SQL)](https://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623) 變更作業的屬性。  
  
    -   執行 [sp_update_schedule (Transact-SQL)](https://msdn.microsoft.com/97b3119b-e43e-447a-bbfb-0b5499e2fefe) 變更作業定義的排程詳細資料。  
  
    -   執行 [sp_add_jobstep (Transact-SQL)](https://msdn.microsoft.com/97900032-523d-49d6-9865-2734fba1c755) 新增作業步驟。  
  
    -   執行 [sp_update_jobstep (Transact-SQL)](https://msdn.microsoft.com/e158802c-c347-4a5d-bf75-c03e5ae56e6b) 變更已存在的作業步驟。  
  
    -   執行 [sp_delete_jobstep (TRANSACT-SQL)](https://msdn.microsoft.com/421ede8e-ad57-474a-9fb9-92f70a3e77e3) 從作業移除作業步驟。  
  
    -   修改任何 SQL Server Agent 主要作業的其他預存程序：  
  
        -   執行 [sp_delete_jobserver (Transact-SQL)](https://msdn.microsoft.com/6d63ed32-68cf-4d8f-aa40-05a3826e05b8) 刪除目前與作業相關聯的伺服器。  
  
        -   執行 [sp_add_jobserver (Transact-SQL)](https://msdn.microsoft.com/485252cc-0081-490a-9bd1-cbbd68eea286) 讓伺服器與目前作業產生關聯。  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>使用 SQL Server 管理物件  
**若要修改作業**  
  
透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 **Job** 類別。 如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。  
  
