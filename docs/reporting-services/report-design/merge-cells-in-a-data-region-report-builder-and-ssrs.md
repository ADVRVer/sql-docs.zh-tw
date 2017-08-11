---
title: "資料區域 （報表產生器及 SSRS） 中合併資料格 |Microsoft 文件"
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
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c643b94c86109a99e1448093b4b9744924fcd7f7
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a>在資料區中合併資料格 (報表產生器及 SSRS)
在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 分頁報表中，您可以在資料區域中合併資料格來結合資料格、增進資料區域外觀，或為資料行群組與資料列群組提供橫跨的標籤。  
  
您只能合併資料區的每個區域內的資料格：邊角、資料行標頭、群組定義 (或資料列標頭) 以及主體。 您無法合併跨越區域界限的資料格。 例如，您無法將資料區邊角區域中的資料格與資料列群組區域中的資料格合併。 請深入了解 [資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-merge-cells-in-a-data-region"></a>若要在資料區中合併資料格  
  
1.  在報表設計介面的資料區中，按一下要合併的第一個資料格。 按住滑鼠左鍵，以垂直或水平方向拖曳來選取相鄰的資料格。 選取的資料格就會反白顯示。  
  
2.  以滑鼠右鍵按一下選取的資料格，然後選取**合併資料格**。 選取的資料格就會結合到單一的資料格中。  
  
3.  重複步驟 1 和 2，在資料區域中合併其他相鄰的資料格。  
  
## <a name="see-also"></a>請參閱＜  
[Tablix 資料區](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)  
 [資料表 &#40;報表產生器及 SSRS &#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [建立矩陣](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [使用清單建立發票和表單](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
[資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
