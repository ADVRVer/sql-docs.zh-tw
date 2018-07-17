---
title: 啟用 DirectQuery 設計模式 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 71fc7ebd-2e86-4a76-994b-66d3a57bcc9b
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93b95dc39c0efb088003af9d5fb8b68cfce11ce9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310408"
---
# <a name="enable-directquery-design-mode-ssas-tabular"></a>啟用 DirectQuery 設計模式 (SSAS 表格式)
  若要建立 DirectQuery 模式的模型，必須先將設計階段環境變更為支援使用 DirectQuery 模式。 當您這樣做時，設計工具還會執行下列操作：  
  
-   啟用 DirectQuery 部署屬性。  
  
-   將工作空間資料庫變更為以混合模式執行，以使用快取進行設計。 在您實際部署模型時，模式會變更回您在專案部署屬性中指定的任何值。  
  
-   停用與 DirectQuery 模式不相容的設計功能。  
  
-   驗證現有的模型。  
  
 此程序描述如何在設計工具中啟用 DirectQuery 模式。  
  
### <a name="to-enable-use-of-directquery-in-a-model"></a>若要在模型中啟用 DirectQuery  
  
1.  在  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，開啟方案檔。  
  
2.  在 [物件總管] 中，按兩下 Model.bim 檔案。  
  
3.  在 [**屬性**] 窗格中，變更屬性， **DirectQueryMode**至**上**。  
  
4.  如果沒有錯誤，在 Visual Studio 中，開啟**錯誤清單**並且解決阻礙模型切換為 DirectQuery 模式的任何問題。  
  
## <a name="see-also"></a>另請參閱  
 [DirectQuery 模式&#40;SSAS 表格式&#41;](directquery-mode-ssas-tabular.md)  
  
  
