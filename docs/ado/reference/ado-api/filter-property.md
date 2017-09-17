---
title: "篩選條件屬性 |Microsoft 文件"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::Filter
helpviewer_keywords:
- Filter property
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6aa8e2349bfd564d0cc72d8d17169c6a5ada5f07
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="filter-property"></a>篩選屬性
指出資料中的篩選[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回**Variant**值，其中可以包含下列其中之一：  
  
-   **準則字串**??? 字串串連的一個或多個個別的子句組成**AND**或**OR**運算子。  
  
-   **陣列的書籤**??? 唯一的書籤的陣列值中的記錄該點**資料錄集**物件。  
  
-   A [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)值。  
  
## <a name="remarks"></a>備註  
 使用**篩選**以選擇性地篩選出記錄中的屬性**資料錄集**物件。 將已篩選**資料錄集**會變成目前的資料指標。 傳回值的其他屬性根據目前**游標**受到影響，例如[AbsolutePosition 屬性 (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)， [AbsolutePage 屬性 (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)， [RecordCount 屬性 (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)，和[PageCount 屬性 (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)。 這是因為設定**篩選**為特定值的屬性會將目前的記錄移至第一筆記錄符合新值。  
  
 在表單中的子句組成準則字串*FieldName 運算子值*(例如， `"LastName = 'Smith'"`)。 您可以藉由串連個別的定序子句建立複合子句**AND** (例如， `"LastName = 'Smith' AND FirstName = 'John'"`) 或**OR** (例如， `"LastName = 'Smith' OR LastName = 'Jones'"`)。 準則字串，請使用下列指導方針：  
  
-   *FieldName*必須是有效的欄位名稱從**資料錄集**。 如果欄位名稱包含空格，必須以方括號括住的名稱。  
  
-   運算子必須是下列其中之一： \<，>， \<=、 > =、 <>、 =、 或**像**。  
  
-   值是與您將會比較欄位值的值 (例如，'smith '距離，#8/24/&#95; 12.345 或 $50.00)。 使用單引號字串和日期的井字號 （#）。 數字，您可以使用小數位數、 貨幣符號和科學記號標記法。 如果運算子**像**，值可以使用萬用字元。 允許只有星號 （*） 和百分比符號 （%） 萬用字元，以及它們必須是字串中的最後一個字元。 值不可以是 null。  
  
> [!NOTE]
>  若要篩選器值中包含單引號 （'），使用兩個單引號來代表其中一個。 例如，若要篩選 O'Malley，準則字串應該是"col1 = 'O' Malley' 」。 若要包含在開頭和結尾的篩選值的單一引號，括住的字串以井字符號 （#）。 例如，若要篩選 '1'，準則字串應該是"col1 = '1' # #"。  
  
-   沒有任何優先順序之間 AND 或。 子句可加以群組括號內。 不過，無法群組子句或聯結，然後再加入群組到另一個子句 and，像這樣：`(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   相反地，您會建構為此篩選器`(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   中**像**子句，您可以在開頭和結尾的模式中使用萬用字元 (例如 LastName 類似 '* mit\*')，或只在模式結尾 (比方說，LastName 類似' Smit\*')。  
  
 篩選條件常數更輕鬆地解決個別記錄的衝突，在批次更新模式，可讓您檢視，例如，只有那些記錄期間受到影響時最後一個[UpdateBatch 方法](../../../ado/reference/ado-api/updatebatch-method.md)方法呼叫。  
  
 設定篩選屬性本身可能會失敗，因為與基礎資料衝突 （例如，某筆記錄已經已刪除另一位使用者）。 在這種情況下，提供者所傳回的警告，[錯誤集合 (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)集合但不停止程式執行。 只有當要求的所有記錄中都有衝突，就會發生執行階段錯誤。 使用[Status 屬性 （ADO 資料錄集）](../../../ado/reference/ado-api/status-property-ado-recordset.md)屬性找出具有衝突的記錄。  
  
 設定**篩選**屬性設為零長度字串 ("") 已使用相同的效果**adFilterNone**常數。  
  
 每當**篩選**設定屬性，則目前的記錄位置將移至第一個記錄中記錄的篩選子集**資料錄集**。 同樣地，當**篩選**清除屬性，移至第一筆記錄的目前記錄的位置**資料錄集**。  
  
 當**資料錄集**根據篩選的欄位，某些變數類型 (例如 sql_variant) 錯誤如果不相符的準則字串中使用的欄位和篩選值的子類型，則將會產生 （DISP_E_TYPEMISMATCH 或 80020005）。 例如，如果**資料錄集**物件 (rs) 包含 sql_variant 類型的資料行 (C)，而此資料行的欄位被指派 1 I4 型別，設定 rs 的準則字串值。篩選 ="C = 'A' 」 的欄位就會在執行階段產生錯誤。 不過，rs。篩選 ="C = 2"套用在同一個欄位不會產生任何錯誤，雖然欄位將會篩選出目前的記錄組。  
  
 請參閱[書籤屬性 (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)如需說明，您可以從中建立要用於篩選屬性的陣列的書籤值的屬性。  
  
 只會篩選條件字串的形式 (例如 OrderDate > ' 12/31/1999年 ') 會影響保存的內容**資料錄集**。 篩選建立陣列的書籤，或使用 FilterGroupEnum 中的值不會影響保存的內容**資料錄集**。 這些規則套用至資料錄集與用戶端或伺服器端資料指標建立。  
  
> [!NOTE]
>  當您套用 adFilterPendingRecords 旗標來篩選和修改**資料錄集**在批次更新模式中，產生**資料錄集**如果篩選為基礎的索引鍵的欄位是空的建立單一索引鍵的資料表和修改已根據索引鍵欄位的值。 產生**資料錄集**會為非空白如果下列其中一項條件成立：  
  
-   以建立單一索引鍵資料表中的非索引鍵欄位為基礎的篩選。  
  
-   以建立多個索引鍵資料表中的任何欄位為基礎的篩選。  
  
-   建立單一索引鍵資料表中的非索引鍵欄位上進行修改。  
  
-   建立多個索引鍵資料表中的任何欄位上進行修改。  
  
 下表摘要說明的效果**adFilterPendingRecords**以不同的篩選和修改的組合。 左欄則顯示可能的修改。上的任何非索引鍵欄位，在建立單一索引鍵資料表中，索引鍵欄位上或任何為多個索引鍵資料表中的索引鍵欄位，就可以進行修改。 頂端列會顯示篩選準則。篩選可以根據任何非索引鍵欄位中，建立單一索引鍵的資料表，或任何為多個索引鍵資料表中的索引鍵欄位中的索引鍵欄位。 交集的資料格顯示的結果: + 表示該套用**adFilterPendingRecords**導致非空白**資料錄集**;-表示空**資料錄集**。  
  
||非索引鍵|單一索引鍵|多個索引鍵|  
|-|--------------|----------------|-------------------|  
|**非索引鍵**|+|+|+|  
|**單一索引鍵**|+|-|不適用|  
|**多個索引鍵**|+|不適用|+|  
  
## <a name="applies-to"></a>適用於  
 [資料錄集物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [篩選器和 RecordCount 屬性範例 (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
 [篩選器和 RecordCount 屬性範例 （VC + +）](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
 [Clear 方法 (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [最佳化屬性動態 (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)

