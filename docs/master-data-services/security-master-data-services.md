---
title: 安全性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56bc41ea-de28-4184-aa7e-99111ae55af5
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 200e7f97e0356fae1505bf3786ab11e483f839f8
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="security-master-data-services"></a>安全性 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]在  中，使用安全性可確保使用者具有執行工作所需之特定主要資料的存取權，並避免使用者存取不應使用的資料。  
  
 您也可以使用安全性讓某位使用者成為特定模型和功能區域的管理員 (例如，讓某位使用者建立 Customer 模型的版本，或提供某位使用者設定安全性權限的能力)。  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 安全性是以本機或 Active Directory 網域使用者和群組為基礎。 MDS 安全性可讓您使用更精細的詳細資料層級，來決定使用者可以存取的資料。 由於此資料粒度，安全性很輕易就會變得複雜，因此使用重疊的使用者和群組時要特別小心。 如需詳細資訊，請參閱[重疊的使用者和群組的權限 &#40;Master Data Services&#41;](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)。  
  
  您可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式的 [使用者及群組的權限] 功能區域中，使用 Web 服務指派安全性存取權。  
  
## <a name="types-of-users"></a>使用者類型  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]的使用者類型有兩種：  
  
-    在 [總管] 功能區域中存取資料的使用者。  
  
-   可在 [總管] 以外的區域中執行管理工作的使用者。 這些使用者即稱為[管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)。  
  
## <a name="how-to-set-security"></a>如何設定安全性  
 若要提供存取 MDS 之資料或功能的使用者或群組權限，您必須指派：  
  
-   [功能區域存取權](../master-data-services/functional-area-permissions-master-data-services.md)，決定使用者可以存取使用者介面五個功能區域的哪一個。  
  
-   [模型物件權限](../master-data-services/model-object-permissions-master-data-services.md)，決定使用者可以存取的屬性，以及使用者對這些屬性的存取權類型 (讀取、建立和更新)。 使用者也可以在模型等級指派系統管理員權限。  
  
-   (選擇性) [階層成員權限](../master-data-services/hierarchy-member-permissions-master-data-services.md)，決定使用者可以存取的成員，以及使用者對這些成員的存取權類型 (讀取、更新和刪除)。  
  
 將權限指派給屬性和成員時，權限會交集，此時規則會決定優先使用的權限。 如需詳細資訊，請參閱 [如何決定權限 &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)。  
  
## <a name="security-in-the-add-in-for-excel"></a>Excel 的增益集安全性  
 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中設定的安全性也適用於 [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]。 使用者只能檢視和使用擁有其權限的資料。 管理員可以執行管理工作。  
  
 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 唯一需要注意的是， 中指派的所有安全性在經過 20 分鐘的間隔之前，都不會在 Excel 中生效。 *MdsMaximumUserInformationCacheInterval* 此間隔是透過 web.config 檔案中的  設定所定義。 若要變更間隔，您可以變更此設定並重新啟動 IIS。  
  
## <a name="related-tasks"></a>相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|建立具有模型完整權限的使用者。|[建立模型管理員 &#40;Master Data Services&#41;](../master-data-services/create-a-model-administrator-master-data-services.md)|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]將 Active Directory 群組加入至 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ；這是提供群組權限，以存取  Web 應用程式中資料的第一步。|[新增群組 &#40;Master Data Services&#41;](../master-data-services/add-a-group-master-data-services.md)|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 將權限指派給  Web 應用程式的功能區域。|[指派功能區域權限 &#40;Master Data Services&#41;](../master-data-services/assign-functional-area-permissions-master-data-services.md)|  
|透過將權限指派給模型物件，來將權限指派給屬性值。|[指派模型物件權限 &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)|  
|透過將權限指派給階層節點，來將權限指派給成員值。|[指派階層成員權限 &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)|  
  
## <a name="see-also"></a>另請參閱  
 [管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)   
 [使用者和群組 &#40;Master Data Services&#41;](../master-data-services/users-and-groups-master-data-services.md)   
 [功能區域權限 &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)   
 [模型物件權限 &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [階層成員權限 &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [如何決定權限 &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
