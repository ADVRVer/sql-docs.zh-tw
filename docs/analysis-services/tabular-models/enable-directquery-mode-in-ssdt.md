---
title: SSDT 中啟用 DirectQuery 模式 |Microsoft 文件
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1d2a1ced9638a48dc02729c0f224b883974a7dde
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34040732"
---
# <a name="enable-directquery-mode-in-ssdt"></a>在 SSDT 中啟用 DirectQuery 模式
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
在本主題中，我們將說明如何在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中啟用表格式模型專案的 DirectQuery 模式。  
  
當您啟用在 SSDT 中所設計之表格式模型的 DirectQuery 模式時︰
-   停用與 DirectQuery 模式不相容的功能。  
-   驗證現有的模型。 如果功能與 DirectQuery 模式不相容，則會顯示警告。  
-   如果先前已在啟用 DirectQuery 模式之前匯入資料，則會清空工作模型的快取。  
  
### <a name="enable-directquery"></a>啟用 DirectQuery  
  
在 SSDT 中，於 **Model.bim** 檔案的 [屬性] 窗格中，將屬性 **DirectQuery Mode** 變更為 **On**。  

![在 SSDT 中啟用 DirectQuery 模式](../../analysis-services/tabular-models/media/enable-directquery-mode-in-ssdt.png)
  
如果模型已有與資料來源和現有資料的連接，系統會提示您輸入用來連接到關聯式資料庫的資料庫認證。 模型內所有現成的資料都會從記憶體內部快取中予以移除。  
  
如果您的模型在啟用 DirectQuery 模式之前已部分或完全完成，您可能會收到不相容功能的錯誤。 請在 Visual Studio 中開啟 [錯誤清單]，並且解決阻礙模型切換為 DirectQuery 模式的任何問題。  


### <a name="whats-next"></a>下一步 
您現在可以使用 [資料表匯入精靈] 匯入資料，來取得模型的中繼資料。 您無法取得資料的資料列，但您會取得資料表、資料行和用做模型基礎的關聯性。 

您可以建立每個資料表的範例資料分割，以及加入範例資料，以便在建置模型時驗證其行為。 您加入的任何範例資料都是用於 **Excel 分析** 或其他可以連接到工作空間資料庫的用戶端工具。 如需詳細資訊，請參閱 [在設計模式中將範例資料加入 DirectQuery 模型中](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md) 。  
  
> [!TIP]  
    >  即使是在空模型的 DirectQuery 模式中，您一律可以檢視每個資料表的小型內建資料列集。 在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中，按一下 [資料表] > [資料表屬性] 以檢視 50 列的資料集。  
  
  
## <a name="see-also"></a>另請參閱  
[在 SSMS 中啟用 DirectQuery 模式](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md)

[在設計模式中將範例資料加入 DirectQuery 模型中](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)
  
