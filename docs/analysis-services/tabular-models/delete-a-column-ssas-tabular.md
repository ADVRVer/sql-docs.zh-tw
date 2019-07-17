---
title: 刪除 Analysis Services 表格式模型中的資料行 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f61aea9e4751094dafd37fe3b9ca8ed8d6ef0fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207706"
---
# <a name="delete-a-column"></a>刪除資料行 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  本文說明如何從表格式模型資料表中刪除資料行。  
  
## <a name="delete-a-model-table-column"></a>刪除模型資料表資料行  
  
> [!NOTE]  
>  從模型資料表中刪除資料行時，並不會從資料分割查詢定義中刪除該資料行。 如果您要刪除的資料行屬於資料分割的一部分，就必須從資料分割查詢定義中手動刪除該資料行。 如果沒有從資料分割查詢定義中刪除資料行，將會導致系統在處理作業期間查詢該資料行並且傳回資料，但是不會擴展至模型資料表。 如需詳細資訊，請參閱 <<c0> [ 分割區](../../analysis-services/tabular-models/partitions-ssas-tabular.md)。  
  
#### <a name="to-delete-a-model-table-column"></a>若要刪除模型資料表資料行  
  
-   在模型設計師中，於包含您想要刪除之資料行的資料表內，以滑鼠右鍵按一下資料行，然後按一下 [刪除]  。  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>若要使用資料表屬性對話方塊來刪除模型資料表資料行  
  
1.  在模型設計師中，按一下包含您想要刪除之資料行的資料表、按一下 [資料表]  功能表，然後按一下 [資料表屬性]  。  
  
2.  在 [資料行名稱來自]  中，選取 [模型]  (使用模型資料表資料行名稱，如果與來源不同的話  )。  
  
3.  在 [編輯資料表屬性]  對話方塊的 [資料表預覽] 視窗中，取消核取您想要刪除的資料行，然後按一下 [確定]  。  
  
## <a name="see-also"></a>另請參閱  
 [將資料行加入資料表](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [資料分割](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  
