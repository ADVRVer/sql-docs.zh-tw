---
title: 第12課：建立角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec4bad8ef036e8f19ce0a856f3d9c04bafd0e7c5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079273"
---
# <a name="lesson-12-create-roles"></a>第 12 課：建立角色
  在這一課，您將建立角色。 角色會藉由僅限身為角色成員的 Windows 使用者存取的方式，提供模型資料庫物件和資料安全性。 每個角色都定義有單一權限︰「無」、「讀取」、「讀取和處理」、「處理」或「系統管理員」。 您可以使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中的 [角色管理員] 對話方塊，在模型撰寫期間定義角色。 部署模型之後，您可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]管理角色。 如需詳細資訊，請參閱[角色 &#40;SSAS 表格式&#41;](tabular-models/roles-ssas-tabular.md)。  
  
> [!NOTE]  
>  完成本教學課程並不需要建立角色。 根據預設，您目前登入的帳戶將擁有模型的「系統管理員」權限。 不過，為了讓組織中的其他使用者能夠使用報表用戶端應用程式瀏覽模型，您必須至少建立一個具有「讀取」權限的角色，並將這些使用者加入為成員。  
  
 您將建立三個角色︰  
  
-   銷售經理-此角色可包含組織中您想要對所有模型物件和資料具有讀取權限的使用者。  
  
-   美國銷售分析師-此角色可包含組織中的使用者，您只希望能夠在美國（美國）流覽與銷售相關的資料。 對於此角色，您將使用 DAX 公式來定義「資料列篩選條件」**，以限制成員只能瀏覽美國方面的資料。  
  
-   系統管理員-此角色可包含您想要擁有系統管理員許可權的使用者，這允許無限制的存取權和許可權，在 model 資料庫上執行管理工作。  
  
 因為組織中的 Windows 使用者和群組帳戶都是獨一無二，您可以將特定組織中的帳戶新增至成員。 不過，在本教學課程中，您也可以將成員留白。 稍後在「第 12 課︰在 Excel 中進行分析」中，您仍然可以測試每個角色的效果。  
  
 這堂課的預估完成時間：**15 分鐘**  
  
## <a name="prerequisites"></a>Prerequisites  
 本主題是表格式模型教學課程的一部分，請依序完成。 在執行本課中的工作之前，您應已完成上一課： [第 11 課：建立資料分割](lesson-10-create-partitions.md)。  
  
## <a name="create-roles"></a>建立角色  
  
#### <a name="to-create-a-sales-manager-user-role"></a>建立「銷售經理」使用者角色  
  
1.  在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]**** 功能表，然後按一下 [角色]****。  
  
2.  在 [角色管理員]**** 對話方塊中，按一下 [新增]****。  
  
     清單中會新增 [無] 權限的新角色。  
  
3.  按一下 [新增] 角色，然後在 [**名稱**] 資料行中，將角色`Internet Sales Manager`重新命名為。  
  
4.  在 [權限]**** 資料行中，按一下下拉式清單，然後選取 [讀取]**** 權限。  
  
5.  選擇性：按一下 [成員]**** 索引標籤，然後按一下 [新增]****。  
  
6.  在 [選取使用者或群組]**** 對話方塊中，輸入您想從組織中加入此角色的 Windows 使用者或群組。  
  
7.  確認您的選擇，然後按一下 **[確定]**  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>建立「美國銷售分析師」使用者角色  
  
1.  在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]**** 功能表，然後按一下 [角色]****。  
  
2.  在 [角色管理員]**** 對話方塊中，按一下 [新增]****。  
  
     清單中會新增 [無] 權限的新角色。  
  
3.  按一下 [新增] 角色，然後在 [**名稱**] 資料行中，將角色`Internet Sales US`重新命名為。  
  
4.  在 [權限]**** 資料行中，按一下下拉式清單，然後選取 [讀取]**** 權限。  
  
5.  按一下 [資料列篩選] 索引標籤，然後僅針對 [Geography]**** 資料表，在 [DAX 篩選] 資料行中輸入下列公式：  
  
     `=Geography[Country Region Code] = "US"`  
  
     「資料列篩選條件」公式必須解析成布林值 (TRUE/FALSE)。 在此公式中，您指定只有國家地區代碼值為 "US" 的資料列才會顯示給使用者。  
  
     完成建立公式時，按 ENTER。  
  
6.  選擇性：按一下 [成員]**** 索引標籤，然後按一下 [新增]****。  
  
7.  在 [選取使用者或群組]**** 對話方塊中，輸入您想從組織中加入此角色的 Windows 使用者或群組。  
  
8.  確認您的選擇，然後按一下 **[確定]**  
  
#### <a name="to-create-an-administrator-role"></a>若要建立 Administrator 角色  
  
1.  在 [角色管理員]**** 對話方塊中，按一下 [新增]****。  
  
2.  按一下 [新增] 角色，然後在 [**名稱**] 資料行中，將角色`Internet Sales Administrator`重新命名為。  
  
3.  按一下 [權限]**** 資料行中的下拉式清單，然後選取 [系統管理員]**** 權限。  
  
4.  按一下 [成員]**** 索引標籤，然後按一下 [新增]****。  
  
5.  選擇性：在 [選取使用者或群組]**** 對話方塊中，從組織輸入要包含在角色中的 Windows 使用者或群組。  
  
6.  確認您的選擇，然後按一下 **[確定]**  
  
## <a name="next-steps"></a>後續步驟  
 若要繼續進行本教學課程，請前往下一課： [第 13 課：在 Excel 中進行分析](lesson-12-analyze-in-excel.md)。  
  
  
