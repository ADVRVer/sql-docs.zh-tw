---
title: "將框線加入至報表 （報表產生器及 SSRS） |Microsoft 文件"
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
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 824ca565b87a77add1c547aafb264345a9a63dab
ms.contentlocale: zh-tw
ms.lasthandoff: 06/13/2017

---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a>在報表中加入框線 (報表產生器及 SSRS)
  您可以藉由將框線加入頁首、頁尾和報表主體本身來在 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 分頁報表中加入框線，而不必加入線條或矩形。    
    
 如果加入了出現在頁首和頁尾的報表框線，不要抑制報表第一頁和最後一頁的頁首及頁尾。 如果抑制顯示，則報表第一頁和最後一頁之上方或下方的框線將被切斷。 如需詳細資訊，請參閱[頁首和頁尾 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)。    
    
## <a name="to-add-a-border-to-a-report"></a>在報表中加入框線    
    
1.  在頁首內以滑鼠右鍵按一下任何項目的外部，然後按一下 [頁首屬性]。 以您所要的樣式，在 **[框線]** 索引標籤上加入左框線、上框線和右框線。    
    
    > [!NOTE]    
    >  如果您不要在報表中使用頁首，可以將框線放在報表主體的周圍，或是從 [插入] 索引標籤加入頁首。    
    
2.  在設計介面上以滑鼠右鍵按一下主體內任何項目的外部，然後按一下 [主體屬性]。 以您所要的樣式，在 **[框線]** 索引標籤上加入左框線和右框線。    
    
3.  在頁尾內以滑鼠右鍵按一下任何項目的外部，然後按一下 [頁尾屬性]。 以您所要的樣式，在 **[框線]** 索引標籤上加入左框線、下框線和右框線。    
    
## <a name="see-also"></a>請參閱＜    
 [矩形和線條 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/rectangles-and-lines-report-builder-and-ssrs.md)    
    
  
