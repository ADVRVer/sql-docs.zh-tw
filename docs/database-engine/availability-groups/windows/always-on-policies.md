---
title: 使用群組原則評估可用性群組的健全狀況
description: 了解如何檢視 Always On 儀表板為提供可用性群組健全狀況相關資訊所使用的群組系統原則。
ms.custom: ag-guide, seodec18
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 26bf8f71-c2b8-45ef-b3a3-372b96c9e6e3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d049d012c9447eeb79cd2d64435d37223540adb5
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044604"
---
# <a name="evaluate-health-of-the-always-on-availability-group-using-group-policies"></a>使用群組原則評估 Always On 可用性群組的健全狀況
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Always On 儀表板使用 Always On 可用性群組系統原則，來將可用性群組健全狀況的資訊提供給使用者。 它們對可用性群組操作問題的疑難排解非常有用。 這些原則可以擴充，並用來自訂 Always On 儀表板，或立即執行以報告所需的健康情況資訊。  
  
 有 14 個可用性群組的系統原則。 如需每個原則的詳細資訊，請參閱 [Always On 可用性群組 (SQL Server) 操作問題的 Always On 原則](always-on-policies-for-operational-issues-always-on-availability.md)。  
  
## <a name="view-or-evaluate-availability-groups-system-policies"></a>檢視或評估可用性群組的系統原則  
 若要在 SQL Server Management Studio (SSMS) 中檢視或執行可用性群組的系統原則，請執行以下作業：  
  
1.  在 [物件總管] 中，依序展開 [管理]、[原則管理]、[原則]，然後 [系統原則]。  
  
2.  以滑鼠右鍵按一下其中一個原則，然後按一下 [評估]。 如果您想要評估所選取的原則，那麼您已完成。 您可以在 [目標詳細資料] 方塊中按一下 [檢視]，以查看評估結果的詳細資料。  
  
3.  若要在 [選取頁面] 窗格中檢視所有可用性群組系統原則，按一下 [原則選取]。  
  
## <a name="next-steps"></a>後續步驟  
 [The Always On health model, part 2:Extending the health model](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx) (Always On 健全狀況模型第 2 部分：擴充健全狀況模型)。   
  
  
