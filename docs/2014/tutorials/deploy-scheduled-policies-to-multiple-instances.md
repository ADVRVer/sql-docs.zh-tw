---
title: 將已排程的原則部署到多個執行個體 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
caps.latest.revision: 6
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ebabe1d982f427002eea31f09541cd40654bcfc1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249528"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a>將已排程的原則部署至多個執行個體
  您可以使用已註冊的伺服器，將已排程的原則從中央位置部署到 Managed 伺服器。 您可以從本機伺服器群組，或從中央管理伺服器部署已排程的原則。  
  
 在這個工作中，您將進行下列作業：  
  
1.  將您在先前工作中排程的原則匯出至資料夾。  
  
2.  將已排程的原則部署到透過已註冊的伺服器所管理的目標執行個體。  
  
 您必須在已完成本課程先前工作的電腦上執行這些工作。  
  
## <a name="prerequisites"></a>先決條件  
 此工作的必要條件如下：  
  
-   您必須先完成本課程先前的工作。  
  
-   其上要部署已排程原則的執行個體必須是執行 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 或更新版本。 若要進行自動化作業，原則必須儲存在本機位置，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 版本不支援此功能。  
  
-   必須在已註冊的伺服器中註冊的伺服器，您要部署已排程的原則，在**本機伺服器群組**或**中央管理伺服器**節點。 如需詳細資訊，請參閱下列主題：  
  
    -   [建立或編輯伺服器群組 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   [註冊連接的伺服器&#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)。  
  
    -   [建立中央管理伺服器與伺服器群組 &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a>若要將已排程的原則匯出為 .xml 檔案  
  
1.  在伺服器上您在先前的工作設定排程的原則，依序展開**管理**，展開**原則管理**，然後按一下**原則**。  
  
2.  在 [檢視] 功能表上，按一下 [物件總管詳細資料]。  
  
3.  在 **物件總管詳細資料**窗格中，選取所有已排程的最佳做法原則，您想要部署到其他伺服器透過已註冊的伺服器。  
  
    > [!NOTE]  
    >  您可以按一下**分類**標題，依類別排序的原則。  
  
4.  選取範圍，以滑鼠右鍵按一下，然後按一下**匯出原則**。  
  
5.  如果您選取多個原則以在匯出**瀏覽資料夾** 對話方塊中，選取目的地資料夾，或建立新的資料夾。 這一課中，建立新的資料夾路徑**C:\Scheduled_BP_Policies**，然後按一下**確定**。  
  
     如果您只選取一個要在匯出的原則**匯出原則**對話方塊方塊中，建立新的資料夾路徑**C:\Scheduled_BP_Policies**，按一下 **開啟**，然後按一下**儲存**。  
  
     .xml 原則檔案是建立在資料夾位置。  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a>若要將已排程的原則部署到透過已註冊的伺服器所管理的伺服器  
  
1.  在 [檢視] 功能表上，按一下 [已註冊的伺服器]。  
  
2.  依序展開**Database Engine**，展開**本機伺服器群組**或**中央管理伺服器**，以滑鼠右鍵按一下您想要部署原則的節點，然後按一下 **匯入原則**。  
  
    > [!NOTE]  
    >  如果您以滑鼠右鍵按一下**本機伺服器群組**或中央管理伺服器本身，原則就會部署到所有受管理的伺服器。 如果以滑鼠右鍵按一下特定的伺服器群組，原則就只會部署到該群組中的伺服器。 如果以滑鼠右鍵按一下特定的已註冊伺服器，原則就只會部署到該伺服器。  
  
3.  旁**匯入的檔案**，按一下省略符號按鈕 (**...**).  
  
4.  在 [**選取原則**] 對話方塊中，瀏覽至您儲存已排程的原則的資料夾位置。 此範例中，瀏覽到位置**C:\Scheduled_BP_Policies**。  
  
5.  選取您想要匯入到目標執行個體，然後按一下 原則**開啟**。  
  
6.  在 **匯入**對話方塊中，於**原則狀態**清單中，選取所需的原則狀態。 您可以選擇在匯入原則保留原則狀態 (啟用) 或加以停用。 請注意，原則必須啟用才能按排程執行。  
  
7.  按一下 **確定**原則匯入所有目標執行個體。  
  
    > [!NOTE]  
    >  如果有任何錯誤，**匯入**對話方塊不會消失。 按一下 **記錄**頁面，即可檢視錯誤訊息。 按一下 **取消**以關閉對話方塊。  
  
8.  若要檢視的目標執行個體的原則，連接到執行個體，開啟物件總管 中，展開**管理**，然後展開**原則**。 您應該會看到在匯入的原則**原則**節點。 您可以在每個原則上按兩下來檢視排程或變更設定。  
  
    > [!NOTE]  
    >  若要在已排程的原則執行後檢視評估結果，請開啟目標執行個體上的「原則記錄」記錄檔。 若要開啟記錄檔，以滑鼠右鍵按一下**原則管理**，然後按一下**檢視歷程記錄**。  
  
## <a name="summary"></a>摘要  
 本教學課程已為您示範如何針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一個或多個執行個體，視需要或按排程來執行最佳做法原則的評估。  
  
## <a name="next"></a>下一個  
 本教學課程已完成。 若要返回開頭，請參閱[教學課程： 評估原則式管理的最佳作法](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md)。  
  
 若要查看一份[!INCLUDE[ssDE](../includes/ssde-md.md)]教學課程中，按一下[Database Engine 教學課程](../relational-databases/database-engine-tutorials.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來管理伺服器](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
