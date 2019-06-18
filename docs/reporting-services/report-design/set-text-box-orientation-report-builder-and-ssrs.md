---
title: 設定文字方塊方向 (報表產生器及 SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 119e9f04ddbaf91da420d69343d7fe741fbdd63d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65576842"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>設定文字方塊方向 (報表產生器及 SSRS)
在 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 分頁報表中，您可以將文字方塊旋轉到不同方向︰   
* 水平   
* 垂直 (旋轉 90 度，從上往下讀取文字)  
* 旋轉 270 度 (從下往上讀取文字)。   
  
因為旋轉的是文字方塊不是文字，所以旋轉會套用到文字方塊中的所有文字。 您不能指定部分文字有不同的方向。 手動調整資料行寬度及資料列高度，以配合旋轉的文字大小。  
  
 用來指定文字方向的 WritingMode 屬性無法在 [文字方塊屬性]  對話方塊中使用。 其位在 [屬性] 窗格中，並在該處設定屬性。   
  
## <a name="to-rotate-text"></a>旋轉文字  
  
1.  建立報表或開啟現有的報表，並 [將文字方塊加入](../../reporting-services/report-design/add-move-or-delete-a-text-box-report-builder-and-ssrs.md) 設計介面。  
  
3.  選取您要旋轉的文字方塊。  
  
2.  如果 [屬性] 窗格並未開啟，請選取 [檢視]  索引標籤上的 [屬性]  核取方塊。  
  
4.  在 [屬性] 窗格中尋找 WritingMode 屬性，並選取要套用到文字方塊的文字方向。  
  
    > [!NOTE]  
    >  當 [屬性] 窗格中的屬性組織成類別目錄時，WritingMode 會位於 [當地語系化]  類別目錄中。  
  
5.  在清單方塊中，選取 **[Horizontal]** 、 **[Vertical]** 或 **[Rotate270]** 。  
  
## <a name="see-also"></a>另請參閱  
 [文字方塊 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [教學課程：格式化文字 &#40;報表產生器&#41;](../../reporting-services/tutorial-format-text-report-builder.md)  
  
  
