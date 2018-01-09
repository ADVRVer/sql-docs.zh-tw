---
title: "視覺化總計和非視覺化總計 |Microsoft 文件"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4d85d2ce789793c03fa99d51451e1a64d0868962
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="visual-totals-and-non-visual-totals"></a>視覺化總計和非視覺化總計
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]視覺化總計是結尾的資料行或資料列的加總所有可見資料行或資料列中的項目。 這是大部分資料表顯示時的預設行為。 不過，有時候使用者只想要顯示資料表中的某些資料行，但保持整個資料列的總計，包括未顯示的資料行。 這些稱為「非視覺化總計」，因為總計來自可見和不可見的值。  
  
 下列案例示範非視覺化總計的行為。 第一個步驟示範視覺化總計的預設行為。  
  
 下列範例示範 [Adventure Works] 的查詢如何在包含產品類別目錄資料行和轉售商商務類型資料列的資料表中，取得 [Reseller Sales Amount] 數字。 請注意，在發出下列 SELECT 陳述式時，會提供產品和轉售商的總計：  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 會產生下列結果：  
  
|||||||  
|-|-|-|-|-|-|  
||**All Products**|**Accessories**|**Bikes**|**服裝**|**Components**|  
|**All Resellers**|**$80,450,596.98**|**$571,297.93**|**$66,302,381.56**|**$1,777,840.84**|**$11,799,076.66**|  
|**Specialty Bike Shop**|**$6,756,166.18**|**$65,125.48**|**$6,080,117.73**|**$252,933.91**|**$357,989.07**|  
|**Value Added Reseller**|**$34,967,517.33**|**$175,002.81**|**$30,892,354.33**|**$592,385.71**|**$3,307,774.48**|  
|**Warehouse**|**$38,726,913.48**|**$331,169.64**|**$29,329,909.50**|**$932,521.23**|**$8,133,313.11**|  
  
## <a name="non-visual-on-rows-and-columns"></a>資料行和資料列上的非視覺化  
 若要只針對產品為 Accessories 和 Clothing，且轉售商為 Value Added Reseller 和 Warehouse 的資料產生資料表，但同時保留全部項目的總計，可以使用 NON VISUAL 撰寫如下：  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 會產生下列結果：  
  
|||||  
|-|-|-|-|  
||**All Products**|**Accessories**|**Clothing**|  
|**All Resellers**|**$80,450,596.98**|**$571,297.93**|**$1,777,840.84**|  
|**Value Added Reseller**|**$34,967,517.33**|**$175,002.81**|**$592,385.71**|  
|**Warehouse**|**$38,726,913.48**|**$331,169.64**|**$932,521.23**|  
  
## <a name="non-visual-on-rows"></a>資料列上的非視覺化  
 若要產生可以視覺化總計資料行，但就資料列總計傳回所有 [Category] 的實際總計，應發出下列查詢：  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 請注意如何將 NON VISUAL 只套用到 [Category]。  
  
 上述的查詢會產生下列結果：  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$73,694,430.80|$506,172.45|$1,524,906.93|  
|Value Added Reseller|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 與前一個結果相比，您可以發現 [All Resellers] 資料列現在只總計 [Value Added Reseller] 和 [Warehouse] 的顯示值，但 [All Products] 資料行顯示所有產品 (包括未顯示產品) 的總計值。  
  
## <a name="see-also"></a>請參閱  
 [MDX 的關鍵概念 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [「 自動存在 」](../../../analysis-services/multidimensional-models/mdx/autoexists.md)   
 [使用成員、Tuple 和集合 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [MDX 查詢基礎觀念 &#40;Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [基本 MDX 查詢 &#40;MDX &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)   
 [利用查詢與 Slicer 軸 &#40; 限制查詢MDX &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-restricting-the-query.md)   
 [建立查詢中的 Cube 內容 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)  
  
  
