---
title: "指派階層成員權限 (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: ab447d35def70cd31f34806294de568c243e6d11
ms.contentlocale: zh-tw
ms.lasthandoff: 09/07/2017

---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a>指派階層成員權限 (Master Data Services)
  指派階層成員的權限，提供使用者或群組存取權，以便在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的總管功能區域中檢視資料。  
  
 階層成員權限為選擇性。 它們為必要的模型物件權限提供更細微的控制。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序：  
  
-   您必須擁有存取 **[使用者及群組的權限]** 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱 [Administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md) (管理員 (Master Data Services))。  
  
### <a name="to-assign-hierarchy-member-permissions"></a>若要指派階層成員權限  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[使用者及群組的權限]**。  
  
2.  在 **[使用者]** 或 **[群組]** 頁面上，選取要編輯之使用者或群組的資料列。  
  
3.  按一下 **[編輯選取的使用者]**。  
  
4.  按一下 [階層成員] 索引標籤。  
  
5.  從 [模型] 清單中選取模型。  
  
6.  從 **[版本]** 清單中選取版本。  
  
7.  從 [階層] 清單中選取階層。  
  
8.  按一下 **[編輯]**。  
  
9. 展開樹狀結構，然後按一下要指派權限的階層節點。  
  
10. 從功能表中，選取 [建立]、[讀取]、[更新] 和 [刪除] 的組合，或是 [拒絕] 權限。  
  
11. 按一下 **[儲存]**。  
  
    > [!NOTE]  
    >  階層成員權限不會立即生效。 如需詳細資訊，請參閱[立即套用成員權限 &#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [刪除階層成員權限 &#40;Master Data Services&#41;](../master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [指派模型物件權限 &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [階層成員權限 &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  

