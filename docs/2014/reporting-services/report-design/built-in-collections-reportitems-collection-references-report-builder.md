---
title: ReportItems 集合參考 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: edc0c75f-0530-4e6d-85aa-3385301bfd00
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 4c72d35c92cabae9f9b1f73daa8c665c1b19771b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053888"
---
# <a name="reportitems-collection-references-report-builder-and-ssrs"></a>ReportItems 集合參考 (報表產生器及 SSRS)
  `ReportItems` 內建集合是報表項目的文字方塊集合，例如，報表設計介面上的資料區或文字方塊列。 `ReportItems`集合包含的頁首、 頁尾或報表主體目前範圍中的文字方塊。 這個集合是在執行階段由報表處理器和報表轉譯器而決定。 隨著報表處理器連續地將報表資料和報表項目配置元素結合為報表的使用者檢視頁面，目前的範圍也會變更。 您可以使用`ReportItems`內建集合來產生字典樣式頁首，每個頁面上顯示的第一個和最後一個項目。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-reportitems-value-property"></a>使用 ReportItems 值屬性  
 內的項目`ReportItems`集合有只有一個屬性： 值。 `ReportItems` 項目的值可用來顯示或計算報表中其他欄位的資料。 若要存取目前文字方塊的值，您可以使用 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 內建全域 Me.Value，或是只使用 Value。 在報表函數 (例如，First 和彙總函式) 中，請使用完整的語法。  
  
 例如：  
  
-   這個置於文字方塊中的運算式會顯示名為 `Textbox1` 的 `ReportItem` 文字方塊的值：  
  
     `=ReportItems!Textbox1.Value`  
  
-   此運算式中，置於`ReportItem`文字方塊 Color 屬性，會顯示為黑色文字的值時 > 0; 否則值會以紅色顯示：  
  
     `=IIF(Me.Value > 0,"Black","Red")`  
  
-   這個放在頁首或頁尾之文字方塊中的運算式，會為名為 `LastName`的文字方塊顯示已轉譯報表之每一頁的第一個值：  
  
     `=First(ReportItems("LastName").Value)`  
  
## <a name="dictionary-style-page-header-expressions"></a>字典樣式頁首運算式  
 您可以建立頁首來顯示頁面上的第一個客戶，以及頁面上的最後一個客戶。 因為頁首中的文字方塊在運算式中只能參考 `ReportItems` 內建集合一次，所以您需要將兩個文字方塊加入到頁首：一個是第一個客戶的名稱 (`=First(ReportItems!textboxLastName.Value`)，另一個則是最後一個客戶的名稱 (`=Last(ReportItems!textboxLastName.Value`)。  
  
 在頁首或頁尾區段中，只有目前頁面上的文字方塊才能做為 `ReportItems` 集合的成員。 例如，如果 `ReportItems!textboxLastName.Value` 參考的文字方塊只會顯示在多頁面資料區域的第一個頁面上，則您會看到第一頁的值，但所有其他的頁面都會顯示 **#Error** ，表示運算式無法評估為已寫入。  
  
## <a name="scope-for-the-reportitems-collection"></a>ReportItems 集合的範圍  
 在系統處理報表時，每個報表主體或資料區域中的文字方塊都會在其資料集、資料區域和群組關聯的內容中進行評估。 如需參考範圍`ReportItems`集合是目前的範圍或高於目前範圍的任何時間點。  
  
 例如，在父群組的資料列內的文字方塊所包含的運算式，不得參考子群組資料列中的文字方塊的名稱。 此類運算式不會解析為報表中的值，因為子資料列文字方塊超出範圍。 如需詳細資訊，請參閱 [彙總函式參考 &#40;報表產生器和 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Built-in Collections in Expressions&#40;報表產生器及 SSRS&#41;](built-in-collections-in-expressions-report-builder.md)   
 [運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [篩選、 分組和排序資料&#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
