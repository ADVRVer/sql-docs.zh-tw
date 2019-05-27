---
title: 報表伺服器 (Upgrade Advisor) 上偵測到自訂報表項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 778f626e64bdacb3eff57f20f749d24628baaec2
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66095924"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>在報表伺服器上偵測到自訂報表項目 (Upgrade Advisor)
  針對舊版所建立的自訂報表項目[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]與不相容[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。 雖然升級可以繼續進行，但是使用自訂報表項目的報表將無法如預期方式執行。 Upgrade Advisor 偵測到自訂報表項目。 雖然升級可以繼續進行，但是您必須在升級完成之後，手動將自訂報表項目檔案移至新的安裝資料夾。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。|  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>描述  
 Upgrade Advisor 偵測到組態檔中有自訂 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 延伸模組設定，表示安裝包括報表的一個或多個自訂組件。  
  
## <a name="corrective-action"></a>更正動作  
 升級完成之後，請手動將自訂報表項目檔案移至新的安裝資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 升級問題&#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
