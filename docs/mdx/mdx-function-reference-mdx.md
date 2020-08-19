---
description: MDX 函數參考 (MDX)
title: Mdx 函數參考 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4d7590bf0fb76d9443ea9ceaebe2d8e2d00fbf57
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429790"
---
# <a name="mdx-function-reference-mdx"></a>MDX 函數參考 (MDX)


  Analysis Services 提供在多維度運算式中使用函數 (MDX) 語法。 函數可以用於任何有效的 MDX 陳述式，且通常是用於查詢、自訂積存定義以及其他計算。 本節提供 MDX 函數的相關資訊。  
  
 您可以利用下表按照傳回值的類別目錄尋找函數，或者從目錄中按照字母順序排列的名單中選取函數。  
  
## <a name="array-functions"></a>陣列函式  
  
|函式|描述|  
|--------------|-----------------|  
|[SetToArray &#40;MDX&#41;](../mdx/settoarray-mdx.md)|將一個 (含) 以上集合轉換成陣列，以便用在使用者自訂的函數中。|  
  
## <a name="hierarchy-functions"></a>階層函數  
  
|函式|描述|  
|--------------|-----------------|  
|[階層 &#40;MDX&#41;](../mdx/hierarchy-mdx.md)|傳回含有特定成員或層級的階層式架構。|  
|[維度 &#40;MDX&#41;](../mdx/dimension-mdx.md)|傳回含有指定成員、層級或階層式架構的維度。|  
|[維度 &#40;MDX&#41;](../mdx/dimensions-mdx.md)|傳回由數值或字串運算式所指定的階層。|  
  
## <a name="level-functions"></a>層級函數  
  
|函式|描述|  
|--------------|-----------------|  
|[層級 &#40;MDX&#41;](../mdx/level-mdx.md)|傳回成員的層級。|  
|[&#40;MDX&#41;的層級 ](../mdx/levels-mdx.md)|傳回層級，而其在維度或階層中的位置是由數值運算式指定，或者其名稱是由字串運算式指定。|  
  
## <a name="logical-functions"></a>邏輯函數  
  
|函式|描述|  
|--------------|-----------------|  
|[IsAncestor &#40;MDX&#41;](../mdx/isancestor-mdx.md)|傳回指定的成員是否為另一個指定成員的上階。|  
|[IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)|傳回評估的運算式是否為空白資料格值。|  
|[IsGeneration &#40;MDX&#41;](../mdx/isgeneration-mdx.md)|傳回指定的成員是否在指定的生成集內。|  
|[IsLeaf &#40;MDX&#41;](../mdx/isleaf-mdx.md)|傳回指定的成員是否為分葉成員。|  
|[IsSibling &#40;MDX&#41;](../mdx/issibling-mdx.md)|傳回指定的成員是不是與另一個指定成員同層級。|  
  
## <a name="member-functions"></a>成員函數  
  
|函式|描述|  
|--------------|-----------------|  
|[上階 &#40;MDX&#41;](../mdx/ancestor-mdx.md)|傳回某個成員在特定層級或特定距離的上階。|  
|[ClosingPeriod &#40;MDX&#41;](../mdx/closingperiod-mdx.md)|傳回某個成員在特定層級的子系之最後一個同層級 (Sibling)。|  
|[Cousin &#40;MDX&#41;](../mdx/cousin-mdx.md)|傳回在某父成員之下，與指定的子成員具有相同關係位置的子成員。|  
|[CurrentMember &#40;MDX&#41;](../mdx/currentmember-mdx.md)|反覆運算時，傳回指定維度或階層的目前成員。|  
|[DataMember &#40;MDX&#41;](../mdx/datamember-mdx.md)|傳回由系統所產生，與維度某個非分葉成員相關的資料成員。|  
|[DefaultMember &#40;MDX&#41;](../mdx/defaultmember-mdx.md)|傳回維度或階層架構的預設成員。|  
|[FirstChild &#40;MDX&#41;](../mdx/firstchild-mdx.md)|傳回成員的第一個子系。|  
|[FirstSibling &#40;MDX&#41;](../mdx/firstsibling-mdx.md)|傳回成員父系的第一個子系。|  
|[專案 &#40;成員&#41; &#40;MDX&#41;](../mdx/item-member-mdx.md)|傳回一個來自指定 Tuple 的成員。|  
|[&#40;MDX&#41;的延隔時間 ](../mdx/lag-mdx.md)|傳回在成員維度內指定的成員，前面指定幾個位置上的成員。|  
|[LastChild &#40;MDX&#41;](../mdx/lastchild-mdx.md)|傳回指定成員的最後一個子系。|  
|[LastSibling &#40;MDX&#41;](../mdx/lastsibling-mdx.md)|傳回指定成員父系的最後一個子系。|  
|[潛在客戶 &#40;MDX&#41;](../mdx/lead-mdx.md)|傳回在成員維度內指定的成員，後面指定幾個位置上的成員。|  
|[LinkMember &#40;MDX&#41;](../mdx/linkmember-mdx.md)|傳回相當於指定階層架構中的指定成員的成員|  
|[成員 &#40;字串&#41; &#40;MDX&#41;](../mdx/members-string-mdx.md)|傳回由字串運算式指定的成員。|  
|[NextMember &#40;MDX&#41;](../mdx/nextmember-mdx.md)|傳回內含指定成員的層級中下一個成員。|  
|[OpeningPeriod &#40;MDX&#41;](../mdx/openingperiod-mdx.md)|傳回屬於指定層級之下階的第一個同層級成員，可選擇性地指定成員。|  
|[ParallelPeriod &#40;MDX&#41;](../mdx/parallelperiod-mdx.md)|傳回先前跟特定成員在同樣相對位置上的成員。|  
|[父 &#40;MDX&#41;](../mdx/parent-mdx.md)|傳回一個成員的父系。|  
|[PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)|傳回含有指定成員的層級中之前一個成員。|  
|[StrToMember &#40;MDX&#41;](../mdx/strtomember-mdx.md)|傳回 MDX 格式字串所指定的成員。|  
|[UnknownMember &#40;MDX&#41;](../mdx/unknownmember-mdx.md)|傳回與層級或成員相關的未知的成員。|  
|[ValidMeasure &#40;MDX&#41;](../mdx/validmeasure-mdx.md)|強迫將不可使用的維度移到最上層，以傳回虛擬 Cube 中的有效量值。|  
  
## <a name="numeric-functions"></a>數值函數  
  
|函式|描述|  
|--------------|-----------------|  
|[Aggregate &#40;MDX&#41;](../mdx/aggregate-mdx.md)|傳回純量值，此值是藉由彙總量值或指定集合的 Tuple 上選擇性指定的數值運算式而計算出。|  
|[Avg &#40;MDX&#41;](../mdx/avg-mdx.md)|評估指定的集合，傳回量值的平均值或選擇性數值運算式的平均值。|  
|[CalculationCurrentPass &#40;MDX&#41;](../mdx/calculationcurrentpass-mdx.md)|傳回 Cube 目前的計算行程 (給特定的查詢內容)。|  
|[CalculationPassValue &#40;MDX&#41;](../mdx/calculationpassvalue-mdx.md)|評估 Cube 指定的計算行程後，傳回 MDX 運算式的值。|  
|[CoalesceEmpty &#40;MDX&#41;](../mdx/coalesceempty-mdx.md)|將空白資料格值與數字或字串聯合，並傳回聯合的值。|  
|[相互關聯 &#40;MDX&#41;](../mdx/correlation-mdx.md)|傳回在集合上評估的兩個序列的交互關聯係數。|  
|[&#40;維度的計數&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)|傳回 Cube 中的維度數目。|  
|[&#40;階層層級的計數&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)|傳回一個維度或階層中的層級數目。|  
|[Count &#40;集合&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)|傳回集合中的資料格數目。|  
|[計算 &#40;元組&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)|傳回 Tuple 中的維度數目。|  
|[&#40;MDX&#41;的共變數 ](../mdx/covariance-mdx.md)|傳回在採用偏差結果母體公式的集合上評估兩個序列之擴展協方差。|  
|[CovarianceN &#40;MDX&#41;](../mdx/covariancen-mdx.md)|傳回在採用無偏差結果母體公式的集合上評估兩個序列的樣本共變數。|  
|[DistinctCount &#40;MDX&#41;](../mdx/distinctcount-mdx.md)|傳回集合中相異 (Distinct) Tuple、非空白 Turple 的數目。|  
|[IIf &#40;MDX&#41;](../mdx/iif-mdx.md)|傳回由邏輯測試決定的兩個值的其中之一。|  
|[LinRegIntercept &#40;MDX&#41;](../mdx/linregintercept-mdx.md)|計算集合的線性回歸，並傳回迴歸線 y = ax + b 中攔截的值。|  
|[LinRegPoint &#40;MDX&#41;](../mdx/linregpoint-mdx.md)|計算集合的線性回歸，並傳回迴歸線 y = ax + b 中的 *y* 值。|  
|[LinRegR2 &#40;MDX&#41;](../mdx/linregr2-mdx.md)|計算一個集合的線性迴歸，並傳回決定係數 R2。|  
|[LinRegSlope &#40;MDX&#41;](../mdx/linregslope-mdx.md)|計算集合的線性回歸，並傳回迴歸線 y = ax + b 中斜率的值。|  
|[LinRegVariance &#40;MDX&#41;](../mdx/linregvariance-mdx.md)|計算集合的線性回歸，並傳回與迴歸線 y = ax + b 相關聯的變異數。|  
|[LookupCube &#40;MDX&#41;](../mdx/lookupcube-mdx.md)|在相同資料庫中其他指定的 Cube 運算後傳回數值 MDX 運算式的值。|  
|[最大 &#40;MDX&#41;](../mdx/max-mdx.md)|在集合評估後傳回數值運算式的最大值。|  
|[MDX &#40;中位數&#41;](../mdx/median-mdx.md)|在集合評估後傳回數值運算式的中間值。|  
|[最小 &#40;MDX&#41;](../mdx/min-mdx.md)|在集合評估後傳回數值運算式的最小值。|  
|[&#40;MDX&#41;的序數 ](../mdx/ordinal-mdx.md)|傳回與層級有關以零為基準的序號。|  
|[預測 &#40;MDX&#41;](../mdx/predict-mdx.md)|傳回數值運算式在某個資料採擷模型上所評估出的值。|  
|[順位 &#40;MDX&#41;](../mdx/rank-mdx.md)|傳回指定集合中、指定 Tuple 的以一為基底次序。|  
|[RollupChildren &#40;MDX&#41;](../mdx/rollupchildren-mdx.md)|傳回由積存特定成員子成員的值，利用指定的一元 (Unary) 運算子所產生的值。|  
|[Stddev &#40;MDX&#41;](../mdx/stddev-mdx.md)|[Stdev &#40;MDX&#41;](../mdx/stdev-mdx.md)的別名。|  
|[StddevP &#40;MDX&#41;](../mdx/stddevp-mdx.md)|[StdevP &#40;MDX&#41;](../mdx/stdevp-mdx.md)的別名。|  
|[Stdev &#40;MDX&#41;](../mdx/stdev-mdx.md)|使用無偏差結果母體公式，傳回某個數值運算式在某集合上評估的標準差。|  
|[StdevP &#40;MDX&#41;](../mdx/stdevp-mdx.md)|使用偏差結果母體公式，傳回某個數值運算式在某集合上評估的擴展標準差。|  
|[StrToValue &#40;MDX&#41;](../mdx/strtovalue-mdx.md)|傳回 MDX 格式字串所指定的值。|  
|[&#40;MDX&#41;的總和 ](../mdx/sum-mdx.md)|傳回在一個集合上評估的數字運算式加總。|  
|[值 &#40;MDX&#41;](../mdx/value-mdx.md)|傳回一個量值的數值。|  
|[MDX &#40;MDX&#41;](../mdx/var-mdx.md)|傳回某個數值運算式在採用無偏差結果母體公式的集合上所評估出的範例變異數。|  
|[MDX &#40;差異&#41;](../mdx/variance-mdx.md)|[Var &#40;MDX&#41;](../mdx/var-mdx.md)的別名。|  
|[VarianceP &#40;MDX&#41;](../mdx/variancep-mdx.md)|[VarP &#40;MDX&#41;](../mdx/varp-mdx.md)的別名。|  
|[VarP &#40;MDX&#41;](../mdx/varp-mdx.md)|使用偏差結果母體公式，傳回某個數值運算式在某集合上評估出之擴展變異數。|  
  
## <a name="set-functions"></a>集合函數  
  
|函式|描述|  
|--------------|-----------------|  
|[AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)|傳回藉由在指定集合中新增導出成員的方式所產生的集合。|  
|[AllMembers &#40;MDX&#41;](../mdx/allmembers-mdx.md)|傳回一個集合，包含指定維度、階層或層級的所有成員，包括導出成員在內。|  
|[&#40;MDX&#41;的祖系 ](../mdx/ancestors-mdx.md)|傳回指定層級或距離上某個成員的所有上階的集合。|  
|[父 &#40;MDX&#41;](../mdx/ascendants-mdx.md)|傳回指定成員的上階集合，包括該成員本身。|  
|[軸 &#40;MDX&#41;](../mdx/axis-mdx.md)|傳回一個在座標軸中所定義的集合。|  
|[BottomCount &#40;MDX&#41;](../mdx/bottomcount-mdx.md)|以遞增的順序排序集合，並傳回數值最低的指定 Tuple 數。|  
|[BottomPercent &#40;MDX&#41;](../mdx/bottompercent-mdx.md)|以遞增的順序排序集合，並傳回數值最低的 Tuple 集合，此集合的累計總和等於或小於指定的百分比。|  
|[BottomSum &#40;MDX&#41;](../mdx/bottomsum-mdx.md)|以遞增的順序排序集合，並傳回數值最低的 Tuple 集合，此集合的總和等於或小於指定的值。|  
|[Children &#40;MDX&#41;](../mdx/children-mdx.md)|傳回指定成員的子成員。|  
|[MDX&#41;的交叉結合 &#40;](../mdx/crossjoin-mdx.md)|傳回兩個集合的交叉乘積。|  
|[CurrentOrdinal &#40;MDX&#41;](../mdx/currentordinal-mdx.md)|反覆運算時傳回集合中目前的反覆運算編號。|  
|[子代 &#40;MDX&#41;](../mdx/descendants-mdx.md)|傳回特定層集或距離的成員之子系集合，選擇性包括或排除其他層級中的子系。|  
|[Distinct &#40;MDX&#41;](../mdx/distinct-mdx.md)|傳回一個集合，從指定集合中移除重複的 Tuple。|  
|[DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)|向下切入一個集合的成員，直到集合中最低層級下面的一個層級，或者到集合中一個成員的特定層級下面的一個層級。|  
|[DrilldownLevelBottom &#40;MDX&#41;](../mdx/drilldownlevelbottom-mdx.md)|在特定層級中將集合的成員向下切入到下一個層級。|  
|[DrilldownLevelTop &#40;MDX&#41;](../mdx/drilldownleveltop-mdx.md)|在特定層級中將集合的成員向下切入到下一個層級。|  
|[DrilldownMember &#40;MDX&#41;](../mdx/drilldownmember-mdx.md)|向下切入特定集合中出現在第二個特定集合裡的成員。 或者，函數向下鑽研 Tuple 集合。|  
|[DrilldownMemberBottom &#40;MDX&#41;](../mdx/drilldownmemberbottom-mdx.md)|向下切入特定集合中出現在第二個特定集合的成員，所得到的集合成員限制在特定的數目內。 或者，此函數也向下鑽研 Tuple 集合。|  
|[DrilldownMemberTop &#40;MDX&#41;](../mdx/drilldownmembertop-mdx.md)|向下切入特定集合中出現在第二個特定集合的成員，所得到的集合成員限制在特定的數目內。 或者，此函數向下鑽研 Tuple 集合。|  
|[DrillupLevel &#40;MDX&#41;](../mdx/drilluplevel-mdx.md)|向下切入集合內在特定層級底下的成員。|  
|[DrillupMember &#40;MDX&#41;](../mdx/drillupmember-mdx.md)|向上鑽研同時存在於第二個指定集合中的指定集合成員。|  
|[除了 &#40;MDX&#41;](../mdx/except-mdx-function.md)|找出兩集合間的差異，選擇性保留重複部分。|  
|[存在 &#40;MDX&#41;](../mdx/exists-mdx.md)|傳回有一個或多個其他集合的一個或多個 Tuple 存在的一個集合的成員集合。|  
|[&#40;MDX&#41;解壓縮 ](../mdx/extract-mdx.md)|從引出的維度元件傳回一個 Tuple 集合。|  
|[Filter &#40;MDX&#41;](../mdx/filter-mdx.md)|傳回根據搜尋條件篩選指定集合後所得的集合。|  
|[產生 &#40;MDX&#41;](../mdx/generate-mdx.md)|套用一個集合到另一個集合的每個成員，然後以聯集的方式將結果集聯結。 或者，針對集合進行字串運算式評估之後，傳回所產生的串連字串。|  
|[Head &#40;MDX&#41;](../mdx/head-mdx.md)|傳回集合中指定數目的前幾個元素，同時保留重複項。|  
|[Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)|以階層式架構排列集合成員。|  
|[Intersect &#40;MDX&#41;](../mdx/intersect-mdx.md)|傳回兩個輸入集合的交叉部分，選擇性保留重複部分。|  
|[LastPeriods &#40;MDX&#41;](../mdx/lastperiods-mdx.md)|傳回指定成員之前的成員集合 (包含指定成員)。|  
|[成員 &#40;設定&#41; &#40;MDX&#41;](../mdx/members-set-mdx.md)|傳回維度、層級或階層架構中成員的集合。|  
|[Mtd &#40;MDX&#41;](../mdx/mtd-mdx.md)|傳回與指定成員層級相同的同層級成員集合，以第一個同層級成員開始，以指定的成員結束，如同受 Time 維度中的 Year 層級條件約束。|  
|[NameToSet &#40;MDX&#41;](../mdx/nametoset-mdx.md)|傳回集合，其中包含由 MDX 格式字串所指定的成員。|  
|[NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)|以集合的方式傳回兩個以上集合的交叉乘積，排除空的 Tuple 與沒有相關事實資料表資料的 Tuple。|  
|[順序 &#40;MDX&#41;](../mdx/order-mdx.md)|安排指定集合的成員，可以選擇保留或者打破階層架構。|  
|[PeriodsToDate &#40;MDX&#41;](../mdx/periodstodate-mdx.md)|傳回與指定成員層級相同的同層級成員集合，以第一個同層級成員開始，以指定的成員結束，如同受 Time 維度中的指定層級條件約束。|  
|[Qtd &#40;MDX&#41;](../mdx/qtd-mdx.md)|傳回一組與指定成員相同層級的一組同級成員，以第一個同級為開頭，並以指定的成員結束，如同時間維度中的 *季* 層級條件約束。|  
|[&#40;MDX&#41;的同級 ](../mdx/siblings-mdx.md)|傳回成員的同層級 (Sibling)，包括成員本身。|  
|[StripCalculatedMembers &#40;MDX&#41;](../mdx/stripcalculatedmembers-mdx.md)|傳回一個藉由移除指定集合中的導出成員的方式所產生的集合。|  
|[StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md)|傳回 MDX 格式字串所指定的集合。|  
|[子集 &#40;MDX&#41;](../mdx/subset-mdx.md)|從指定集合中傳回 Tuple 的子集。|  
|[Tail &#40;MDX&#41;](../mdx/tail-mdx.md)|從集合末端傳回一個子集合。|  
|[ToggleDrillState &#40;MDX&#41;](../mdx/toggledrillstate-mdx.md)|切換成員的探究狀態。|  
|[TopCount &#40;MDX&#41;](../mdx/topcount-mdx.md)|以遞減的順序排序集合，並傳回數值最高的指定元素數。|  
|[TopPercent &#40;MDX&#41;](../mdx/toppercent-mdx.md)|以遞減的順序排序集合，並傳回數值最高的 Tuple 集合，此集合的累計總和等於或小於指定的百分比。|  
|[TopSum &#40;MDX&#41;](../mdx/topsum-mdx.md)|為集合排序，並傳回頂端數個元素，這些元素的累積總數至少是指定的數值。|  
|[Union &#40;MDX&#41;](../mdx/union-mdx.md)|傳回兩個集合的聯合，選擇性保留重複部分。|  
|[Unorder &#40;MDX&#41;](../mdx/unorder-mdx.md)|移除指定集合中的任何強制排序。|  
|[VisualTotals &#40;MDX&#41;](../mdx/visualtotals-mdx.md)|傳回指定集合中動態加總子成員所產生的集合，您可以選擇是否要在結果集中使用父成員名稱的模式。|  
|[Wtd &#40;MDX&#41;](../mdx/wtd-mdx.md)|傳回與指定成員層級相同的同層級成員集合，以第一個同層級成員開始，以指定的成員結束，如同受 Time 維度中的 Week 層級條件約束。|  
|[Ytd &#40;MDX&#41;](../mdx/ytd-mdx.md)|傳回一組與指定成員相同層級的一組同級成員，從第一個同級開始，並以指定的成員結束，如同時間維度中的 *Year* 層級所限制。|  
  
## <a name="string-functions"></a>字串函式  
  
|函式|描述|  
|--------------|-----------------|  
|[CalculationPassValue &#40;MDX&#41;](../mdx/calculationpassvalue-mdx.md)|在 Cube 指定的計算行程運算後傳回數值 MDX 運算式的值。|  
|[CoalesceEmpty &#40;MDX&#41;](../mdx/coalesceempty-mdx.md)|將空白資料格值與數字或字串聯合，並傳回聯合的值。|  
|[產生 &#40;MDX&#41;](../mdx/generate-mdx.md)|套用一個集合到另一個集合的每個成員，然後以聯集的方式將結果集聯結。 或者，針對集合進行字串運算式評估之後，傳回所產生的串連字串。|  
|[IIf &#40;MDX&#41;](../mdx/iif-mdx.md)|傳回由邏輯測試決定的兩個值的其中之一。|  
|[LookupCube &#40;MDX&#41;](../mdx/lookupcube-mdx.md)|在相同資料庫中其他指定的 Cube 運算後傳回數值 MDX 運算式的值。|  
|[MemberToStr &#40;MDX&#41;](../mdx/membertostr-mdx.md)|傳回對應至指定成員的 MDX 格式字串。|  
|[MDX&#41;名稱 &#40;](../mdx/name-mdx.md)|傳回維度、階層架構、層級或者成員的名稱。|  
|[Properties &#40;MDX&#41;](../mdx/properties-mdx.md)|傳回包含成員屬性值的字串或強型別 (strongly-typed) 值。|  
|[SetToStr &#40;MDX&#41;](../mdx/settostr-mdx.md)|傳回對應至指定成員的 MDX 格式化字串。|  
|[TupleToStr &#40;MDX&#41;](../mdx/tupletostr-mdx.md)|傳回對應至指定之元組的 MDX 格式字串。|  
|[UniqueName &#40;MDX&#41;](../mdx/uniquename-mdx.md)|傳回指定維度、階層、層級或成員的唯一名稱。|  
|[&#40;MDX&#41;的使用者名稱 ](../mdx/username-mdx.md)|傳回目前連接的網域名稱與使用者名稱。|  
  
## <a name="subcube-functions"></a>Subcube 函數  
  
|函式|描述|  
|--------------|-----------------|  
|[此 &#40;MDX&#41;](../mdx/this-mdx.md)|傳回目前的 Subcube。|  
|[離開 &#40;MDX&#41;](../mdx/leaves-mdx.md)|傳回指定維度、成員或 Tuple 的分葉成員集合。|  
  
## <a name="tuple-functions"></a>Tuple 函數  
  
|函式|描述|  
|--------------|-----------------|  
|[目前的 &#40;MDX&#41;](../mdx/current-mdx.md)|反覆運算時從一個集合傳回目前的 Tuple。|  
|[專案 &#40;元組&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md)|從集合傳回一個 Tuple。|  
|[根 &#40;MDX&#41;](../mdx/root-mdx.md)|傳回包含 cube、維度或元組中每個屬性階層之 **所有** 成員的元組。|  
|[StrToTuple &#40;MDX&#41;](../mdx/strtotuple-mdx.md)|傳回 MDX 格式字串所指定的元組。|  
  
## <a name="other-functions"></a>其他函數  
  
|函式|描述|  
|--------------|-----------------|  
|[MDX&#41;&#40;錯誤 ](../mdx/error-mdx.md)|引發錯誤，選擇性提供指定的錯誤訊息。|  
  
## <a name="see-also"></a>另請參閱  
 [MDX 語言參考 &#40;MDX&#41;](../mdx/mdx-language-reference-mdx.md)  
  
  
