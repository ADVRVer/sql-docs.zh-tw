---
title: 在 Analysis Services 中建立計算結果的欄 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 705428d2c2a6671452a1d95e06e500f4860574e0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472300"
---
# <a name="create-a-calculated-column"></a>建立導出資料行
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  導出資料行可讓您將新資料加入至模型。 不必貼上或匯入到資料行的值，您可以建立定義資料行的資料列層級值的 DAX 公式。 當您建立有效的公式，然後按一下 ENTER 時，即會計算並填入導出資料行之每個資料列中的值。 然後導出資料行就可以像是其他任何資料行，加入至報表應用程式或分析應用程式。 本文說明如何在模型設計師中使用 DAX 公式列建立新的導出資料行。  
  
#### <a name="to-create-a-new-calculated-column"></a>建立新的導出資料行  
  
1.  在模型設計師的 [資料檢視] 中，選取您要加入導出資料行的資料表，然後按一下 **[資料行]** 功能表，再按一下 **[加入資料行]**。  
  
     **[加入資料行]** 將反白顯示於最右側空白資料行，而且游標會移到公式列。  
  
     若要在兩個現有的資料行之間建立新資料行，請以滑鼠右鍵按一下現有的資料行，然後按一下 [插入資料行]。  
  
2.  在公式列中，執行下列其中一項：  
  
    -   輸入等號，後面接著公式。  
  
    -   輸入等號，後面接著 DAX 函數，然後是函數需要的引數和參數。  
  
    -   按一下函數按鈕 (**fx**)，然後在 [插入函數] 對話方塊中，選取類別目錄和函數，再按一下 [確定]。 在公式列中，輸入函數所需的其餘引數和參數。  
  
3.  按下 ENTER 鍵接受公式。  
  
     整個資料行都會填入公式，而且會針對每個資料列計算值。  
  
> [!TIP]  
>  您可以透過巢狀函數，在現有的公式中間使用 DAX 公式自動完成。 插入點前方的文字用於顯示下拉式清單中的值，而在插入點之後的所有文字則維持不變。  
  
## <a name="see-also"></a>另請參閱  
 [導出資料行](../../analysis-services/tabular-models/ssas-calculated-columns.md)   
 [量值](../../analysis-services/tabular-models/measures-ssas-tabular.md)  
  
  
