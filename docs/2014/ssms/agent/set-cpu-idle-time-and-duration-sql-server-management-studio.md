---
title: 設定 CPU 閒置與持續時間 (SQL Server Management Studio) | Microsoft Docs
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
- CPU [SQL Server], idle conditions
- time [SQL Server], CPU idle and duration
- duration of CPU idle [SQL Server]
- SQL Server Agent, CPU idle conditions
- idle time [SQL Server]
ms.assetid: 8647b465-d899-4cc7-9640-134a506d0a2e
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7198e25e2d5b38774247073961165fedebae46b8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183795"
---
# <a name="set-cpu-idle-time-and-duration-sql-server-management-studio"></a>設定 CPU 閒置與持續時間 (SQL Server Management Studio)
  本主題說明如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]定義伺服器的 CPU 閒置條件。 CPU 閒置定義會影響 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 回應事件的方式。 例如，假設您將 CPU 閒置條件定義為平均 CPU 使用量低於百分之十且此狀態持續 10 分鐘。 然後，如果您已定義每當伺服器 CPU 達到閒置條件時要執行的作業，當 CPU 使用量低於百分之十且此狀態持續 10 分鐘，將會執行該作業。 如果此作業會明顯影響伺服器的效能，則如何定義 CPU 閒置條件就很重要。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-set-cpu-idle-time-and-duration"></a>若要設定 CPU 閒置時間與期間  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。  
  
2.  以滑鼠右鍵按一下 [SQL Server Agent]，按一下 [屬性]，然後選取 [進階] 頁面。  
  
3.  在 **[閒置 CPU 的條件]** 下方，執行下列步驟：  
  
    -   核取 **[定義閒置 CPU 的條件]**。  
  
    -   在 [平均 CPU 使用量低於]\(所有 CPU) 方塊中指定百分比。 這樣會設定 CPU 必須低於此使用量才會視為閒置。  
  
    -   在 **[並且持續低於此狀態達]** 方塊中指定秒數。 這樣會設定此期間必須維持最小 CPU 用量才會視為閒置。  
  
  
