---
title: 顯示頁碼或其他報表屬性 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 77e87dc08897954cb210b9e785dc4d6e266a3ea3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36134870"
---
# <a name="display-page-numbers-or-other-report-properties-report-builder-and-ssrs"></a>顯示頁碼或其他報表屬性 (報表產生器及 SSRS)
  您可以輕鬆地將頁碼、報表標題、檔案名稱和其他報表屬性加入至報表的頁首或頁尾。 在 [報表資料] 窗格的 [內建欄位] 資料夾中，這些屬性會儲存成欄位：  
  
-   執行時間  
  
-   頁碼  
  
-   報表資料夾  
  
-   報表名稱  
  
-   報表伺服器 URL  
  
-   總頁數  
  
-   使用者識別碼  
  
-   語言  
  
 您可能會想要針對頁碼，在數字前面加入 "Page" 一詞。 您可能也會想要顯示總頁數。  
  
> [!NOTE]  
>  將總頁數加入至頁尾可能會在您執行或預覽報表時降低效能。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-number-or-other-report-properties"></a>若要加入頁碼或其他報表屬性  
  
1.  在 [報表資料] 窗格中，展開 [內建欄位] 資料夾。  
  
    > [!NOTE]  
    >  如果您看不到 [報表資料] 窗格，請在 [檢視] 索引標籤上，核取 [報表資料]。  
  
2.  將 [頁碼] 欄位從 [報表資料] 窗格拖曳至報表頁首或頁尾。  
  
    > [!NOTE]  
    >  頁尾就會自動加入至報表。 若要新增頁首，請在 [插入] 索引標籤上，按一下 [頁首]，然後按一下 [新增頁首]。  
    >   
    >  包含簡單運算式 [&PageNumber] 的文字方塊隨即加入。  
  
### <a name="to-add-the-word-page-before-the-page-number"></a>若要在頁碼前面加入 "Page" 一詞  
  
1.  以滑鼠右鍵按一下包含 [&PageNumber] 的文字方塊，然後按一下 [運算式]。  
  
     [設定運算式對象: 值] 文字方塊包含運算式 =Globals!PageNumber。  
  
2.  將游標置於類型 = 符號後`"Page " &`。  
  
     運算式現在是 ="Page "&Globals!PageNumber  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-total-number-of-pages-after-the-page-number"></a>若要在頁碼後面加入總頁數  
  
1.  以滑鼠右鍵按一下包含運算式的文字方塊，然後按一下 [運算式]。  
  
2.  在運算式結尾鍵入 **&" of "&**。  
  
3.  在 [類別目錄] 窗格中，展開 [內建欄位]，然後按兩下 [TotalPages]。  
  
     運算式現在是 ="Page "&Globals!PageNumber &" of "&Globals!TotalPages  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [頁首和頁尾&#40;報表產生器和 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)   
 [在文字方塊中格式化文字&#40;報表產生器和 SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  