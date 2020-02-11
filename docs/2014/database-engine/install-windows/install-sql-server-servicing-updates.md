---
title: 安裝 SQL Server 2014 服務更新 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 07f438f86a22b866351a0b83ee7634338f3ad2cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "62775341"
---
# <a name="install-sql-server-2014-servicing-updates"></a>安裝 SQL Server 2014 服務更新
  本主題提供有關安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]更新的資訊。 本節提供下列作業的相關資訊：  
  
-   在進行新安裝期間安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的更新。  
  
-   在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝完成之後安裝更新。  
  
 我們建議客戶及時評估並安裝最新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新，以便確保系統保持在最新狀態而且具有最新的安全性更新。  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-during-a-new-installation"></a>在進行新安裝期間安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的更新。  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式會整合最新產品更新與主要產品安裝，因此主要產品及其適用的更新可同時安裝。 產品更新可以從下列位置搜尋適用的更新：  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Windows Server Update Services (WSUS)  
  
-   本機資料夾  
  
-   網路共用  
  
 安裝程式找到最新版本的可用更新後，會使用目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程序進行下載與整合。 產品更新可能包括累計更新、Service Pack，或 Service Pack 加上累計更新。 產品更新功能是 PCU1 中[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]提供之彙集[功能](https://go.microsoft.com/fwlink/?LinkId=219945)的延伸模組。  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝完成之後安裝更新  
 在已安裝的[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]實例上，建議您套用所有可用的更新：一般發行版本（GDR-安全性/重大更新）、Service PACK （SP）以及最新可用的累計更新（CU）。  
  
 視服務版本的類型而定，您可以透過 Microsoft Update （MU）、Microsoft 下載中心及/或客戶支援服務的修補伺服器來取得 SQL Server 更新。 Microsoft Update 會自動提供 SQL Server 的安全性和重大更新（若要查看這些更新，您必須透過 [控制台] 中的 Windows Update 加入宣告 MU）。 在 MU 上提供 Service Pack 做為選擇性/重要下載，以及下載中心。 在 CU 知識庫文章中提供的 Microsoft 修復程式下載伺服器上提供累計更新。  
  
## <a name="see-also"></a>另請參閱  
 [從安裝精靈安裝 SQL Server 2014 &#40;安裝程式&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [從命令提示字元安裝更新](installing-updates-from-the-command-prompt.md)[將功能新增至 SQL Server 2014 &#40;安裝程式的實例&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [卸除 SQL Server 2014 安裝](repair-a-failed-sql-server-installation.md)  
  
  
