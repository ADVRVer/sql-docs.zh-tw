---
title: 設定報表或文字方塊的地區設定 (Reporting Services) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- locales [Reporting Services]
ms.assetid: df115b01-184b-47f0-b5ec-0ad965ff9bee
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c5f31ffe9fc3158cf0c6b1c6ef8a9ba813417e76
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65576766"
---
# <a name="set-the-locale-for-a-report-or-text-box-reporting-services"></a>設定報表或文字方塊的地區設定 (Reporting Services)
  報表或文字方塊上的 **[Language]** 屬性包含地區設定，地區設定會決定用來顯示依語言和地區而不同之報表資料的預設格式，例如日期、貨幣或數值。 文字方塊上的 **[Language]** 屬性會覆寫報表上的 **[Language]** 屬性。 如果 **[Language]** 未指定任何值，Reporting Services 會針對發行的報表使用報表伺服器上作業系統的地區設定，或是針對報表預覽使用報表撰寫電腦的地區設定。  
  
 如果是 HTML 報表，您可以覆寫預設的 **Language** 值，並使用瀏覽器用戶端之 HTTP 標頭所指定的語言，其方式是在報表或文字方塊之 **Language** 屬性的運算式內使用內建的 User!Language 欄位。  
  
 您也可以在 URL 中指定報表的 **[Language]** 屬性。 如需詳細資訊，請參閱 [設定 URL 中報表參數的語言言](../../reporting-services/set-the-language-for-report-parameters-in-a-url.md)。  
  
### <a name="to-set-the-locale-for-a-report"></a>若要設定報表的地區設定  
  
1.  在 [設計] 檢視中，按一下報表設計介面的外面來選取報表。  
  
2.  在 [屬性] 窗格中，針對 **[Language]** 屬性輸入或選取您要用於報表的語言。  
  
### <a name="to-set-the-locale-for-a-text-box"></a>若要設定文字方塊的地區設定  
  
1.  在 [設計] 檢視中，選取要套用地區設定的文字方塊。  
  
2.  在 [屬性] 窗格中執行下列動作：  
  
    -   針對 **[Calendar]** 屬性，請輸入或選取用於日期的日曆。  
  
    -   針對 **[Direction]** 屬性，輸入或選取文字的書寫方向。  
  
    -   針對 **[Language]** 屬性，請輸入或選取要用於文字方塊的語言。 這個值會覆寫報表的 **[Language]** 屬性。  
  
    -   針對 **[NumeralLanguage]** 屬性，請輸入或選取文字方塊中所使用的數字格式。  
  
    -   針對 **[NumeralVariant]** 屬性，輸入或選取文字方塊中所使用之數字格式的變數。  
  
    -   針對 **[UnicodeBiDi]** 屬性，選取文字方塊中所使用之雙向內嵌的層級。  
  
## <a name="see-also"></a>另請參閱  
 [報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [適用於多語言或全域部署的解決方案設計考量 (Reporting Services)](https://msdn.microsoft.com/55630eca-d1e5-4ac6-93c7-9a3f15c0d08a)  
  
  
