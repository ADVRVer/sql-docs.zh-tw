---
title: 查詢繫結詳細資料 （資料分割來源對話方塊） (Analysis Services-多維度資料) |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3e9a9fc76282ebd231e18aec24fe6a9d28650100
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36146386"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>查詢繫結詳細資料 (資料分割來源對話方塊) (Analysis Services - 多維度資料)
  使用 **[資料分割來源]** 對話方塊中的 **[查詢繫結]** 選項，即可指定為資料分割提供資料的查詢。 您可以從 **[資料分割來源]** 對話方塊的 **[繫結類型]** 選項中，選取 **[查詢繫結]** 來顯示此窗格。  
  
## <a name="options"></a>選項。  
 **資料來源**  
 在執行用來為資料分割提供事實資料的查詢上，選取資料來源。  
  
 **[資料集屬性]**  
 當處理資料分割時，鍵入或修改擷取事實資料時使用的 SQL 陳述式。  
  
> [!IMPORTANT]  
>  指定 WHERE 子句，就可以在這個資料分割使用記錄的子集。 當有多個分割區以單一事實資料表為基礎時，這是防止資料重複所必要的。 如需詳細資訊，請參閱[資料分割來源對話方塊&#40;Analysis Services-多維度資料&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)。  
  
 **檢查**  
 按一下即可確認 [查詢] 中的陳述式是否為有效的 SQL 陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [資料分割來源對話方塊&#40;Analysis Services-多維度資料&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  