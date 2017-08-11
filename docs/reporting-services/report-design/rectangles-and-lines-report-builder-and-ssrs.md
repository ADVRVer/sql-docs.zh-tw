---
title: "矩形和線條 （報表產生器及 SSRS） |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bc6c8bc8ddf4e23afe15c533a49a30c96702294c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="rectangles-and-lines-report-builder-and-ssrs"></a>矩形和線條 (報表產生器及 SSRS)
  矩形和線條可在 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 編頁報表內建立視覺效果。 您可以從 [主資料夾] 索引標籤的 [框線] 區段設定這些報表項目的顯示屬性，而且可以在 [屬性] 窗格內設定其他屬性。 您可以將背景色彩或影像、工具提示或書籤等功能加入至矩形。  
  
##  <a name="RectanglesLinesReportParts"></a> 矩形和線條做為報表組件  
 您可以將矩形及其包含的項目當做報表組件，與報表分開發行。 報表組件是指儲存在報表伺服器上的獨立報表項目，而且可以包含在其他報表中。  
  
 您無法發行矩形內的報表項目作為報表組件。 將矩形加入至報表時，會獲得矩形和其中包含的項目。  深入了解 [報表組件](../../reporting-services/report-design/report-parts-report-builder-and-ssrs.md)。  
  
##  <a name="RectangleAsContainer"></a> 使用矩形做為容器  
 您可以使用矩形做為其他項目的容器。 當您移動矩形時，包含在矩形中的項目會跟著它移動。 矩形內部的項目會以其 **Parent** 屬性顯示矩形的名稱。 如需有關使用矩形當做容器的詳細資訊，請參閱[加入矩形或容器 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-design/add-a-rectangle-or-container-report-builder-and-ssrs.md)和[矩陣和圖表 &#40; 顯示相同的資料報表產生器 &#41;](../../reporting-services/report-design/display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).  
  
> [!NOTE]  
>  矩形只是您可以在矩形中建立或拖曳至矩形之項目的容器。 如果您在已經存在設計介面上的項目周圍繪製矩形，該矩形將不會當做其容器。 該矩形不會列在項目的 Parent 屬性中。  
  
 使用矩形來包含報表項目時，請考慮在報表轉譯時，可能對項目造成的整體影響。 包含重複資料列的報表項目 (例如資料表) 會展開，以容納查詢所傳回的資料，而這會影響矩形中之其他項目的定位。 如果項目放在資料區域之下，資料表會將項目往下推。 若要將項目放在固定位置，可以將報表項目放在一個上邊緣位於資料表下邊緣上方的矩形中。 如需詳細資訊，請參閱[轉譯行為 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)。  
  
##  <a name="ReportBorder"></a> 加入報表框線  
 您可以藉由將框線加入頁首、頁尾和報表主體本身來在報表中加入框線，而不必加入線條或矩形。 如需詳細資訊，請參閱 [在報表中加入框線 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-a-border-to-a-report-report-builder-and-ssrs.md)。  
  
##  <a name="HowTo"></a> 如何主題  
 [在報表中加入框線 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-a-border-to-a-report-report-builder-and-ssrs.md)  
  
 [加入矩形或容器 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
 [加入和修改線條 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-and-modify-a-line-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>請參閱＜  
 [加入矩形或容器 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
  
