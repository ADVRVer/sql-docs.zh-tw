---
title: "使用者自訂成員屬性 (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: eaeb79931b4c9c57088ada093148047a26b614d2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-member-properties---user-defined-member-properties"></a>MDX 成員屬性使用者自訂成員屬性
  使用者自訂成員屬性可以做為屬性關聯性，增加到維度中的特定具名層級。 階層的 **(All)** 層級或階層本身無法加入使用者定義成員屬性。  
  
## <a name="creating-user-defined-member-properties"></a>建立使用者自訂成員屬性  
 您可以透過使用者介面或以程式設計的方式，將使用者自訂成員屬性增加到伺服器維度或 Cube：  
  
-   若要透過使用者介面加入使用者定義成員屬性，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中的維度設計師。 如需詳細資訊，請參閱 [定義屬性關聯性](../../../analysis-services/multidimensional-models/attribute-relationships-define.md)。  
  
-   若要以程式設計方式加入使用者定義的成員屬性，您的應用程式可以使用分析管理物件 (AMO)，或 XML for Analysis (XMLA) 及 Analysis Services 指令碼語言 (ASSL) 的組合。 如需詳細資訊，請參閱 [屬性關聯性](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。  
  
## <a name="retrieving-user-defined-member-properties"></a>擷取使用者自訂成員屬性  
 您可以使用 **PROPERTIES** 關鍵字或 [Properties](../../../mdx/properties-mdx.md) 函數，擷取使用者定義成員屬性。  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>使用 PROPERTIES 關鍵字擷取使用者自訂成員屬性  
 擷取使用者自訂成員屬性的語法，跟用以擷取內建層級成員屬性的語法類似，如以下語法所示：  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 **PROPERTIES** 關鍵字會在座標軸規格的集合運算式後面出現。 例如，以下的 MDX 查詢使用 **PROPERTIES** 關鍵字來擷取 `List Price` 與 `Dealer Price` 使用者定義成員屬性，並且在識別 1 月份銷售之產品的集合運算式之後顯示：  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a>使用 Properties 函數擷取使用者自訂成員屬性  
 或者，您可以使用 **Properties** 函數來存取自訂成員屬性。 例如，以下的 MDX 查詢使用 **WITH** 關鍵字來建立包含 `List Price` 成員屬性的導出成員：  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 如需建立導出成員的詳細資訊，請參閱[在 MDX 中建立導出成員 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [使用成員屬性 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [屬性 &#40;MDX &#41;](../../../mdx/properties-mdx.md)  
  
  
