---
title: "隱藏或凍結資料行 (SSAS 表格式) |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 000c14047bf7147215b6f3f6b07e9c87a7bd8a38
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a>隱藏或凍結資料行 (SSAS 表格式)
  在模型設計師中，如果資料表中有您不想要顯示的資料行，可以暫時隱藏起來。 隱藏資料行會讓您在螢幕上有更多的空間，以加入新的資料行或是只處理相關的資料行。 您可以從模型設計師的 [資料行] 功能表，以及從每個資料行標頭所提供的右鍵功能表，來隱藏及取消隱藏資料行。 若要在捲動到模型其他區域時，讓某個模型區域保持可見，您可以執行凍結操作，將特定的資料行鎖定於一個區域之中。  
  
> [!IMPORTANT]  
>  隱藏資料行的功能並不是要用來提供資料安全性，而只是要在模型設計師或報表中簡化及縮短可見資料行清單。 您可以定義安全性角色，以保護資料的安全性。 角色可以限制只有角色中定義的物件，才可以檢視中繼資料和資料。 如需詳細資訊，請參閱 [角色 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/roles-ssas-tabular.md)。  
  
 隱藏資料行時，可以選擇只有在模型設計師或報表中作業時才隱藏資料行。 如果隱藏所有資料行，整個資料表在模型設計師中就會顯示為空白。  
  
> [!NOTE]  
>  如果您需要隱藏許多資料行，可以建立檢視方塊，而非隱藏並取消隱藏資料行。 檢視方塊是資料的自訂檢視，可讓您更輕鬆地使用相關資料的子集。 如需詳細資訊，請參閱[建立及管理檢視方塊 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)  
  
### <a name="to-hide-an-individual-column"></a>隱藏個別資料行  
  
1.  在模型設計師中，選取包含所要隱藏資料行的資料表。  
  
2.  以滑鼠右鍵按一下資料行，然後按一下 [隱藏資料行]，再按一下 [從設計師和報表]、[從報表] 或 [從設計師]。  
  
### <a name="to-hide-multiple-columns"></a>隱藏多個資料行  
  
1.  在模型設計師中，選取包含所要隱藏資料行的資料表。  
  
2.  按一下 [資料行] 功能表，然後按一下 [隱藏和取消隱藏]。  
  
3.  在 [隱藏和取消隱藏資料行] 對話方塊中，找出所要隱藏的每個資料行，然後取消選取 [在設計師中] 及/或 [在報表中]。  
  
4.  按一下 **[確定]**。  
  
### <a name="to-freeze-columns"></a>凍結資料行  
  
1.  在模型設計師中，選取包含所要凍結資料行的資料表。  
  
2.  選取一個或多個要凍結的資料行。  
  
3.  按一下 [資料行] 功能表，然後按一下 [凍結]。  
  
    > [!NOTE]  
    >  凍結資料行時，該資料行會移至設計師之資料表的左方 (或上方)。 取消凍結資料行不會將資料行移回其原始位置。  
  
## <a name="see-also"></a>請參閱＜  
 [資料表與資料行 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)   
 [檢視方塊 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [角色 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
