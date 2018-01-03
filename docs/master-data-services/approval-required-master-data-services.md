---
title: "需要核准 (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5fa143b8b1f8316d5de80b895399e328d8a6a6c8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="approval-required-master-data-services"></a>需要核准 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]內，系統管理員可以將實體設定為需要核准。 對此實體的所有變更都需要一個實體系統管理員檢閱並核准變更。  
  
> [!NOTE]  
>  分葉成員上所做的變更需要核准。 已被取代的明確階層和集合上之變更會略過核准。  
>   
>  暫存資料表的處理序所做的變更會略過核准。  
>   
>  商務規則所做的變更會略過核准。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要執行此程序：  
  
-   您必須擁有存取 [系統管理] 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱[管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)  
  
-   實體必須存在。 如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="to-enable-approval-required-for-an-entity"></a>啟用實體所需的核准  
  
1.  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，按一下 [系統管理]。  
  
2.  在 [管理模型] 頁面上，從方格中選取模型，然後按一下 [實體]。  
  
3.  在 [管理實體] 頁面上，從方格中選取含有您想要啟用 [需要核准] 之實體的資料列。  
  
4.  按一下 [編輯]，並選取 [需要核准]，然後按一下 [儲存]。  
  
## <a name="see-also"></a>另請參閱  
 [變更集 &#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)  
  
  
