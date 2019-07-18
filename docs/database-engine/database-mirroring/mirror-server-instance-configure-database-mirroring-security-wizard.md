---
title: 鏡像伺服器執行個體 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.mirrorsrvr.f1
ms.assetid: 53223432-615e-440f-904d-925d33ec2144
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: ee3fcfb29de3f029c8229e0092ee31c8a8faa007
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795384"
---
# <a name="mirror-server-instance-configure-database-mirroring-security-wizard"></a>鏡像伺服器執行個體 (設定資料庫鏡像安全性精靈)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  使用此頁面來指定有關使用鏡像資料庫之伺服器執行個體的資訊。  
  
> [!IMPORTANT]  
>  鏡像伺服器執行個體必須執行與主體伺服器執行個體相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本 (Standard 或 Enterprise)。 此外，我們強烈建議您在可比較而且可以處理相同工作負載的系統上執行這些伺服器執行個體。  
  
 **若要使用 SQL Server Management Studio 設定資料庫鏡像**  
  
-   [使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>選項。  
 **鏡像伺服器執行個體**  
 如果已經指定鏡像伺服器執行個體 (在 [資料庫屬性]  對話方塊的 [鏡像]  頁面上)，則會顯示該執行個體；如需詳細資訊，請參閱[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)。  
  
 否則，請輸入鏡像伺服器執行個體的名稱。 請注意，鏡像伺服器執行個體不可以與主體伺服器執行個體相同。  
  
 **[連接]**  
 如果未指定鏡像伺服器執行個體，請按一下 [連接]  。 這會顯示 **[連接到伺服器]** 對話方塊，您可以在其中指定伺服器執行個體並建立連接。  
  
 如果已指定執行個體，但精靈缺少具備檢查端點是否存在之權限的連接，請按一下 **[連接]** 。 隨即顯示已預先選取伺服器執行個體的 [連接到伺服器]  對話方塊，且無法變更。 指定具備足夠權限的網域帳戶，然後連接到伺服器執行個體。  
  
> [!NOTE]  
>  連接到伺服器執行個體時，「設定資料庫鏡像安全性精靈」會使用 **[連接到伺服器]** 對話方塊中提供的認證。 這些認證與鏡像工作階段的認證不同，後者會使用以服務方式執行伺服器執行個體之啟動帳戶的認證。  
  
 **接聽程式通訊埠**  
 此選項的行為會視此伺服器執行個體的鏡像端點是否存在，如下：  
  
-   如果伺服器執行個體沒有接聽程式通訊埠，在 **[通訊埠]** 文字方塊中就會顯示通訊埠編號 5022。 您可以使用任何可用的通訊埠編號，例如 7022。  
  
-   當鏡像端點已經存在時，會顯示來自該端點的通訊埠編號。 如果您需要變更通訊埠，請使用 ALTER ENDPOINT 命令。 如需詳細資訊，請參閱 [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md)。  
  
    > [!NOTE]  
    >  需要通訊埠編號。  
  
 **端點名稱**  
 如果這個伺服器執行個體存在有鏡像端點，該端點名稱會顯示於此處。 如果端點不存在，您可以指定端點名稱。  
  
 **透過此端點傳送的資料要加密**  
 依預設，加密為已啟用。 當已啟用時，加密為必須的 (不只是支援的)，並且所有的加密選項都使用預設值。 如需詳細資訊，請參閱 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)的相關資訊。  
  
 若要停用加密，請清除該核取方塊。 若要重新啟用加密，請選取該核取方塊。  
  
## <a name="see-also"></a>另請參閱  
 [資料庫鏡像端點 &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
