---
title: 定義貨幣轉換 （商業智慧精靈） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.existingscriptpage.f1
ms.assetid: 37dd65b7-9d8d-44ad-b316-96a92c622472
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce1916bd988d23dfd33f689f189436a50408a207
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159509"
---
# <a name="define-currency-conversion-business-intelligence-wizard"></a>定義貨幣轉換 (商業智慧精靈)
  使用 [定義貨幣轉換] 頁面來檢閱多維度運算式 (MDX) 指令碼，該指令碼包含 [商業智慧精靈] 所產生的貨幣轉換功能。 然後，您可以使用此精靈產生的 MDX 指令碼，在 Cube 的 MDX 指令碼中覆寫或附加之前定義的貨幣轉換功能。  
  
> [!NOTE]  
>  只有商業智慧精靈在 Cube 的 MDX 指令碼中偵測到至少有一個之前定義的貨幣轉換時，才會出現此頁面。 在 Cube 的 MDX 指令碼中，利用下列註解包覆貨幣轉換：  
>   
>  `//<Currency conversion>`  
>   
>  `...`  
>   
>  `[MDX statements for the currency conversion]`  
>   
>  `...`  
>   
>  `//</Currency conversion>`  
>   
>  如果您變更或移除這些註解，商業智慧精靈可能無法偵測到任何之前定義的貨幣轉換。  
  
## <a name="options"></a>選項。  
 **新增貨幣轉換指令碼**  
 顯示由目前商業智慧精靈工作階段產生的 MDX 指令碼。  
  
 **覆寫現有的貨幣轉換指令碼**  
 選取以使用 [新增貨幣轉換指令碼] 中所顯示的 MDX 指令碼，來覆寫 [現有的貨幣轉換指令碼] 中所顯示的 MDX 指令碼。  
  
 **附加於後面**  
 選取即可將 [新增貨幣轉換指令碼] 中所顯示的 MDX 指令碼，附加至 [現有的貨幣轉換指令碼] 中所顯示之 MDX 指令碼的結尾處。 附加的指令碼會顯示為新的區段。  
  
 **現有的貨幣轉換指令碼**  
 選取現有 MDX 指令碼的區段，其中包含要覆寫或附加的之前定義的貨幣轉換功能。  
  
## <a name="see-also"></a>另請參閱  
 [商業智慧精靈 F1 說明](business-intelligence-wizard-f1-help.md)   
 [Cube 設計師&#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [維度設計師&#40;Analysis Services-多維度資料&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
