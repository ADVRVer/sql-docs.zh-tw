---
title: "授與使用者存取報表伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
caps.latest.revision: 54
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a92c37165b8142b7e96a8bb99dee43ea5f12e247
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="grant-user-access-to-a-report-server"></a>將報表伺服器的存取權授與使用者

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用角色型安全性將報表伺服器的存取權授與使用者。 在新的報表伺服器安裝上，只有屬於本機管理員群組的成員擁有報表伺服器內容和作業的權限。 若要讓報表伺服器供其他使用者使用，您必須建立角色指派，以便將使用者或群組帳戶對應至指定工作集合的預先定義角色。

 **SharePoint 模式報表伺服器：** 若為針對 SharePoint 整合模式所設定的報表伺服器，您可以設定使用 SharePoint 權限從 SharePoint 網站存取的方式。 SharePoint 網站的權限等級會決定報表伺服器內容和作業的存取權。 您必須是網站管理員，才能授與 SharePoint 網站的權限。 如需詳細資訊，請參閱 [授與 SharePoint 網站上報表伺服器項目的權限](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)。

 **原生模式報表伺服器：**本主題會著重於報表伺服器設定為原生模式與使用 web 入口網站，若要指派使用者至角色。 目前有兩種角色類型：

- 項目層級角色是用來檢視、加入和管理報表伺服器內容、訂閱、報表處理，以及報表記錄。 項目層級角色指派定義於根節點 ([主資料夾] 資料夾) 或階層中更低的特定資料夾或項目上。

- 系統層級角色會授與並未繫結至任何特定項目之網站範圍作業的存取權。 範例包括使用報表產生器和使用共用排程。

    這兩種角色類型彼此互補，而且您應該一起使用它們。 因此，將使用者加入至報表伺服器是兩個部分的作業。 如果您將某位使用者指派至項目層級角色，就應該同時將他指派至伺服器層級角色。 指派使用者至角色時，您必須選取已經定義的角色。 若要建立、修改或刪除角色，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。 如需詳細資訊，請參閱[建立、刪除或修改角色 &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md)。

## <a name="before-you-start"></a>開始之前

將使用者加入至原生模式報表伺服器之前，請檢閱下列清單。

- 您在報表伺服器電腦上必須是本機管理員群組的成員。 如果您要將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 部署在 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] 或 Windows Server 2008 上，就必須進行其他組態設定，然後才能在本機管理報表伺服器。 如需詳細資訊，請參閱 [設定原生模式報表伺服器進行本機管理](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。

- 若要將這項工作委派給其他使用者，請建立角色指派，以便將使用者帳戶對應至「內容管理員」和「系統管理員」角色。 擁有「內容管理員」和「系統管理員」權限的使用者可以將使用者加入至報表伺服器。

- 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，檢視「系統角色」和「使用者角色」的預先定義角色，如此您就可以熟悉每個角色的工作類型。 工作描述中不會顯示入口網站中，所以您會想要先熟悉這些角色您開始加入使用者。

- (選擇性) 您可以自訂角色或定義其他角色來包含所需的工作集合。 例如，如果您計畫針對個別項目使用自訂安全性設定，可能會想要建立新角色定義，以便授與資料夾的檢視存取權。

### <a name="to-add-a-user-or-group-to-a-system-role"></a>若要將使用者或群組加入至系統角色

1. 啟動[入口網站](../web-portal-ssrs-native-mode.md)。

2. 選取*齒輪圖示*右上方。

3. 選取 [網站設定]。

4. 選取 [安全性] 。

5. 選取**新增群組或使用者**。

6. 在**群組或使用者**中，輸入 Windows 網域使用者或群組帳戶，格式如下：\<網域 >\\< 帳戶\>。 

    > [!NOTE]
    > 如果您要使用表單驗證或自訂安全性，請使用適用於部署的正確格式來指定使用者或群組帳戶。

7. 選取系統角色，然後再選取**確定**。

    由於角色是累計的，因此如果您同時選取「系統管理員」和「系統使用者」，則使用者或群組就能夠以這兩種角色來執行工作。

8. 重複上述步驟，以便建立其他使用者或群組的指派。

### <a name="to-add-a-user-or-group-to-an-item-role"></a>若要將使用者或群組加入至項目角色

1. 啟動**入口網站**並找出您要新增使用者或群組的報表項目。

2. 選取**...** （橢圓形） 上的項目。

3. 在下拉式功能表中，選取**管理**。

4. 選取 [安全性] 。

5. 選取**新增群組或使用者**。

    > [!NOTE]
    > 如果項目目前是從父項目繼承安全性，請選取**自訂安全性**在工具列中，若要變更安全性設定。 然後選取**新增群組或使用者**。

6. 在**群組或使用者**中，輸入 Windows 網域使用者或群組帳戶，格式如下：\<網域 >\\< 帳戶\>。 如果您要使用表單驗證或自訂安全性，請使用適用於部署的正確格式來指定使用者或群組帳戶。

7. 選取一或多個角色定義描述如何使用者或群組應存取的項目，然後選取**確定**。

8. 重複上述步驟，以便建立其他使用者或群組的指派。

## <a name="next-steps"></a>後續的步驟

[建立及管理角色指派](../../reporting-services/security/create-and-manage-role-assignments.md)   
[新增角色指派： 編輯角色指派頁面 &#40;報表管理員 &#41;](http://msdn.microsoft.com/library/3319ced0-4b86-42af-b18d-da41a625113c)   
[安全性屬性頁面，項目 &#40;報表管理員 &#41;](http://msdn.microsoft.com/library/351b8503-354f-4b1b-a7ac-f1245d978da0)   
[角色指派](../../reporting-services/security/role-assignments.md)   
[角色定義](../../reporting-services/security/role-definitions.md)  

更多問題嗎？ [請嘗試詢問 Reporting Services 論壇](http://go.microsoft.com/fwlink/?LinkId=620231)
