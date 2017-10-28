---
title: "SQL Server Agent 屬性 (連接頁面) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bfc821d303f7da943a39e18fe8221aefeaefceab
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-agent-properties-connection-page"></a>SQL Server Agent 屬性 (連接頁面)
使用此頁面檢視及修改 [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 服務與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 之間的連線設定。  
  
## <a name="options"></a>選項。  
**別名本機主機伺服器**  
指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]之本機執行個體的別名。 如果您無法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 的預設連接選項，請為執行個體定義別名，並在此處指定該別名。  
  
**使用 Windows 驗證**  
將 [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 驗證設定為連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 執行個體的驗證方法。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 會以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent 服務執行身分帳戶連線。  
  
**使用 SQL Server 驗證**  
設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 驗證為連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 執行個體的驗證方法。  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 提供驗證的目的在提供回溯相容性。 為了提升安全性，如果可能的話請使用 Windows 驗證。  
  
**登入**  
指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]的登入名稱。  
  
**密碼**  
指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]的密碼。  
  

