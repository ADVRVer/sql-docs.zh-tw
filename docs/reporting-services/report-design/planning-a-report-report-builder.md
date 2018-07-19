---
title: 規劃報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- getting started
- report design
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
caps.latest.revision: 19
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84f5898fcc0bf443440a6dcfd3bc88551534e8a5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "33025115"
---
# <a name="planning-a-report-report-builder"></a>規劃報表 (報表產生器)
  報表產生器可讓您建立許多種類的分頁報表。 例如，您可以建立顯示摘要或詳細銷售資料、行銷和銷售趨勢、營運報表或儀表板的報表。 您也可以建立利用豐富文字格式 (例如銷售訂單、產品目錄或正式書信) 的報表。 所有這些報表都是使用報表產生器中相同基本建置組塊的不同組合而建立。 若要建立有用且易於了解的報表，先進行規劃是有效的方法。 以下是開始作業前可能要考量的部分事項：  
  
-   **要以何種格式顯示報表？**  
  
     您可以在線上以瀏覽器 (例如 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web 入口網站) 轉譯報表，或將報表匯出為 Excel、Word 或 PDF 之類的其他格式。 報表所採用的最終格式是一項重要的考量，因為並非所有匯出格式都可以提供所有功能。 如需詳細資訊，請參閱 [匯出報表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)中之分頁的規則。  
  
-   **要使用什麼結構來展示報表中的資料？**  
  
     您可以選擇表格式、矩陣 (類似交叉分析或樞紐分析表報表)、圖表、自由形式結構，或上述任何組合來展示資料。 如需詳細資訊，請參閱[資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md) 和[圖表 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)。  
  
-   **要報表呈現什麼外觀？**  
  
     報表產生器提供許多報表項目，可加入報表使其更易於讀取、反白顯示主要資訊、協助您的對象導覽報表等等。 知道報表將以何種方式呈現，有助於判斷您是否需要文字方塊、矩形、影像和線條等報表項目。 您可能也想要顯示或隱藏項目、加入文件引導模式、包含鑽研報表或子報表，或連結到其他報表。 如需詳細資訊，請參閱[影像、文字方塊、矩形和線條 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/images-text-boxes-rectangles-and-lines-report-builder-and-ssrs.md) 和[互動式排序、文件引導模式及連結 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)。  
  
-   **要讀者看到什麼資料？應該要為不同的對象篩選資料或格式嗎？**  
  
     您可以將報表的範圍縮小為特定的使用者或地點，或限制為特定的時間週期。 若要篩選報表資料，請使用參數僅擷取及顯示所要的資料。 如需詳細資訊，請參閱 MSDN 上的 [報表參數 &#40;報表產生器和報表設計師&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)類型之報表資料來源為基礎的資料集。  
  
-   **需要建立自己的計算嗎？**  
  
     有時候，您的資料來源和資料集並不包含完全符合報表需求的欄位。 在這種情況下，您可能需要建立自己的導出欄位。 例如，您可以將單價乘以數量以取得明細項目銷售量。 您也可使用運算式來提供條件式格式化和其他進階功能。 如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)。  
  
-   **一開始要隱藏報表項目嗎？**  
  
     請考慮是否要在初次執行報表時隱藏報表項目，包括資料區、群組和資料行。 例如，可以一開始先展示摘要資料表，然後再向下鑽研到詳細資料。 如需詳細資訊，請參閱[向下鑽研動作 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/drilldown-action-report-builder-and-ssrs.md)。  
  
-   **要以何種方式傳遞報表？**  
  
     您可以將報表儲存至本機電腦，繼續在本機使用或執行，以滿足您自己的資訊需求。 不過，若要與他人共用報表，您需要將報表儲存至以原生模式設定的報表伺服器，或是 SharePoint 整合模式下的報表伺服器。 如果將報表儲存到伺服器，其他人就可以在需要時隨時執行該報表。 或者，報表伺服器管理員可以設定報表的訂閱，或設定以電子郵件將報表傳遞給其他個人。 如果想要，可以用特定的匯出格式傳遞報表。 如需詳細資訊，請參閱 [尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 2016 的報表產生器](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [報表撰寫概念 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/report-authoring-concepts-report-builder-and-ssrs.md)   
 [報表產生器教學課程](../../reporting-services/report-builder-tutorials.md)  
  
  
