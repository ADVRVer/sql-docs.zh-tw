---
title: 列印報表 (SSRS) | Microsoft Docs
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: 4bad1b6e-7d94-4b17-9502-ccd3dce0fdd9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c3b18a02c29be7221e70f1b4092cd9b212de3133
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56292376"
---
# <a name="print-reports---reporting-services-ssrs"></a>列印報表 - Reporting Services (SSRS)
  將報表儲存至報表伺服器之後，您就可以從入口網站或任何用來檢視所匯出報表的應用程式，檢視及列印報表。 儲存報表之前，您可以在預覽報表時將它列印出來。  
  
 所有列印程序都可以視需要，直接在用戶端電腦上執行。 目前沒有伺服器端列印功能，可讓您從報表伺服器直接將列印工作傳送到連接 Web 伺服器的印表機。 印表機及列印選項是由個別的報表使用者，透過標準 **[列印]** 對話方塊加以選取。  
  
 特別為列印輸出設計報表的作者，可以使用分頁符號、頁首和頁尾、運算式和背景影像，來建立列印專用的報表設計。 供列印輸出使用的報表設計元素的範例，包括要列印在每一份報表背面的條款，或是模擬信頭的圖形和文字元素。  
  
 由於不同轉譯格式實作的分頁方式有所不同，您可能無法使每一份報表的每一種轉譯格式達到最佳列印輸出結果。 下列清單將提供範例：  
  
1.  報表頁面是為了容納不同資料量而設計的。 例如，依據使用者是否以互動方式切換資料列和資料行而定，包括矩陣的報表可能會造成頁面的橫向與縱向成長。 未擴充矩陣的使用者得到的列印結果，將與有擴充矩陣的使用者不同。  
  
2.  您無法在相同的報表中，合併橫向和縱向模式的頁面，也無法建立列印配置來取代在瀏覽器或其他應用程式中轉譯的報表配置或與之並存。  
  
3.  就大部分的匯出報表而言，報表列印輸出會包括報表上顯示的所有內容，如使用者在電腦螢幕上看到的一樣。 系統會保留報表設計介面中的空白。 若要以水平方式加入或移除額外的空白頁面，請變更報表頁面寬度。  
  
> [!NOTE]  
>  如果您使用瀏覽器的 [列印] 命令，則 HTML 報表列印輸出可能只會包含第一頁的內容。 如果您使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用戶端列印功能來列印 HTML 報表，可以獲得較好的結果。 如需詳細資訊，請參閱 [使用列印控制項從瀏覽器列印報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a>本節內容  
 [使用列印控制項從瀏覽器列印報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)  
 描述如何使用用戶端列印功能，從入口網站進行報表的列印。  
  
 [從其他應用程式列印報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/print-reports-from-other-applications-report-builder-and-ssrs.md)  
 描述如何列印已匯出至另一個應用程式的報表。  
  
 [列印報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/print-a-report-report-builder-and-ssrs.md)  
 提供逐步指示，說明如何列印報表、如何控制頁面邊界，以及如何指定強制分頁轉譯器轉譯的報表紙張大小：PDF、影像或列印。  
  
## <a name="see-also"></a>另請參閱  
 [匯出報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [頁首和頁尾 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)   
 [影像 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)   
 [Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)  
  
  
