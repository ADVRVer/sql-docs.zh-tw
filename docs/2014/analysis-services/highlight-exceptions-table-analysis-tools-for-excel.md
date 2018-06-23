---
title: 反白顯示例外狀況 （適用於 Excel 的資料表分析工具） |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 359ca09bdb3e722d44a42bde001eaffc58794ac5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36134860"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a>反白顯示例外狀況 (適用於 Excel 的資料表分析工具)
  ![反白顯示功能區中的例外狀況按鈕](media/tat-highlightex.gif "功能區中的反白顯示例外狀況按鈕")  
  
 資料有時可能包含不尋常的值。 例如，家長的年齡可能會列為五歲。 這些值時，通常稱為*極端值*、 可能是因為資料輸入錯誤，錯誤，或它們可能表示不尋常的趨勢。 不論是哪一個情況，例外狀況都可影響分析的品質。 **反白顯示例外狀況**工具可協助您尋找這些值並加以檢閱來進一步的動作。  
  
 **反白顯示例外狀況**工具可以使用 Excel 資料表中資料的整個範圍，或您可以只選取幾個資料行。 您也可以調整控制資料變化性的臨界值，以尋找更多或更少的例外狀況。  
  
 當此工具完成分析時，它會建立一張新的工作表，其中包含您所分析之每一個資料行中所找到之極端值數目的摘要報表。 此工具也會在原始的資料表中反白顯示例外狀況。 由於此工具會分析整體趨勢，所以它可能會發現資料列中的大多數值為一般值，而只反白顯示該資料列中的一個資料格。 在上面，唯一的家長範例**年齡**資料行可能會反白顯示。  
  
 您也可以變更**例外狀況臨界值**值**摘要報表**。 這個值表示特定資料格包含異常值的機率。 因此，如果您增加其值，反白顯示為極端值的值數目就會減少。 相反地，當您減少這個值時，您將會看到更多反白顯示的資料格。  
  
## <a name="using-the-highlight-exceptions-tool"></a>使用反白顯示例外狀況工具  
  
1.  開啟 Excel 資料表，然後按一下**反白顯示例外狀況**。  
  
2.  指定要分析的資料行。  
  
3.  按一下 **[執行]**。  
  
4.  開啟標題為工作表\<資料表名稱 > 極端值，以檢視找到的極端值摘要。  
  
5.  若要變更反白顯示的數目，請按一下向上和向下箭頭**例外狀況臨界值**列**反白顯示例外狀況報告**。  
  
### <a name="requirements"></a>需求  
 您可以包括未含有錯誤值的資料行，但前提是這些值所包含的資訊可能對於預測其他資料列很有協助。 但是，您應該取消選取有許多遺失值或零值的資料行。  
  
 由於所有選取的資料行都用於建立一般模式，因此，您應該避免使用已知效能低落的輸入資料行，例如下列：  
  
-   包含識別碼之類唯一值的資料行。  
  
-   包含高百分比錯誤值的資料行。  
  
-   包含許多遺漏值的資料行。  
  
     請注意，在某些情況下，包含有許多遺漏值的輸入資料行很有用。 例如，若客戶向零售店購買時，地址欄位的值總是遺漏，資料採礦演算法就可以使用這項資訊來識別其他類似的客戶。 您必須依各個案例來判斷資料是因省略而遺漏，或是由於遺漏的狀態有意義。  
  
-   建立模式時，可能不實用的資料行。 例如，在每個資料列都有相同值的資料行不會加入建立模式時相當實用的資訊。  
  
## <a name="understanding-the-highlight-exceptions-report"></a>了解反白顯示例外狀況報表  
 當您按一下**執行**，此工具會執行三個動作：  
  
-   根據目前在資料表中的資料來建立資料採礦結構。  
  
-   使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群集演算法建立新的資料採礦模型。  
  
-   根據模式來建立預測查詢，以判斷工作表中是否有任何值未必會發生。  
  
 例外狀況臨界值的初始值一定是 75，這表示那裡計算的演算法有 75% 的機率代表反白的資料有誤。 此工具會自動設定這個臨界值，好讓初始分析能夠通過，但是您可以在報表中變更該值。  
  
 **反白顯示例外狀況**工具會反白顯示原始資料的資料表中可疑的資料格。 如果反白顯示的顏色很深，則表示資料列需要您特別留意。 如果反白顯示的顏色很亮，則表示該特定資料格中的值識別為可疑值。 如果您變更例外狀況的臨界值，反白顯示的值也會隨著變更。  
  
 摘要圖表會顯示每一個資料行中在例外狀況臨界值以上的資料格數目。  
  
## <a name="related-tools"></a>相關工具  
 當您在準備資料採礦的過程中要清除或檢閱資料時，您可能也會嘗試適用於 Excel 的資料採礦用戶端中的資料瀏覽功能。 這個增益集提供了更多進階的工具來協助您尋找極端值、重定資料標籤，或是檢視資料的分佈。 適用於 Excel 的資料採礦用戶端的資料瀏覽工具的相關資訊，請參閱[總管和清除資料](exploring-and-cleaning-data.md)。  
  
 **反白顯示例外狀況**工具會使用[!INCLUDE[msCoName](../includes/msconame-md.md)]群集演算法。 群集模型會偵測共用類似特性的資料列群組。 適用於 Excel 的資料採礦用戶端提供**瀏覽**使用圖表和特性設定檔，讓您瀏覽由群集所建立的資料採礦模型的視窗。 如需有關如何瀏覽所建立之群集模型資訊**反白顯示例外狀況**工具，請參閱[瀏覽模型 （資料採礦用戶端 for Excel）](highlight-exceptions-table-analysis-tools-for-excel.md)。  
  
 如需有關 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群集演算法的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 線上叢書》中的＜Microsoft 群集演算法＞主題。  
  
## <a name="see-also"></a>另請參閱  
 [適用於 Excel 的資料表分析工具](table-analysis-tools-for-excel.md)  
  
  