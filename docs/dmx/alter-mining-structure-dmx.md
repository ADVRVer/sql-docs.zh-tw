---
title: 改變採礦結構 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 65374ec0499d6dbb549a14af239c03c06dca4062
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52545425"
---
# <a name="alter-mining-structure-dmx"></a>ALTER MINING STRUCTURE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  建立以現有採礦結構為基礎的新採礦模型。  當您使用**ALTER MINING STRUCTURE**陳述式來建立新的採礦模型，結構必須已經存在。 相反地，當您使用陳述式[CREATE MINING MODEL &#40;DMX&#41;](../dmx/create-mining-model-dmx.md)，您建立模型，並自動產生其基礎採礦結構，在相同的時間。  
  
## <a name="syntax"></a>語法  
  
```  
  
ALTER MINING STRUCTURE <structure>  
ADD MINING MODEL <model>  
(  
    <column definition list>  
  [(<nested column definition list>) [WITH FILTER (<nested filter criteria>)]]  
)  
USING <algorithm> [(<parameter list>)]   
[WITH DRILLTHROUGH]  
[,FILTER(<filter criteria>)]  
```  
  
## <a name="arguments"></a>引數  
 *結構*  
 要對其加入採礦模型之採礦結構的名稱。  
  
 *model*  
 採礦模型的唯一名稱。  
  
 *資料行定義清單*  
 資料行定義的逗號分隔清單。  
  
 *巢狀資料行定義清單*  
 取自巢狀資料表之資料行的逗號分隔清單 (如果適用的話)。  
  
 *巢狀的篩選準則*  
 套用至巢狀資料表中資料行的篩選運算式。  
  
 *演算法*  
 提供者所定義的資料採礦演算法名稱。  
  
> [!NOTE]  
>  使用也可以擷取一份目前的提供者所支援的演算法[DMSCHEMA_MINING_SERVICES 資料列集](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)。 若要檢視目前執行個體中支援的演算法[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，請參閱 <<c2> [ 資料採礦屬性](../analysis-services/server-properties/data-mining-properties.md)。  
  
 *參數清單*  
 選擇性。 提供者自訂之演算法參數的逗號分隔清單。  
  
 *篩選準則*  
 套用至案例資料表中之資料行的篩選運算式。  
  
## <a name="remarks"></a>備註  
 如果採礦結構包含複合索引鍵，採礦模型就必須包含結構中定義的所有索引鍵資料行。  
  
 如果模型不需要可預測資料行 (例如使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群集與 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時序群集演算法建立的模型)，您就不必在陳述式中包含資料行定義。 產生之模型中的所有屬性都會當成輸入處理。  
  
 在  **WITH**子句套用至案例資料表中，您可以指定篩選和鑽研選項：  
  
-   新增**篩選**關鍵字和篩選條件。 篩選器會套用到採礦模型中的案例。  
  
-   新增**鑽研**關鍵字來讓採礦模型的使用者從模型結果鑽研至案例資料。 在資料採礦延伸模組 (DMX) 中，只有在建立模型時才能啟用鑽研。  
  
 同時使用案例篩選和鑽研，您可以結合在單一關鍵字**WITH**子句使用下列範例所示的語法：  
  
 `WITH DRILLTHROUGH, FILTER(Gender = 'Male')`  
  
## <a name="column-definition-list"></a>資料行定義清單  
 請藉由指定資料行定義清單 (其中包含每個資料行的下列資訊) 來定義模型的結構：  
  
-   名稱 (強制的)  
  
-   別名 (選擇性)  
  
-   模型旗標  
  
-   預測要求，指出演算法是否該資料行包含可預測的值，由**PREDICT**或是**PREDICT_ONLY**子句  
  
 使用下列資料行定義清單的語法來定義單一資料行：  
  
```  
<structure column name>  [AS <model column name>]  [<modeling flags>]    [<prediction>]  
```  
  
### <a name="column-name-and-alias"></a>資料行名稱和別名  
 在資料行定義清單中使用的資料行名稱，必須是採礦結構中所使用的資料行名稱。 不過，您也可以選擇定義別名來代表採礦模型中的結構資料行。 您也可以為相同的結構資料行建立多個資料行定義，然後為每個資料行副本指派不同的別名及預測使用方式。 根據預設，如果沒有定義別名，就會使用結構資料行名稱。 如需詳細資訊，請參閱 <<c0> [ 模型資料行建立別名](../analysis-services/data-mining/create-an-alias-for-a-model-column.md)。  
  
 對於巢狀的資料表資料行中，指定巢狀資料表的名稱、 資料類型指定為**資料表**，然後提供要包含在模型中，括號括住的巢狀資料行的清單。  
  
 您可以將篩選準則運算式加在巢狀資料表資料行定義之後，以定義套用至巢狀資料表的篩選運算式。  
  
### <a name="modeling-flags"></a>模型旗標  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支援下列用於採礦模型資料行的模型旗標：  
  
> [!NOTE]  
>  NOT_NULL 模型旗標適用於採礦結構資料行。 如需詳細資訊，請參閱 [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md)。  
  
|||  
|-|-|  
|詞彙|定義|  
|**REGRESSOR**|指示演算法可以在迴歸演算法的迴歸公式中使用指定的資料行。|  
|**MODEL_EXISTENCE_ONLY**|指出屬性資料行的值是否比屬性的存在更重要。|  
  
 您可以為一個資料行定義多個模型旗標。 如需如何使用模型旗標的詳細資訊，請參閱[模型旗標&#40;DMX&#41;](../dmx/modeling-flags-dmx.md)。  
  
### <a name="prediction-clause"></a>預測子句  
 預測子句描述如何使用預測資料行。 下表列出可能的子句。  
  
|||  
|-|-|  
|**PREDICT**|這個資料行可以由模型預測，而其值可以用來當做輸入以預測其他可預測資料行的值。|  
|**PREDICT_ONLY**|這個資料行可以依模型預測，但是其值不能用於輸入案例中以預測其他可預測資料行的值。|  
  
## <a name="filter-criteria-expressions"></a>篩選準則運算式  
 您可以定義篩選來限制用於採礦模型中的案例。 篩選可套用至案例資料表中的資料行或巢狀資料表中的資料列，或套用至兩者。  
  
 篩選準則運算式是經過簡化的 DMX 述詞，與 WHERE 子句類似。 篩選運算式限於使用基本數學運算子、純量和資料行名稱的公式。 EXISTS 運算子則是例外；如果子查詢至少傳回一個資料列，該運算子就會評估為 True。 使用常見的邏輯運算子，可以結合述詞：AND、 OR 和 NOT。  
  
 如需有關搭配採礦模型的篩選條件的詳細資訊，請參閱[採礦模型的篩選&#40;Analysis Services-Data Mining&#41;](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)。  
  
> [!NOTE]  
>  篩選中的資料行必須是採礦結構資料行。 您無法在模型資料行或別名資料行上建立篩選。  
  
 如需有關 DMX 運算子和語法的詳細資訊，請參閱 <<c0> [ 採礦模型資料行](../analysis-services/data-mining/mining-model-columns.md)。  
  
## <a name="parameter-definition-list"></a>參數定義清單  
 您可以將演算法參數加入至參數清單，以調整模型的效能和功能。 可以使用的參數是依照您在 USING 子句中指定的演算法而定。 如需每一種演算法相關聯的參數，請參閱[資料採礦演算法&#40;Analysis Services-Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)。  
  
 參數清單的語法如下：  
  
```  
[<parameter> = <value>, <parameter> = <value>,...]  
```  
  
## <a name="example-1-add-a-model-to-a-structure"></a>範例 1：將模型加入結構  
 下列範例會將貝氏機率分類採礦模型來**New Mailing**採礦結構和限制為 50，指出屬性的最大數目。  
  
```  
ALTER MINING STRUCTURE [New Mailing]  
ADD MINING MODEL [Naive Bayes]  
(  
    CustomerKey,   
    Gender,  
    [Number Cars Owned],  
    [Bike Buyer] PREDICT  
)  
USING Microsoft_Naive_Bayes (MAXIMUM_STATES = 50)  
```  
  
## <a name="example-2-add-a-filtered-model-to-a-structure"></a>範例 2：將篩選的模型加入結構  
 下列範例會將採礦模型時， `Naive Bayes Women`，以**New Mailing**採礦結構。 新模型的基本結構與在範例 1 中加入的採礦模型相同；不過這個模型將取自採礦結構的案例限制為年過 50 的女性客戶。  
  
```  
ALTER MINING STRUCTURE [New Mailing]  
ADD MINING MODEL [Naive Bayes Women]  
(  
    CustomerKey,   
    Gender,  
    [Number Cars Owned],  
    [Bike Buyer] PREDICT  
)  
USING Microsoft_Naive_Bayes  
WITH FILTER([Gender] = 'F' AND [Age] >50)  
```  
  
## <a name="example-3-add-a-filtered-model-to-a-structure-with-a-nested-table"></a>範例 3：將篩選的模型加入具有巢狀資料表的結構  
 下列範例將採礦模型加入至購物籃採礦結構的修改版本中。 在範例中使用的採礦結構已經過修改，加入**區域**資料行，其中包含客戶地區的屬性，以及**Income Group**資料行中，將客戶收入分類使用值**高**，**中等**，或**低**。  
  
 此採礦結構也會包含列出客戶已購買之項目清單的巢狀資料表。  
  
 因為採礦結構包含巢狀資料表，所以您可以在案例資料表、巢狀資料表 (或這兩者) 上定義篩選。 此範例結合了案例篩選和巢狀資料列篩選，將案例限制為已購買其中一款公路胎型號的富有歐洲客戶。  
  
```  
ALTER MINING STRUCTURE [Market Basket with Region and Income]  
ADD MINING MODEL [Decision Trees]  
(  
    CustomerKey,   
    Region,  
    [Income Group],  
    [Product] PREDICT (Model)   
WITH FILTER (EXISTS (SELECT * FROM [v Assoc Seq Line Items] WHERE   
 [Model] = 'HL Road Tire' OR  
 [Model] = 'LL Road Tire' OR  
 [Model] = 'ML Road Tire' )  
)  
) WITH FILTER ([Income Group] = 'High' AND [Region] = 'Europe')  
USING Microsoft_Decision Trees  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組&#40;DMX&#41;資料定義陳述式](../dmx/dmx-statements-data-definition.md)   
 [資料採礦延伸模組&#40;DMX&#41;資料操作陳述式](../dmx/dmx-statements-data-manipulation.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
