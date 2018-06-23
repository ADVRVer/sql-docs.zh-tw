---
title: 資料採礦程式設計 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1ad8f0d8e066fde6f199af26c977b5a9ba3d8917
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313286"
---
# <a name="data-mining-programming"></a>資料採礦程式設計
  如果您發現 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的內建工具和檢視器不符合需求，就可以透過編碼自己的延伸模組，擴充 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的功能。 在這種方法中，您有兩種選擇：  
  
-   **XMLA**  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 支援 XML for Analysis (XMLA) 當做與用戶端應用程式通訊的通訊協定。 擴充 XML for Analysis 規格的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 可支援其他命令。  
  
     因為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會將 XMLA 用於資料定義、資料操作和資料控制支援，所以您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 提供的視覺化工具來建立採礦結構和採礦模型，然後擴充您之前使用資料採礦延伸模組 (DMX) 和 Analysis Services 指令碼語言 (ASSL) 指令碼所建立的資料採礦物件。  
  
     您可以完整地在 XMLA 指令碼中建立及修改資料採礦物件，並從您自己的應用程式以程式設計方式針對模型執行預測查詢。  
  
-   **分析管理物件 (AMO)**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 也提供了一個完整架構，可讓協力廠商資料採礦提供者將下列資料採礦物件整合至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。  
  
     您可以藉由使用 AMO 來建立採礦結構和採礦模型。 請參閱 CodePlex 中的以下範例：  
  
    -   AMO 瀏覽器  
  
         連接到您所指定的 SSAS 執行個體，並列出所有伺服器物件及其屬性，包括採礦結構和採礦模型。  
  
    -   AMO Simple 範例  
  
         AS Simple 範例涵蓋了大部分主要物件的程式設計存取方式，而且會示範中繼資料瀏覽以及存取物件中的值。  
  
         此範例也會示範如何建立和處理資料採礦結構和模型，以及瀏覽現有的資料採礦模型。  
  
-   **DMX**  
  
     您可以使用 DMX 來封裝命令陳述式、預測查詢和中繼資料查詢，並以表格格式傳回結果，前提是您已經建立與 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器的連接。  
  
## <a name="in-this-section"></a>本節內容  
 [資料採礦的 OLE DB](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 描述此規格的添加來支援資料採礦和多維度資料：新的結構描述資料列集和資料行、用來建立和管理採礦結構的資料採礦延伸模組 (DMX) 語言。  
  
## <a name="related-reference"></a>相關的參考資料  
 [使用 ADOMD.NET 來開發](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 介紹 ADOMD.NET 用戶端和伺服器程式設計物件。  
  
 [使用分析管理物件開發&#40;AMO&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
 介紹 AMO 程式設計程式庫。  
  
 [使用 Analysis Services 開發的指令碼語言&#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 介紹 XML for Analysis (XMLA) 和它的延伸模組。  
  
## <a name="see-also"></a>另請參閱  
 [開發人員手冊 》 &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md)   
 [資料採礦延伸模組&#40;DMX&#41;參考](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
