---
title: "內容類型 (DMX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- Data Mining Extensions [Analysis Services], content types
- content types [DMX]
- DMX [Analysis Services], content types
ms.assetid: ab9dd887-df8d-4878-96b0-635881892573
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 33af21a44066e96223bbfc07e39f4718edf87fc2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="content-types-dmx"></a>內容類型 (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  資料採礦演算法需要資料類型之外的其他資訊才能正確作用，例如內容類型。 內容類型協助演算法決定如何處理資料行中的資料。  
  
 每一種演算法支援特定的內容類型。 例如，[!INCLUDE[msCoName](../includes/msconame-md.md)] 貝氏機率分類演算法不能使用連續資料行。 若要在 [!INCLUDE[msCoName](../includes/msconame-md.md)] 貝氏機率分類模型中使用連續資料行，就必須分隔資料行中的資料。 有些演算法需要特定內容類型才能正確作用。 例如，[!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列演算法需要索引鍵時間資料行，以識別收集資料的一段時間。  
  
 如需完整的說明內容的類型，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]支援，請參閱[內容類型 &#40; 資料採礦 &#41;](../analysis-services/data-mining/content-types-data-mining.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦演算法 &#40;Analysis Services-資料採礦 &#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [資料採礦延伸模組 &#40; DMX &#41;參考](../dmx/data-mining-extensions-dmx-reference.md)   
 [資料採礦延伸模組 &#40; DMX &#41;語法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [資料採礦延伸模組 &#40; DMX &#41;函數參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [資料採礦延伸模組 &#40; DMX &#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [資料採礦延伸模組 &#40; DMX &#41;陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)   
 [資料採礦延伸模組 &#40; DMX &#41;語法慣例](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般預測函數 &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [結構和使用方式的 DMX 預測查詢](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 陳述式](../dmx/understanding-the-dmx-select-statement.md)  
  
  

