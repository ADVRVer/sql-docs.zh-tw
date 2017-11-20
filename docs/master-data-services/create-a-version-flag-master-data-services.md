---
title: "建立版本旗標 (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 039f5c71946946bc6093dcfcd432da21d75ec2ad
ms.contentlocale: zh-tw
ms.lasthandoff: 09/07/2017

---
# <a name="create-a-version-flag-master-data-services"></a>建立版本旗標 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，建立要指派給版本的版本旗標。 此旗標可以指出使用者或訂閱系統應該使用的版本。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序：  
  
-   您必須擁有存取 **[版本管理]** 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱 [Administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md) (管理員 (Master Data Services))。  
  
-   您必須具有存取 [版本管理] 功能區域的權限。 如需詳細資訊，請參閱[功能區域權限 &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)。  
  
### <a name="to-create-a-version-flag"></a>若要建立版本旗標  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[版本管理]**。  
  
2.  在 **[管理版本]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[旗標]**。  
  
3.  在 **[管理版本旗標]** 頁面上，從 **[模型]** 欄位選取您要建立旗標的模型。  
  
4.  按一下 **[加入]**。  
  
5.  在 **[名稱]** 方塊中，輸入名稱。  
  
6.  在 **[描述]** 方塊中，輸入描述。  
  
7.  在 **[僅限認可的版本]** 欄位中，選取 **[True]** 表示旗標只能指派給狀態為 **[已認可]** 的版本。 選取 **[False]** 表示旗標可以指派給任何狀態的版本。  
  
8.  按一下 **[儲存]**。  
  
## <a name="next-steps"></a>後續步驟  
  
-   [將旗標指派給版本 &#40;Master Data Services&#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [版本 &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [變更版本旗標名稱 &#40;Master Data Services&#41;](../master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  

