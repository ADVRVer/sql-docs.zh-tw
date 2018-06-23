---
title: 指定資料行內容和資料類型 （資料採礦精靈） |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0634be64-4c38-4381-9b19-fe9a5889306c
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d8e0802d79913fe796fa636f79b6d728f3900885
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36146614"
---
# <a name="specify-column-content-and-data-type-data-mining-wizard"></a>指定資料行內容和資料類型 (資料採礦精靈)
  使用 **[指定資料行的內容和資料類型]** 頁面，針對每個在精靈的前一頁上所選取的資料行指定使用方式和資料類型。 如果想要忽略資料行，請按一下 **[上一步]** 返回 **[指定培訓資料]**，然後清除所有核取方塊。  
  
 資料行的使用方式代表資料在模型中的使用方式。 資料行可用來當做識別序列的索引鍵、用於分析的輸入值，或者您要預測的值。 資料行可以同時用於預測和輸入。  
  
 資料類型會指定有關資料行所包含之資料類型以及在培訓期間如何使用資料的其他詳細資料。 某些內容類型需要使用特定的資料類型，反之亦然。 根據在建立採礦模型時所使用的演算法，您可能也需要指定特定的資料類型。 如需採礦模型和結構中的內容類型及資料類型的資訊，請參閱[內容類型 &#40;資料採礦&#41;](data-mining/content-types-data-mining.md)。  
  
 **如需詳細資訊︰**[採礦結構 &#40;Analysis Services - 資料採礦&#41;](data-mining/mining-structures-analysis-services-data-mining.md)、[採礦模型資料行](data-mining/mining-model-columns.md)、[資料採礦精靈 &#40;Analysis Services - 資料採礦&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>選項。  
 **採礦模型結構**  
 顯示在精靈的上一頁上所選取的檢視及巢狀資料表的資料行。  
  
 **資料行**  
 列出資料行。  
  
 **內容類型**  
 指定資料行的內容類型。 如果將資料行指定為精靈前一頁上的索引鍵，則可使用下列值：  
  
|選項|描述|  
|------------|-----------------|  
|索引鍵|指定資料行包含案例序列的唯一識別碼。|  
|Key Sequence|指定資料行包含順序識別碼。|  
|Key Time|指定資料行包含日期或其他的唯一連續號碼，以用來識別日期或時間序列。|  
  
 如果將資料行選取為非索引鍵的資料行，則根據資料類型，可以使用下列值：  
  
|選項|描述|  
|------------|-----------------|  
|Continuous|指定資料行包含連續的數字值。|  
|Discretized|指定資料行包含的數字值已離散化，或可以視為離散的值。|  
|Discrete|指定資料行包含文字或其他非數字的值。|  
  
 **Data type**  
 指定資料行的資料類型。  
  
 有下列可用的值：  
  
-   `Boolean`  
  
-   `Date`  
  
-   `Double`  
  
-   `Long`  
  
-   `Text`  
  
 **偵測**  
 分析所有數字資料行中的資料範例。 以推薦的內容類型取代指定的 **[內容類型]** 值。  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦精靈 F1 說明&#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [建議相關資料行&#40;資料採礦精靈&#41;](suggest-related-columns-data-mining-wizard.md)   
 [指定資料表類型&#40;資料採礦精靈&#41;](specify-table-types-data-mining-wizard.md)   
 [指定資料行的內容和資料型別&#40;資料採礦精靈&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  