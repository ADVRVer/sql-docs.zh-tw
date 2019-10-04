---
title: 未設定報表伺服器資料庫（Upgrade Advisor） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: bb5dd5968930319532a29ff7c3909c36af99b3a0
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952114"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>未設定報表伺服器資料庫 (Upgrade Advisor)
  由於報表伺服器組態不完整，因此系統封鎖了升級。 未設定報表伺服器資料庫。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。|  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>描述  
 安裝程式只能升級已完全設定的報表伺服器執行個體。 若要繼續，您必須設定報表伺服器資料庫，或使用 Microsoft Windows [**控制台**]，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中移除報表伺服器功能。 在您移除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之後，就可以升級其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件。  
  
## <a name="corrective-action"></a>更正動作  
 如果您並未設定報表伺服器資料庫，報表伺服器便無法運作，而且您應該在升級之前移除它。  
  
 如需卸載 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的詳細資訊，請參閱[卸載 Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\))。 該主題描述如何解除安裝特定版本，而且程序與舊版的程序相似。  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 升級問題&#40;upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
