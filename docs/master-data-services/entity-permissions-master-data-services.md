---
title: "實體權限 (Master Data Services) | Microsoft Docs"
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
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 86574d904f58a15eff67a45525bdffd5ca8da849
ms.contentlocale: zh-tw
ms.lasthandoff: 09/07/2017

---
# <a name="entity-permissions-master-data-services"></a>實體權限 (Master Data Services)
  實體權限適用於：  
  
-   所有實體的屬性，包括分葉成員和合併成員的 **Name** 和 **Code**。  
  
-   所有實體的集合。  
  
-   明確階層成員資格和關聯性。  
  
 當您擁有實體的權限時，您可從實體、實體的明確階層和集合中加入及移除成員。  
  
> [!NOTE]  
>  這些權限只適用於使用者介面的 [總管] 功能區域。  
  
|權限|說明|  
|----------------|-----------------|  
|**讀取**|使用者可以讀取成員、屬性、階層成員資格或集合成員資格。|  
|**建立**|使用者可以建立成員，並在建立期間指派屬性值。|  
|**Update**|使用者可以更新成員、屬性、階層成員資格或集合成員資格。|  
|**Delete**|使用者可以刪除成員。|  
|**拒絕**|拒絕所有對實體的存取。|  
  
 讀取、建立、更新和刪除權限可以彼此合併。 指派建立、更新和刪除權限時，將會自動指派讀取權限。  
  
## <a name="see-also"></a>另請參閱  
 [指派模型物件權限 &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [模型物件權限 &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [實體 &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  

