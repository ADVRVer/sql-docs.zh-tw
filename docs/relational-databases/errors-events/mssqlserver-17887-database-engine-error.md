---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb10e2970cf8612486bb515e8e8d88ba483ef4a0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17887"></a>MSSQLSERVER_17887
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|17887|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SRV_IO_COMP_LISTENER_NONYIELDING|  
|訊息文字|IO Completion Listener (0x%lx) 工作者 0x%p 在節點 %ld 上似乎沒有產量。 已使用的約略 CPU: 核心 %I64d ms，使用者 %I64d ms，間隔: %I64d。|  
  
## <a name="explanation"></a>說明  
表示針對網路讀取/寫入事件執行 I/O 完成常式時，指定之節點上的 I/O 完成通訊埠 (Completion Port) 接聽程式可能發生問題。 當 I/O 完成通訊埠接聽程式從執行 I/O 完成常式返回時，這個錯誤就會消失。  
  
## <a name="user-action"></a>使用者動作  
請連絡 Microsoft 客戶支援服務 (CSS)。  
  
