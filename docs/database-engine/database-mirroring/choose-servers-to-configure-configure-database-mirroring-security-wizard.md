---
title: 選取要設定的伺服器 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.choosesrvrs.f1
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 31c9ce74c6638925b1a91ab6d63abb8c759324cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66774963"
---
# <a name="choose-servers-to-configure-configure-database-mirroring-security-wizard"></a>選取要設定的伺服器 (設定資料庫鏡像安全性精靈)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  使用此頁面來指定現在要設定的伺服器執行個體。 您必須至少選取一個伺服器執行個體才能繼續執行精靈。  
  
 如果清除某個伺服器執行個體的核取方塊，則精靈將不會對其做任何變更。 不過，精靈會要求您輸入有關該執行個體的資訊，並將此資訊另存為其他伺服器執行個體組態的一部分。 例如，若您清除見證伺服器執行個體的核取方塊，精靈將會要求您輸入該見證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶，因為必須將該帳戶的登入建立為安全性組態的一部分，並儲存在主體和鏡像伺服器執行個體中。  
  
 **若要使用 SQL Server Management Studio 設定資料庫鏡像**  
  
-   [使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>選項。  
 **主體伺服器執行個體**  
 選取以設定主體伺服器的安全性。  
  
 **鏡像伺服器執行個體**  
 選取以設定鏡像伺服器的安全性。  
  
 **見證伺服器執行個體**  
 選取以設定見證伺服器的安全性 (如果有的話)。  
  
## <a name="see-also"></a>另請參閱  
 [資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
