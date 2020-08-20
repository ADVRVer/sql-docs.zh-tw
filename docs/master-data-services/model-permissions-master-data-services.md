---
description: 模型權限 (Master Data Services)
title: 模型權限
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e195c4f2db244fa5cf647c19c0713f24840c3441
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461732"
---
# <a name="model-permissions-master-data-services"></a>模型權限 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  模型權限適用於所有實體、衍生階層、明確階層及存在於模型內的集合。 可以針對任何個別的物件來覆寫指派給模型的權限。  
  
> [!NOTE]  
>  如果使用者是模型管理員，則使用者介面的所有功能區域中都會顯示此模型。 否則，此模型只會顯示在 [總管]**** 功能區域中。 如需詳細資訊，請參閱系統 [管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)。  
  
|權限|描述|  
|----------------|-----------------|  
|**讀取**|使用者可以讀取成員、屬性、階層成員資格或集合成員資格。|  
|**建立**|使用者可以建立成員，並在建立期間指派屬性值。|  
|**更新**|使用者可以更新成員、屬性、階層成員資格或集合成員資格。|  
|**刪除**|使用者可以刪除成員。|  
|**拒絕**|拒絕所有對模型的存取。|  
|**管理員**|模型的管理員權限。 模型層級才提供管理員權限。|  
  
 讀取、建立、更新和刪除權限可以彼此合併。 指派建立、更新和刪除權限時，將會自動指派讀取權限。  
  
## <a name="see-also"></a>另請參閱  
 [指派模型物件使用權限 &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [模型物件使用權限 &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [實體許可權 &#40;Master Data Services&#41;](../master-data-services/entity-permissions-master-data-services.md)   
 [集合權限 &#40;Master Data Services&#41;](../master-data-services/collection-permissions-master-data-services.md)  
  
  
