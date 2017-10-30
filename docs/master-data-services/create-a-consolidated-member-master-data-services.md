---
title: "建立合併成員 (Master Data Services) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
caps.latest.revision: 12
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: a48fd41c90f01925b2cd884f33cf37bc0407d533
ms.contentlocale: zh-tw
ms.lasthandoff: 09/07/2017

---
# <a name="create-a-consolidated-member-master-data-services"></a>Create a Consolidated Member (Master Data Services)
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]當您需要明確階層的父節點時，可以在 中建立合併成員。 如果您想要加入大量資料，請改用暫存表格。 如需詳細資訊，請參閱[從資料表匯入資料 &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序：  
  
-   您必須擁有存取 **[總管]** 功能區域的權限。  
  
-   您必須至少具有要新增成員的實體之合併模型物件的 **更新** 權限，以及實體下方合併類型的 **建立** 權限。  
  
### <a name="to-create-a-consolidated-member"></a>若要建立合併成員  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。  
  
2.  從 **[版本]** 清單中選取版本。  
  
3.  按一下 **[總管]**。  
  
4.  從功能表列指向 **[階層]** ，然後按一下要加入合併成員的階層名稱。  
  
5.  在方格上方，選取 **[合併成員]** 或 **[階層中的所有合併成員]** 選項。  
  
6.  在左窗格中，選取您要在其下建立合併成員的根節點或合併成員。  
  
7.  按一下 **[加入]**。  
  
8.  填完右邊窗格中的欄位。  
  
9. 選擇性。 在 **[註解]** 方塊中，輸入有關加入此成員之原因的註解。 可存取成員的所有使用者都可以檢視註解。  
  
10. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [建立明確階層 &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [建立分葉成員 &#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)   
 [成員 &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [明確階層 &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  

