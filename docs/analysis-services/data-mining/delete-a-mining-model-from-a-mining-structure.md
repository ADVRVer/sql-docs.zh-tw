---
title: "從採礦結構刪除採礦模型 |Microsoft 文件"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 470e1d74434261b08c47f93c060c4ac4da143cb2
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>從採礦結構刪除採礦模型
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]您可以刪除採礦模型使用資料採礦設計師中，使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，或使用 DMX 陳述式。  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>使用 SQL Server 資料工具刪除採礦模型  
  
1.  選取 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的 [採礦模型] 索引標籤。  
  
2.  以滑鼠右鍵按一下您想刪除的模型，然後選取 [刪除]。  
  
     [刪除物件] 對話方塊就會開啟。  
  
3.  按一下 **[確定]**。  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>使用 SQL Server Management Studio 刪除採礦模型  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，開啟包含模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。  
  
2.  展開 [採礦結構]，然後展開 [採礦模型]。  
  
3.  以滑鼠右鍵按一下您想刪除的模型，然後選取 [刪除]。  
  
     刪除模型並不會刪除定型資料，只刪除定型模型時建立的中繼資料和所有模式。  
  
### <a name="delete-a-mining-model-using-dmx"></a>使用 DMX 刪除採礦模型  
  
-   [DROP MINING MODEL &#40;DMX&#41;](../../dmx/drop-mining-model-dmx.md)  
  
## <a name="see-also"></a>請參閱  
 [採礦模型工作和使用說明](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
