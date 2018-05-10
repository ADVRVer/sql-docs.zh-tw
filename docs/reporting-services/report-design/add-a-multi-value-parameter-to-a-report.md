---
title: 將多值參數新增至報表 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62cddfc4975dfc4d48bfe6d821db50b48645e872
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="add-a-multi-value-parameter-to-a-report"></a>將多值參數加入至報表
  您可以在報表中新增參數，好讓使用者可以為參數選取多個值。  
  
 您可以將多個參數值傳遞給報表 URL 中的報表。 如需包含多值參數的 URL 範例，請參閱 [在 URL 內傳遞報表參數](../../reporting-services/pass-a-report-parameter-within-a-url.md)。  
  
 如需如何將多個參數值傳遞給預存程序的詳細資訊，請參閱 mssqltips.com 上的 [為 SSRS 報表處理複選參數](http://go.microsoft.com/fwlink/?LinkId=321529) 。  
  
## <a name="to-add-a-multi-value-parameter"></a>若要加入多值參數  
  
1.  在「報表產生器」中，開啟您要加入多值參數的報表。  
  
2.  以滑鼠右鍵按一下報表資料集，然後按一下 [資料集屬性]  
  
3.  將變數加入至資料集查詢，其方式是在 **[查詢]** 方塊中編輯查詢文字或是使用查詢設計工具來加入篩選。 如需詳細資訊，請參閱[在關聯式查詢設計工具中建立查詢 &#40;報表產生器和 SSRS&#41;](../../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    > *  查詢文字的查詢變數不能包含 DECLARE 陳述式。  
    > *  查詢變數的文字必須包含 **IN** 運算子，如上述範例所示。  
    > *  請務必如上所示在變數周圍加上括弧。 否則，報表會無法轉譯，而且會顯示「必須宣告純量變數」錯誤。  
  
    系統會針對查詢變數自動建立內嵌資料集或共用資料集的資料集參數。 系統會自動針對資料集參數建立報表參數。  
  
4.  在 [報表資料] 窗格中展開 [參數] 節點，並以滑鼠右鍵按一下為資料集參數自動建立的報表參數，然後按一下 [參數屬性]。  
  
5.  在 **[一般]** 索引標籤上選取 **[允許多個值]** ，允許使用者針對參數選取多個值。  
  
6.  (選擇性) 在 [可用的值] 索引標籤中，指定要對使用者顯示的可用值清單。  
  
     可用值清單會將使用者可以做的選擇限制為參數的有效值。 如果是多個值，清單的最開頭是 **[全選]** 功能，好讓使用者只需按一下就可以選取或清除所有值。 如果您選擇從資料集查詢取得報表參數的可用值，請確定選取的資料集不能包含與相同報表參數有關聯的查詢變數。  
  
     如需詳細資訊，請參閱[為報表參數新增、變更或刪除可用的值 &#40;報表產生器和 SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-available-values-for-a-report-parameter.md)。  

## <a name="see-also"></a>另請參閱  
 [將串聯參數加入至報表 &#40;報表產生器和 SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [加入、變更或刪除報表參數 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  
