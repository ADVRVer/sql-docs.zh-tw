---
title: 集合權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 778e4890ede89415ac52b1a8fd70af4366a0133b
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35332612"
---
# <a name="collection-permissions-master-data-services"></a>集合權限 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  集合權限會套用至某個實體的所有集合。 您不能提供權限給特定集合，權限會套用到所有的集合。  
  
> [!NOTE]  
>  這些權限只適用於使用者介面的 [總管] 功能區域。  
  
|權限|描述|  
|----------------|-----------------|  
|**讀取**|使用者可以讀取集合成員和成員屬性。|  
|**建立**|使用者可以建立集合成員及指派屬性值。|  
|**Update**|使用者可以更新集合成員、屬性和關聯性。|  
|**刪除**|使用者可以刪除集合成員。|  
|**拒絕**|拒絕所有對集合成員的存取。|  
  
 讀取、建立、更新和刪除權限可以合併。 指派建立、更新和刪除時，將會自動指派讀取權限。  
  
## <a name="see-also"></a>另請參閱  
 [指派模型物件權限 &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [集合 &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [模型物件權限 &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
