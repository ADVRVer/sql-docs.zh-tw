---
title: TopSum （DMX） |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 373fe2f1458b30412f4ee5852baa57b930af4878
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68893039"
---
# <a name="topsum-dmx"></a>TopSum (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  以遞減次序的順序，傳回累計總和至少達指定值的最頂部資料表資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
TopSum(<table expression>, <rank expression>, <sum>)  
```  
  
## <a name="applies-to"></a>套用至  
 傳回資料表的運算式，例如\<資料表資料行參考>，或傳回資料表的函數。  
  
## <a name="return-type"></a>傳回類型  
 \<資料表運算式>  
  
## <a name="remarks"></a>備註  
 **TopSum**函數會根據每個資料列的次序運算式> 引數的評估值\<，以遞減的次序順序傳回最頂部的資料列，讓\<次序運算式> 值的總和至少是\<總和> 引數所指定的給定總和。 **TopSum**會在仍符合指定總和值的情況下，傳回可能的最小元素數目。  
  
## <a name="examples"></a>範例  
 下列範例會針對您使用[基本資料採礦教學](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)課程所建立的關聯模型，建立預測查詢。  
  
 若要瞭解 TopPercent 的運作方式，第一次執行只傳回嵌套資料表的預測查詢可能會很有説明。  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  在此範例中，當做輸入提供的值包含單引號，因此必須在該值前面加上另一個單引號來逸出。 如果您不確定插入逸出字元的語法，可以使用預測查詢產生器來建立查詢。 當您從下拉式清單選取值時，就會為您插入所需的逸出字元。 如需詳細資訊，請參閱[在資料採礦設計工具中建立單一查詢](https://docs.microsoft.com/analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer)。  
  
 範例結果︰  
  
|模型|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016|0.252695851|  
|Water Bottle|2866|0.192620472|0.175205052|  
|Patch kit|2113|0.142012232|0.132389356|  
|Mountain Tire Tube|1992|0.133879965|0.125304948|  
|Mountain-200|1755|0.117951475|0.111260823|  
|Road Tire Tube|1588|0.106727603|0.101229538|  
|Cycling Cap|1473|0.098998589|0.094256014|  
|Fender Set - Mountain|1415|0.095100477|0.090718432|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
  
 **TopSum**函數會採用此查詢的結果，並傳回具有最大值加總為指定計數的資料列。  
  
```  
SELECT   
TopSum  
    (  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $PROBABILITY,  
    .5)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 **TopSum**函數的第一個引數是資料表資料行的名稱。 在此範例中，會藉由呼叫 Predict 函數並使用 INCLUDE_STATISTICS 引數來傳回嵌套的資料表。  
  
 **TopSum**函數的第二個引數是用來排序結果的嵌套資料表中的資料行。 在此範例中，INCLUDE_STATISTICS 選項會傳回資料行 $SUPPORT、$PROBABILTY 和 $ADJUSTED PROBABILITY。 此範例會使用 $PROBABILITY 傳回加總為至少 50% 機率的資料列。  
  
 **TopSum**函數的第三個引數會將目標總和指定為雙精度浮點數。 若要取得加總為百分之 50 機率之重要產品的資料列，請輸入 .5。  
  
 範例結果︰  
  
|模型|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.29 .。。|0.25 .。。|  
|Water Bottle|2866|0.19 .。。|0.17 .。。|  
|Patch kit|2113|0.14 .。。|0.13 .。。|  
  
 **注意**此範例僅供說明**TopSum**的使用方式。 根據資料集的大小而定，此查詢可能會花上很長的一段執行時間。  
  
## <a name="see-also"></a>另請參閱  
 [DMX&#41;的函數 &#40;](../dmx/functions-dmx.md)   
 [&#40;DMX&#41;的一般預測函數](../dmx/general-prediction-functions-dmx.md)   
 [DMX&#41;的 TopPercent &#40;](../dmx/toppercent-dmx.md)  
  
  
