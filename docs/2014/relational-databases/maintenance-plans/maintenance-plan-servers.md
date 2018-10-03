---
title: 維護計畫 (伺服器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: df05d1f7bdbcf2f149caf1b82b592607d588b0ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050409"
---
# <a name="maintenance-plan-servers"></a>維護計畫 (伺服器)
  使用 **[伺服器]** 對話方塊可選取要執行維護計畫的伺服器。  
  
 若要建立多伺服器維護計畫，必須設定多伺服器環境，其中包含一個主要伺服器以及一或多個目標伺服器。 針對多伺服器維護計畫，本機伺服器應設為主要伺服器。 在多伺服器環境中，這個對話方塊會顯示 **(本機)** 主要伺服器以及所有相對應的目標伺服器。 本機伺服器會建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業。 這會視您是否選取 **(本機)** 伺服器而啟用或停用。 如果選取目標伺服器，會建立多伺服器作業並下載到每個選取的目標伺服器。 如果沒有選取目標伺服器，會刪除多伺服器作業。  
  
## <a name="see-also"></a>另請參閱  
 [維護計畫](maintenance-plans.md)   
 [建立多伺服器環境](../../ssms/agent/create-a-multiserver-environment.md)   
 [設為主要伺服器](../../ssms/agent/make-a-master-server.md)   
 [設為目標伺服器](../../ssms/agent/make-a-target-server.md)  
  
  
