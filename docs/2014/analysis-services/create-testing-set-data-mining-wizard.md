---
title: 建立測試集（資料採礦嚮導） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.holdout.f1
ms.assetid: d0a44b59-ffbd-45fc-baa8-6b8046b1a2f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f0e4d1a384995c0c49c346102f8fddbcdf47f68
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086784"
---
# <a name="create-testing-set-data-mining-wizard"></a>建立測試集 (資料採礦精靈)
  使用 [建立測試集]**** 頁面來指定用於定型的資料量，以及保留用於測試集的資料量。 在建立採礦結構時將資料分割成定型集和測試集，可以更輕鬆地評估您稍後建立的採礦模型的正確性。  
  
 您可以將測試資料量指定為百分比，或者可以指定數字以限制用於測試的案例數。 如果同時指定了用於測試的案例百分比以及案例數上限，則這兩種設定都會使用，且測試資料集會包含較少的案例數。 根據預設，測試會使用 30% 的資料，定型則使用 70%，且測試案例數沒有上限。  
  
 根據預設，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會產生用來啟動資料分割的數值種子。 此種子是根據採礦結構的名稱而定。 如果想要在採礦結構的名稱變更時仍確保資料分割維持相同狀況，可以設定採礦結構的 HoldoutSeed 屬性來指定種子的值。 如果變更鑑效組種子，則必須重新處理結構。  
  
 如果您稍後想要變更測試或定型資料的數量，您可以使用 [**屬性**] `HoldoutMaxPercent`視窗來修改資料採礦結構上的`HoldoutMaxCases`和屬性。 不過，在進行變更後，必須重新處理採礦結構及所有相關聯的採礦模型。 同時適用下列限制：  
  
-   只有當資料採礦結構是儲存於 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 時，才支援資料採礦結構的資料分割。 舊版的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]不支援快取資料分割資訊，以進行採礦結構。  
  
-   如果採礦結構包含 Key Time 資料行 (必須用於時間序列採礦模型)，則無法對採礦結構進行資料分割。  
  
-   如果想要預測儲存於巢狀資料表中的值，則無法分割資料。  
  
 **如需詳細資訊：** [&#40;資料採礦&#41;進行測試和驗證](data-mining/testing-and-validation-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)、[基本資料採礦教學](../../2014/tutorials/basic-data-mining-tutorial.md)課程  
  
## <a name="options"></a>選項。  
 **測試資料的百分比**  
 請按一下向上或向下箭號來增加或減少用來當做定型集的資料百分比，或在文字方塊中輸入 0 和 100 之間的值。  
  
 **測試資料集中的案例數上限**  
 輸入數字，以限制可用於測試的案例數。  
  
 如果指定的值大於資料中的實際案例數，就會使用所有的案例。  
  
 預設值是 NULL。 這表示沒有限制。  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [建議相關資料行 &#40;Data 採集 Wizard&#41;](suggest-related-columns-data-mining-wizard.md)   
 [指定資料表類型 &#40;資料採礦嚮導&#41;](specify-table-types-data-mining-wizard.md)   
 [指定資料行的內容和資料類型 &#40;[Data] [Wizard]&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
