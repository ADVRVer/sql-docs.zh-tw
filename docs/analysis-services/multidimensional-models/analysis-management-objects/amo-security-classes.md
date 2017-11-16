---
title: "AMO 安全性類別 |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, security
- security [AMO]
- AMO, security
ms.assetid: e3d5012a-8121-40de-9244-1fc824228693
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b61917a7e0191e1645dedef69a311a8f901d12b9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="amo-security-classes"></a>AMO 安全性類別
  本主題包含下列幾節：  
  
-   [Role 和 RoleMember 物件](#RolesMembers)  
  
-   [權限物件](#Permissions)  
  
 下圖顯示在本主題中說明的類別關聯性。  
  
 ![本主題涵蓋在 AMO 中的安全性類別](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-securityclasses.gif "本主題涵蓋在 AMO 中的安全性類別")  
  
##  <a name="RolesMembers"></a>Role 和 RoleMember 物件  
 建立 <xref:Microsoft.AnalysisServices.Role> 物件的方式是將它加入資料庫的角色集合，然後使用 Update 方法將 <xref:Microsoft.AnalysisServices.Role> 物件更新到伺服器。 <xref:Microsoft.AnalysisServices.Role> 物件必須先更新才能使用。  
  
 若要移除 <xref:Microsoft.AnalysisServices.Role> 物件，必須使用 <xref:Microsoft.AnalysisServices.Role> 物件的 Drop 方法來卸除它。 來自角色集合的 Remove 方法只會讓您在應用程式中看不到角色，但是並不會將角色從伺服器移除。 如果有任何權限與 <xref:Microsoft.AnalysisServices.Role> 物件關聯，則無法卸除該物件。  
  
 建立 <xref:Microsoft.AnalysisServices.RoleMember> 物件的方式是將使用者加入角色的成員集合，然後使用 Update 方法將 <xref:Microsoft.AnalysisServices.Role> 物件更新到伺服器。 只有伺服器管理員或是資料庫管理員可以建立角色。 <xref:Microsoft.AnalysisServices.Role> 物件必須更新至伺服器，這樣它的任何成員才可以使用使用者已授與權限的任何物件。  
  
 若要移除 <xref:Microsoft.AnalysisServices.RoleMember> 物件，必須使用該集合的 Remove 方法從集合移除它，然後使用 Update 方法來更新角色。  
  
 如需有關這些物件可用之方法與屬性的詳細資訊，請參閱 <xref:Microsoft.AnalysisServices.Role> 中的 <xref:Microsoft.AnalysisServices.RoleMember> 與 <xref:Microsoft.AnalysisServices>。  
  
##  <a name="Permissions"></a>權限物件  
 建立 <xref:Microsoft.AnalysisServices.Permission> 物件的方式是將它加入物件的權限集合，然後使用 Update 方法將 <xref:Microsoft.AnalysisServices.Permission> 物件更新到伺服器。  
  
 若要移除 <xref:Microsoft.AnalysisServices.Permission> 物件，必須使用該物件的 Drop 方法來卸除它。 從權限集合執行移除方法只會讓您在應用程式中看不到權限，但是它並不會從伺服器移除 <xref:Microsoft.AnalysisServices.Permission> 物件。 如果有任何權限與角色關聯，則無法刪除角色。  
  
 如需有關可用方法和屬性的詳細資訊，請參閱 <xref:Microsoft.AnalysisServices.Permission> 中的 <xref:Microsoft.AnalysisServices>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.AnalysisServices>   
 [程式設計 AMO 安全性物件](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-security-objects.md)   
 [權限和存取權限 &#40;Analysis Services-多維度資料 &#41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [AMO 類別簡介](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [邏輯架構 &#40;Analysis Services-多維度資料 &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [資料庫物件 &#40;Analysis Services-多維度資料 &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  

