---
title: 執行 SQL Server Agent 作業工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.executejob.f1
helpviewer_keywords:
- Execute SQL Server Agent Job Task dialog box
ms.assetid: 4ed75956-ebb8-4d8c-9c16-fc0eb00bd3a0
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8f361eb5bc910d4c584b3aab42772803650b3128
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "40405914"
---
# <a name="execute-sql-server-agent-job-task-maintenance-plan"></a>執行 SQL Server Agent 作業工作 (維護計畫)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  使用 [執行 SQL Server Agent 作業工作] 對話方塊，即可在維護計畫內執行 Microsoft SQL Server Agent 作業。 如果選取的連接上沒有 SQL Server Agent 作業，將無法使用此選項。  
  
 此工作使用 **.sp_start_job** 陳述式。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **[連接]**  
 選取執行此工作時要使用的伺服器連接。  
  
 **新增**  
 建立新的伺服器連接，以便執行此工作時使用。 下面會描述 **[新增連接]** 對話方塊。  
  
 **可用的 SQL 代理程式作業**  
 選取要執行的作業。 方格提供 [作業名稱] 和 [描述] 來識別作業。  
  
 **檢視 T-SQL**  
 根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。  
  
> [!NOTE]  
>  受影響的物件數目較為大量時，會多花一些時間才會顯示。  
  
## <a name="new-connection-dialog-box"></a>新增連接對話方塊  
 **連接名稱**  
 輸入新連接的名稱。  
  
 **選取或輸入伺服器名稱**  
 選取執行此工作時要連接的伺服器。  
  
 **[重新整理]**  
 重新整理可用的伺服器清單。  
  
 **輸入要登入到伺服器的資訊**  
 指定如何對伺服器進行驗證。  
  
 **使用 Windows 整合式安全性**  
 使用 Microsoft Windows 驗證來連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。  
  
 **使用特定的使用者名稱和密碼**  
 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。 無法使用此選項。  
  
 **User name**  
 提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。 無法使用此選項。  
  
 **密碼**  
 提供驗證時要使用的密碼。 無法使用此選項。  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [建立作業](../../ssms/agent/create-a-job.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)  
  
  
