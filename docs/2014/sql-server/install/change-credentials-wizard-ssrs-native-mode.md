---
title: 變更認證精靈 （SSRS 原生模式） |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: c742a02d3accf2a51c2c31bac598064ca34f14c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36132584"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>變更認證精靈 (SSRS 原生模式)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員提供了變更認證精靈，可引導您重新設定報表伺服器用來連接報表伺服器資料庫之帳戶的步驟。 當您變更認證時，組態管理員將會在報表伺服器目前使用之報表伺服器資料庫的資料庫伺服器上，更新所有的權限和資料庫登入資訊。  
  
 若要啟動精靈，請按一下**變更認證**中的 [資料庫] 頁面上[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Configuration Manager。 如需有關如何啟動指示[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Configuration Manager，請參閱[Reporting Services 組態管理員&#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式。  
  
## <a name="options"></a>選項。  
 **資料庫伺服器**  
 指定的名稱[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]執行報表伺服器資料庫的執行個體。  
  
 若要連接到[!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體，您必須使用已登入伺服器及更新資料庫資訊的權限的認證。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager 會使用目前的 Windows 認證，但是如果您沒有登入或資料庫的權限，您可以指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫登入。  
  
 您不能指定不同的 Windows 認證。 如果您想要以不同的 Windows 使用者，登入使用者的身分連線，然後再啟動[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Configuration Manager。  
  
 **認證**  
 指定用來將報表伺服器連接到報表伺服器資料庫的帳戶。 有效值包括報表伺服器 Web 服務的服務帳戶[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上定義的資料庫登入[!INCLUDE[ssDE](../../includes/ssde-md.md)]您用來主控報表伺服器或 Windows 帳戶的執行個體。 如果您使用 Windows 帳戶，您可以指定本機帳戶 (*\<電腦名稱 >\\< 使用者名稱\>*) 如果報表伺服器和資料庫位於同一部電腦或網域使用者帳戶 (*\<網域 >\\< 使用者名稱\>*) 如果它們位於相同網域中的不同電腦上。  
  
 報表伺服器將會建立資料庫登入，並為您指定的帳戶指派資料庫權限。  
  
 報表伺服器不會建立帳戶本身。 您所指定的帳戶必須已經存在，而且對部署組態必須是有效的。 具體而言，如果資料庫位於遠端電腦上，而且您想要使用 Windows 帳戶，您就必須指定在該電腦上具有登入權限的帳戶。  
  
 如果電腦是在不同或不信任網域中，請考慮使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫登入。 如需有關選擇帳戶的詳細資訊，請參閱[設定報表伺服器資料庫連接&#40;SSRS 組態管理員&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。  
  
 **摘要**  
 請在執行精靈之前先確認設定。  
  
 **進度和完成 5d**  
 監視每項工作的進度。  
  
## <a name="see-also"></a>另請參閱  
 [資料庫&#40;SSRS 原生模式&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [變更資料庫精靈&#40;SSRS 原生模式&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [建立原生模式報表伺服器資料庫 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services 組態管理員 F1 說明主題&#40;SSRS 原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [設定報表伺服器資料庫連接&#40;SSRS 組態管理員&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  