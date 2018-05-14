---
title: MSSQLSERVER_948 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00241f105ed79f12177b34be4feadbdcf0a2a290
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver948"></a>MSSQLSERVER_948
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|948|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|NA|  
|訊息文字|無法開啟資料庫 '%.*ls'，因為版本為 %d。 這個伺服器支援 %d 及更早的版本。 不支援降級路徑。|  
  
## <a name="explanation"></a>說明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的某些功能會影響資料庫檔案的結構。 當您將資料庫附加到另一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，檔案格式可能與不同的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 版本不相容。  
  
例如，造成這項錯誤的原因可能是在較新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中使用 Vardecimal 儲存格式，然後嘗試在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 之前的版本中附加資料庫檔案。  
  
## <a name="user-action"></a>使用者動作  
判斷原始伺服器上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下伺服器，然後按一下 [屬性]，或在查詢視窗中鍵入 **SELECT @@VERSION**。 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的原始版本開啟資料庫。 檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中原始資料庫上啟用的功能。 修改這些設定，以搭配用來附加資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。  
  
