---
title: "建立明確階層 (Master Data Services) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 04/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: "10"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e24294a7402f60b56cb8b3d925e5edc4dfda07a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>建立明確階層 (Master Data Services)
  當您需要成員可存在於任何層級的不完全階層時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中建立明確階層。 明確階層包含來自單一實體的成員。  
  
 建立明確階層之後，您可以在總管 功能區域的這個階層中加入成員。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序：  
  
-   您必須擁有存取 **[系統管理]** 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱 [Administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md) (管理員 (Master Data Services))。  
  
-   您必須啟用明確階層和集合的實體。  
  
### <a name="to-create-an-explicit-hierarchy"></a>若要建立明確階層  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。  
  
2.  在 [管理模型]  頁面上，從方格中選取模型，然後按一下 [實體] 。  
  
3.  在 [管理實體] 頁面上，從方格中選取含有您想要為其建立明確階層的實體的資料列。  
  
4.  按一下 [明確階層] 。  
  
5.  在 [管理明確階層] 頁面上，按一下 [加入]。  
  
6.  在 [名稱] 方塊中，輸入階層的名稱。  
  
7.  (選擇性) 清除 [強制階層] 核取方塊，將階層建立為非強制階層。 如需階層類型的詳細資訊，請參閱[明確階層 &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)。  
  
8.  按一下 **[儲存]**。  
  
## <a name="grid-columns"></a>方格資料行  
 對於您建立的每個明確階層，會將含有七個資料行的資料列新增到方格。 下列是資料行的描述。  
  
|名稱|說明|  
|----------|-----------------|  
|狀態|實體狀態。 當您按一下 [儲存] 時，下列影像隨即顯示，指出正在更新實體。<br /><br /> ![正在更新狀態圖示](../master-data-services/media/mds-statusicon-updating.png "正在更新狀態圖示")<br /><br /> 如果建立或編輯實體時發生錯誤，則會顯示下列影像。<br /><br /> ![錯誤狀態圖示](../master-data-services/media/mds-statusicon-error.png "錯誤狀態圖示")<br /><br /> 如果狀態正常，則會顯示下列影像。<br /><br /> ![正常狀態圖示](../master-data-services/media/mds-statusicon-ok.png "正常狀態圖示")|  
|名稱|明確階層名稱。|  
|強制性|指定明確階層是否為強制性。|  
|建立者|建立明確階層之使用者的使用者名稱。|  
|建立於|建立明確階層的日期和時間。|  
|更新者|最後更新明確階層之使用者的使用者名稱。|  
|更新於|最後更新明確階層的日期和時間。|  
  
## <a name="next-steps"></a>後續步驟  
  
-   [建立合併成員 &#40;Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)  
  
  
  
## <a name="see-also"></a>另請參閱  
 [明確階層 &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [具有明確頂層的衍生階層 &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [變更明確階層名稱 &#40;Master Data Services&#41;](../master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  

