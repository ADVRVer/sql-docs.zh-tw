---
title: 系統管理員
description: 瞭解 Master Data Services 中的系統管理員類型：模型系統管理員、實體系統管理員和超級使用者。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7e65024ac3673e6579e614ad64931ab772b599f3
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2020
ms.locfileid: "92193648"
---
# <a name="administrators-master-data-services"></a>管理員 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  本文說明 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中的系統管理員類型：模型系統管理員、實體系統管理員和進階使用者。  
  
## <a name="model-administrators"></a>模型管理員  
 在中 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ，模型管理員是在 [**模型物件**] 索引標籤上，具有指派給最上層模型物件之系統**管理員**許可權的使用者。當使用者在特定模型上具有系統管理員許可權時，模型的子物件上的任何其他許可權 (模型物件和成員許可權) 都會由模型**管理員**許可權並且，並且會有效地忽略。  
  
-   如果使用者可以存取總管**** 功能區域，即可加入、刪除及更新此區域中的所有主要資料。  
  
-   如果使用者可以存取其他功能區域，即可執行該功能區域中的所有管理工作。  
  
 每個模型可以有多個管理員。 每個使用者都可以是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 部署中一個、數個或所有模型的模型管理員。  
  
 使用者可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中或透過程式設計方式設定為模型管理員。 如需詳細資訊，請參閱 [建立模型管理員 &#40;Master Data Services&#41;](../master-data-services/create-a-model-administrator-master-data-services.md)。  
  
## <a name="entity-administrators"></a>實體系統管理員  
 在中 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ，實體系統管理員是在 [模型物件] 索引標籤上，具有指派給實體物件之系統管理員許可權的使用者。當使用者擁有實體的系統管理員許可權時，實體子物件上的任何其他許可權 (模型物件和成員許可權) 都會被系統管理員許可權取代，而且會被忽略。  
  
-   如果使用者可以存取總管**** 功能區域，即可加入、刪除及更新此區域中的所有主要資料。  
  
-   如果實體變更所需的系統管理員核准，則實體系統管理員可以檢閱，然後核准或拒絕變更集。  
  
 每個實體可以有多個系統管理員。 每個使用者可以是一個、多個或所有實體的實體系統管理員。  
  
 使用者可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中或透過程式設計方式設定為實體系統管理員。 如需詳細資訊，請參閱[建立實體管理員 &#40;Master Data Services&#41;](../master-data-services/create-an-entity-administrator-master-data-services.md)。  
  
## <a name="master-data-services-super-user"></a>Master Data Services 進階使用者  
 在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以將 [進階使用者] 功能區域的權限指派給使用者。 具有 [進階使用者] 功能區域權限的使用者實際上具有所有模型的 [Admin (系統管理員)] 權限，而且具有所有其他功能區域權限。 如需功能區域權限的相關資訊，請參閱[功能區域權限 &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)。  
  
 當您使用[建立資料庫精靈 &#40;Master Data Services 組態管理員&#41;](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md) 建立 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫時，會為 [系統管理員帳戶]**** 指定這個預設進階使用者。  
  
 進階使用者可以執行下列作業：  
  
-   存取所有功能區域。  
  
-   在總管**** 功能區域中，新增、刪除和更新所有模型的所有主要資料。  
  
 您可以將進階使用者權限指派給多個使用者和 (或) 使用者群組。  
  
## <a name="comparing-administrator-types"></a>比較管理員類型  
  
|管理員類型|描述|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 進階使用者|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中所指派權限不會影響系統管理員的存取。<br /><br /> 根據明確指派之功能區域權限或繼承自群組的權限，使用者可以是進階使用者。<br /><br /> 自動擁有所有模型的所有權限。<br /><br /> 自動擁有所有功能區域的存取權。|  
|模型管理員|根據明確指派的系統管理員權限或繼承自群組的權限，使用者可以是模型系統管理員。<br /><br /> 只能存取被授與存取權的功能區域。<br /><br /> 自動擁有特定模型中的所有物件和成員的所有權限。|  
|實體系統管理員|根據明確指派的系統管理員權限或繼承自群組的權限，使用者可以是實體系統管理員。<br /><br /> 只能存取被授與存取權的功能區域。<br /><br /> 自動擁有特定實體中所有物件和成員的所有權限。<br /><br /> 如果實體變更需要核准時，就可以核准暫止的變更集。|  
  
## <a name="external-resources"></a>外部資源  
 請參考 msdn.com 上的 [Security Improvements](/archive/blogs/e7/improvements-to-autoplay)(安全性改進) 部落格文章。  
  
## <a name="see-also"></a>另請參閱  
 [建立模型系統管理員 &#40;Master Data Services&#41;](../master-data-services/create-a-model-administrator-master-data-services.md)   
 [建立 Master Data Services 資料庫](../master-data-services/install-windows/create-a-master-data-services-database.md)   
 [通知 &#40;Master Data Services&#41;](../master-data-services/notifications-master-data-services.md)  
  
