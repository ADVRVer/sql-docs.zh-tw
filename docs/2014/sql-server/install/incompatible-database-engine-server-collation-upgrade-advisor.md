---
title: 不相容的 Database Engine 伺服器定序 (Upgrade Advisor) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d2639f783f862e27041985ac27ff16740b47cbb5
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2018
ms.locfileid: "53356758"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>不相容的 Database Engine 伺服器定序 (Upgrade Advisor)
  Upgrade Advisor 偵測到[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]正在使用的執行個體[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]，設定為使用不相容的伺服器定序。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。|  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>描述  
 Upgrade Advisor 偵測到[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]正在使用的執行個體[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]，設定為使用不相容的伺服器定序。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式會使用 SharePoint 共用服務架構。 SharePoint 不支援針對區分大小寫或是伺服器定序或二進位伺服器定序設定的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。 不相容的定序包括預設為區分大小寫或二進位的定序，以及預設不相容，但已透過下列任一定序指示項設定的基底定序：  
  
-   **二進位**  
  
-   **區分大小寫**  
  
-   **二進位字碼指標**  
  
 由於目前的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 伺服器定序不相容，因此升級遭到封鎖。  
  
## <a name="corrective-action"></a>更正動作  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 伺服器定序屬性無法變更。 您將無法完成 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的升級。 您需要將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝移轉至使用相容伺服器定序的新伺服器。 如需詳細資訊，請參閱下列內容：  
  
-   [升級和移轉 Reporting Services](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [選取 SQL Server 定序](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
