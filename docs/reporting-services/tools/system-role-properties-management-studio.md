---
title: "系統角色屬性 (Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.reportserver.systemroleproperties.f1"
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
caps.latest.revision: 30
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 30
---
# 系統角色屬性 (Management Studio)
  您可以使用 [系統角色] 頁面來檢視目前為報表伺服器定義的系統角色定義。 系統角色定義包含相對於整個網站 (而非個別項目) 所執行之工作的具名集合。 角色定義會指派給使用者或群組，以便建立產生的角色指派。 角色定義中的工作會指定使用者或群組可執行的工作。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 有兩個預先定義的系統角色定義： **系統管理員** 和 **系統使用者**。 您可以藉由變更工作清單來修改這些角色定義，也可以建立支援不同工作組合的新系統角色。 編輯角色定義將影響包含該角色定義的所有角色指派。  
  
> [!NOTE]  
>  系統角色定義只會用於以原生模式執行的報表伺服器。 如果報表伺服器是針對 SharePoint 整合所設定，這個頁面就無法使用。  
  
## 選項。  
 **名稱**  
 指定系統角色定義的名稱。  
  
 **說明**  
 顯示系統角色定義的描述。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，這項描述只會顯示在此頁面中。 透過報表管理員檢視這個項目的使用者，會在瀏覽資料夾階層時看到此描述。  
  
 **工作**  
 列出此角色定義可以選取的所有系統層級工作。 您可以將項目加入預先定義的工作清單，或者從清單移除項目，以定義使用者藉由這個角色存取指定項目的方式。 您不能建立新的工作，也不能修改現有的工作。  
  
 **說明**  
 提供每個工作的相關資訊。 您不能修改工作描述。  
  
## 請參閱＜  
 [Management Studio F1 說明中的報表伺服器](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [系統層級工作](../../reporting-services/security/system-level-tasks.md)   
 [工作和權限](../../reporting-services/security/tasks-and-permissions.md)   
 [Predefined Roles](../../reporting-services/security/predefined-roles.md)  
  
  