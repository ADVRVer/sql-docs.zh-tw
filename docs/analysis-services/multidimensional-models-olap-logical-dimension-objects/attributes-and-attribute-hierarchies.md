---
title: 屬性和屬性階層 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b858af0f4f3e86e480099a16e2b8db607b8882c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62679440"
---
# <a name="attributes-and-attribute-hierarchies"></a>屬性和屬性階層
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  維度是屬性的集合，這些屬性會繫結至資料來源檢視中資料表或檢視內的一或多個資料行。  
  
## <a name="key-attribute"></a>索引鍵屬性  
 每一個維度都有包含索引鍵屬性， 每個屬性會繫結至維度資料表中的一或多個資料行。 索引鍵屬性是維度中的一個屬性，它會識別維度主資料表中，用於外部索引鍵與事實資料表之關聯性的資料行。 通常，索引鍵屬性會代表維度資料表中的主索引鍵資料行。 您可以在資料來源檢視中的資料表上定義邏輯主索引鍵，只要其基礎資料來源中沒有實體主索引鍵。 **如需詳細資訊**，請參閱 <<c2> [ 定義邏輯主索引鍵的資料來源檢視中&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-logical-primary-keys-in-a-data-source-view-analysis-services.md)。</c2> 定義索引鍵屬性時，Cube 精靈和維度精靈會嘗試使用資料來源檢視中，維度資料表的主索引資料行。 如果維度資料表沒有定義邏輯主索引鍵或實體主索引鍵，精靈就無法正確地定義維度的索引鍵屬性。  
  
## <a name="binding-an-attribute-to-columns-in-data-source-view-tables-or-views"></a>將屬性繫結到資料來源檢視資料表或檢視中的資料行  
 屬性會繫結到一或多個資料來源檢視資料表或檢視中的資料行， 屬性一定會繫結到一或多個索引鍵資料行，這些索引鍵資料行會決定該屬性所包含的成員。 依預設，這會是屬性所繫結到的唯一資料行。 屬性也可以針對特定用途而繫結到一或多個其他資料行。 例如，屬性的**NameColumn**屬性決定向使用者顯示每個屬性成員的名稱-這個屬性的屬性可以繫結至特定維度資料行透過資料來源檢視，或可以是繫結至資料來源檢視中的導出資料行。 如需詳細資訊，請參閱 < [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)。  
  
## <a name="attribute-hierarchies"></a>屬性階層  
 依預設，屬性成員會組織成兩個層級階層，由分葉層級和「全部」層級所組成。 「全部」層級在跨每一個量值群組的量值中，包含此屬性成員的彙總值，與該屬性相關之量值群組的維度就是成員。 不過，如果**IsAggregatable**屬性設定為 False，則不會建立所有的層級。 如需詳細資訊，請參閱 < [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)。  
  
 屬性可以且通常也會排列為使用者自訂階層，提供向下鑽研路徑，讓使用者瀏覽與屬性相關之量值群組中的資料。 在用戶端應用程式中，屬性可用來提供群組和條件約束資訊。 當屬性排列為使用者定義階層時，您會定義當層級發生在多對一關聯的階層層級之間的關聯性或一對一關聯性 (稱為*自然*關聯性)。 例如，在日曆時間階層中，日層級應該與月份層級有關，而月份層級應該與季層級有關，依此類推。 定義使用者自訂階層中層級之間的關聯性會讓 Analysis Services 定義更多有用的彙總，以提升查詢效能，同時也可以在處理效能期間節省記憶體，對大型或複雜的 Cube 來說非常重要。 如需詳細資訊，請參閱 <<c0> [ 使用者階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)，[建立使用者定義階層](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)，並[定義屬性關聯性](../../analysis-services/multidimensional-models/attribute-relationships-define.md)。  
  
## <a name="attribute-relationships-star-schemas-and-snowflake-schemas"></a>屬性關聯性、星狀結構描述和雪花式結構描述  
 依預設，星狀結構描述中的所有屬性都與索引鍵屬性直接相關，如此可讓使用者根據維度中的任何屬性階層在 Cube 中瀏覽事實。 在雪花式結構描述中，如果其基礎資料表直接連結到事實資料表，則屬性就會直接連結到索引鍵屬性；否則會透過繫結到基礎資料表內索引鍵的屬性間接進行連結，將雪花資料表連結到直接連結的資料表。  
  
## <a name="see-also"></a>另請參閱  
 [建立使用者定義階層](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)   
 [定義屬性關聯性](../../analysis-services/multidimensional-models/attribute-relationships-define.md)   
 [維度屬性內容參考](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
