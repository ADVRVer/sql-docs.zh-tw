---
description: 資料採礦延伸模組 (DMX) 參考
title: " (DMX) 參考的資料採礦延伸模組 |Microsoft Docs"
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6197fc8508e1334e5f8afdcb14aeaf7488890159
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88414084"
---
# <a name="data-mining-extensions-dmx-reference"></a>資料採礦延伸模組 (DMX) 參考
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  資料採礦延伸模組 (DMX) 是一種語言，可讓您用來在中建立和使用資料採礦模型 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。 您可以使用 DMX 建立新資料採礦模型的結構、培訓這些模型，以及瀏覽、管理與預測模型。 DMX 是由資料定義語言 (DDL) 陳述式、資料操作語言 (DML) 陳述式及函數和運算子所組成。  
  
## <a name="microsoft-ole-db-for-data-mining-specification"></a>Microsoft OLE DB for Data Mining 規格  
 中的資料採礦功能 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 是為了符合 [!INCLUDE[msCoName](../includes/msconame-md.md)] 資料採礦規格的 OLE DB 所建立。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]資料採礦規格的 OLE DB 定義下列各項：  
  
-   保存定義資料採礦模型之資訊的結構。  
  
-   建立及處理資料採礦模型的語言。  
  
 規格會將資料採礦的基準定義為資料採礦模型虛擬物件。 資料採礦模型物件會封裝特定採礦模型的所有已知內容。 資料採礦模型物件的結構就像 SQL 資料表，有描述模型的資料行、資料類型與中繼資訊。 這種結構可以讓您使用 DMX 語言 (SQL 的延伸模組) 來建立及處理模型。  
  
 **如需詳細資訊：** [&#40;Analysis Services 資料採礦的採礦結構&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining)  
  
##  <a name="dmx-statements"></a><a name="BKMK_DMXStatements"></a> DMX 語句  
 您可以使用 DMX 陳述式建立、處理、刪除、複製、瀏覽與預測資料採礦模型。 DMX 中有兩種陳述式類型：資料定義陳述式與資料操作陳述式。 您可以使用每一種陳述式執行不同種類的工作。  
  
 下列各區段提供有關使用 DMX 陳述式的詳細資訊：  
  
-   [資料定義語句](#BKMK_DDL)  
  
-   [資料操作陳述式](#BKMK_DML)  
  
-   [查詢基本概念](#BKMK_Queries)  
  
###  <a name="data-definition-statements"></a><a name="BKMK_DDL"></a> 資料定義語句  
 使用 DMX 中的資料定義陳述式建立及定義新的採礦結構與模型，以匯入與匯出採礦模型與採礦結構，以及從資料庫卸除現有的模型。 DMX 中的資料定義陳述式是資料定義語言 (DDL) 的一部份。  
  
 您可以使用 DMX 中的資料定義陳述式執行下列工作：  
  
-   使用 [Create create](../dmx/create-mining-structure-dmx.md) database 語句建立一個採礦結構，並使用 [ALTER database](../dmx/alter-mining-structure-dmx.md) 語句，將採礦模型加入至採礦結構。  
  
-   使用 [create BUILD model](../dmx/create-mining-model-dmx.md) 語句建立空的資料採礦模型物件，同時建立一個採礦模型和相關聯的採礦結構。  
  
-   使用 [export](../dmx/export-dmx.md) 語句，將採礦模型和相關聯的採礦結構匯出到檔案。 使用 [import](../dmx/import-dmx.md) 語句，從 EXPORT 語句所建立的檔案匯入採礦模型和相關聯的採礦結構。  
  
-   使用 [SELECT into](../dmx/select-into-dmx.md) 語句，將現有的採礦模型的結構複製到新模型，並使用相同的資料來定型。  
  
-   使用 [DROP 採礦模型](../dmx/drop-mining-model-dmx.md) 語句，從資料庫中完全移除一個採礦模型。 使用 [DROP 挖掘 structure](../dmx/drop-mining-structure-dmx.md) 語句，從資料庫中完全移除一個採礦結構及其所有相關聯的採礦模型。  
  
 若要深入瞭解您可以使用 DMX 語句執行的資料採礦工作，請參閱 [&#40;DMX&#41; 語句參考中的資料採礦延伸](../dmx/data-mining-extensions-dmx-statements.md)模組。  
  
 [回到 DMX 陳述式](#BKMK_DMXStatements)  
  
###  <a name="data-manipulation-statements"></a><a name="BKMK_DML"></a> 資料動作陳述式  
 使用 DMX 中的資料操作陳述式處理現有的採礦模型、瀏覽模型，以及針對模型建立預測。 DMX 中的資料操作陳述式是資料管理語言 (DML) 的一部份。  
  
 您可以使用 DMX 中的資料操作陳述式執行下列工作：  
  
-   使用 [INSERT INTO](../dmx/insert-into-dmx.md) 語句來定型採礦模型。 這不會將實際的來源資料插入資料採礦模型物件，而是會建立描述演算法建立之採礦模型的摘要。 INSERT INTO 語句的來源查詢會在中描述 [\<source data query>](../dmx/source-data-query.md) 。  
  
-   擴充 SELECT 語句，以流覽模型定型期間所計算並儲存在資料採礦模型中的資訊，例如來源資料的統計資料。 以下是您可以包含的子句，以擴充 SELECT 語句的威力：  
  
    -   [選取 [不同于 &#60;模型 &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
    -   [從 &#60;模型&#62; 選取。DMX&#41;內容 &#40;](../dmx/select-from-model-content-dmx.md)  
  
    -   [從 &#60;模型&#62; 選取。DMX&#41;&#40;案例 ](../dmx/select-from-model-cases-dmx.md)  
  
    -   [從 &#60;模型&#62; 選取。SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
    -   [從 &#60;模型&#62; 選取。DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
-   使用 SELECT 語句的 [預測聯結](../dmx/select-from-model-prediction-join-dmx.md) 子句，建立以現有的採礦模型為基礎的預測。 預測聯結語句的來源查詢會在中描述 [\<source data query>](../dmx/source-data-query.md) 。  
  
-   使用 [DELETE &#40;DMX&#41;](../dmx/delete-dmx.md) 語句，從模型或結構中移除所有定型資料。  
  
 若要深入瞭解您可以使用 DMX 語句執行的資料採礦工作，請參閱 [&#40;DMX&#41; 語句參考中的資料採礦延伸](../dmx/data-mining-extensions-dmx-statements.md)模組。  
  
 [回到 DMX 陳述式](#BKMK_DMXStatements)  
  
###  <a name="dmx-query-fundamentals"></a><a name="BKMK_Queries"></a> DMX 查詢基本概念  
 SELECT 語句是大多數 DMX 查詢的基礎。 根據搭配這些陳述式使用的子句，您可以針對採礦模型瀏覽、複製或預測。 預測查詢會使用一種形式的 SELECT，根據現有的採礦模型來建立預測。 函數會將您瀏覽與查詢採礦模型的能力擴充到資料採礦模型的內建功能之外。  
  
 您可以使用 DMX 函數，取得在培訓模型過程中探索到的資訊，以及計算新資訊。 這些函數可以用於許多用途，包括傳回描述基礎資料或預測精確度的統計資料，以及傳回預測的擴充說明。  
  
 **如需詳細**  **資訊：** [瞭解 Dmx Select 語句](../dmx/understanding-the-dmx-select-statement.md)、 [一般預測函式 &#40;Dmx&#41;](../dmx/general-prediction-functions-dmx.md)、適用 [于 Dmx 預測查詢的結構和使用](../dmx/structure-and-usage-of-dmx-prediction-queries.md)、 [資料採礦延伸模組 &#40;dmx&#41; 函數參考](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
 [回到 DMX 陳述式](#BKMK_DMXStatements)  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組 &#40;DMX&#41; 函數參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 語句參考](../dmx/data-mining-extensions-dmx-statements.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 語法慣例](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 語法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [&#40;DMX&#41;的一般預測函數 ](../dmx/general-prediction-functions-dmx.md)   
 [DMX 預測查詢的結構和使用方式](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 陳述式](../dmx/understanding-the-dmx-select-statement.md)  
  
  
