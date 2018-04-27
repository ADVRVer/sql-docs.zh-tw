---
title: 檢視套件物件 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 507ec523ca3a3ea1a485b0dd146c783cc32b65f7
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="view-package-objects"></a>檢視封裝物件
  在「[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」中，[封裝總管] 索引標籤提供封裝的總管檢視。 此檢視反映 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 架構的容器階層。 封裝容器位於階層的頂端，您可以展開封裝以檢視其中的連接、可執行檔、事件處理常式、記錄提供者、優先順序條件約束和變數。  
  
 可執行檔 (封裝中的容器和工作) 可包含事件處理常式、優先順序條件約束和變數。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 支援容器的巢狀階層，而「For 迴圈」、「Foreach 迴圈」和「時序」容器可包含其他可執行檔。  
  
 如果某個封裝包含資料流程，封裝總管會列出「資料流程」工作，並包含一個列出資料流程元件的 [元件] 資料夾。  
  
 藉由 [封裝總管] 索引標籤，您可以刪除封裝中的物件並存取 [屬性] 視窗以檢視物件屬性。  
  
 下圖顯示簡單封裝的樹狀檢視。  
  
 ![[套件總管] 索引標籤的螢幕擷取畫面](../integration-services/media/packageexplorer.gif "[套件總管] 索引標籤的螢幕擷取畫面")  
  
## <a name="view-the-package-structure-and-content"></a>檢視套件結構和內容  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含您要在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [封裝總管] **中檢視之封裝的**專案。  
  
2.  按一下 **[封裝總管]** 索引標籤。  
  
3.  若要檢視 **[變數]**、 **[優先順序條件約束]**、 **[事件處理常式]**、 **[連接管理員]**、 **[記錄提供者]** 或 **[可執行檔]** 資料夾的內容，請展開各個資料夾。  
  
4.  視封裝結構而定，展開任何下一層級資料夾。  
  
## <a name="view-the-properties-of-a-package-object"></a>檢視套件物件的屬性
  
-   以滑鼠右鍵按一下物件，然後按一下 [屬性]以開啟 [屬性] 視窗。  
  
## <a name="delete-an-object-in-a-package"></a>刪除套件中的物件  
  
-   以滑鼠右鍵按一下物件，然後按一下 [刪除]。 
 
## <a name="see-also"></a>另請參閱  
 [Integration Services 工作](../integration-services/control-flow/integration-services-tasks.md)   
 [Integration Services 容器](../integration-services/control-flow/integration-services-containers.md)   
 [優先順序條件約束](../integration-services/control-flow/precedence-constraints.md)   
 [Integration Services &#40;SSIS&#41; 變數](../integration-services/integration-services-ssis-variables.md)   
 [Integration Services &#40;SSIS&#41; 事件處理常式](../integration-services/integration-services-ssis-event-handlers.md)   
 [Integration Services &#40;SSIS&#41; 記錄](../integration-services/performance/integration-services-ssis-logging.md)  
  
  
