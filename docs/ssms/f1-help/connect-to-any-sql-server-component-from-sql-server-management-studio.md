---
title: 連線到任何 SQL Server 元件
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 2fb4150c0c1d659feebac2047094b479b7027087
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87123089"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>從 SQL Server Management Studio 連接到任何 SQL Server 元件

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之各項元件所需的功能。 請利用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來連接到：  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]的執行個體。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]第 1 課：建立 Windows Azure 儲存體物件[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]。  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]第 1 課：建立 Windows Azure 儲存體物件[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]第 1 課：建立 Windows Azure 儲存體物件[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。  
  
雖然 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 可讓您在沒有先建立資料來源連接的情況下，直接使用查詢，但大部分其他工作都需要連接。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 提供 [連接到伺服器]  對話方塊，可讓您設定對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的連線屬性。 當 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 啟動時，便會開啟 [連接到伺服器]  對話方塊，提示您連線到伺服器。 [連接到伺服器]  對話方塊會保留上次使用的連線設定。  
  
> [!NOTE]  
> 您可以關閉這項功能，因此，不會自動起始任何連接。 如需詳細資訊，請參閱 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)。  
  
## <a name="saving-connections"></a>儲存連接  
您可以儲存通往「已註冊的伺服器」中之特定伺服器的連接，也可以利用 [方案總管] 來儲存專案中的連接。  
  
### <a name="saving-connections-in-registered-servers"></a>在已註冊的伺服器中儲存連接  
當您註冊伺服器時， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 會在已註冊的伺服器中儲存連接資訊。 若要連線到已註冊的伺服器，請在 [已註冊的伺服器] 中，選取兩次這個伺服器名稱。 之後，[物件總管] 就會開啟通往伺服器的連接。  
  
### <a name="saving-connections-in-solution-explorer"></a>在 [方案總管] 中儲存連接  
[方案總管] 可讓您在專案中儲存相關的查詢、指令碼、連接和其他相關的資訊。 每個指令碼專案都包含名為 **連線**的節點，讓您可以從中儲存一或多個連線。 若要新增連線，請以滑鼠右鍵選取 [連線] ，然後選取 [新增連線]。 若要存取儲存的連線，請展開 [連線]，然後選取兩次該連線。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 會開啟該連線所關聯的查詢視窗。 儲存好之後，指令碼會保留它們與特定連接的關聯。  
  
## <a name="see-also"></a>另請參閱  
[使用 SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
[物件總管](../../ssms/object/object-explorer.md)  
  
