---
title: 移轉精靈 」 (AccessToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migration Wizard dialog box
- Migration Wizard, adding Access databases
- Migration Wizard, Connect to SQL Azure
- Migration Wizard, Connect to SQL Server
- Migration Wizard, Link Tables
- Migration Wizard, Migration status
- Migration Wizard, New Project
- Migration Wizard, Selecting objects to migrate
ms.assetid: 5bab5914-b2ae-4795-8cf5-83e42d64bef2
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: acb05f10772ebdf77355b78e1f4ce998cc6c8056
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63453548"
---
# <a name="migration-wizard-accesstosql"></a>移轉精靈 」 (AccessToSQL)
移轉精靈引導您完成移轉的一個或多個資料庫存取權從[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure。 使用精靈，您會建立專案、 將資料庫新增至專案，請選取要移轉，並連接到物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure。 您也會轉換、 載入和存取結構描述和資料移轉。 （選擇性） 您可以在此連結來存取資料表[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 資料表。  
  
大部分的 [移轉精靈] 頁面包含與現有的 SSMA 對話方塊相同的選項。 因此，這裡描述的精靈頁面，以便您可以進一步了解個別的選項，然後提供連結。 如果頁面包含唯一的選項，它們會在此處記錄。  
  
## <a name="starting-the-migration-wizard"></a>啟動移轉精靈  
根據預設，當您啟動 SSMA，會出現 「 移轉精靈 」。 您也可以啟動精靈，在**檔案**功能表中的選取**遷移精靈**。  
  
## <a name="welcome-page"></a>歡迎頁面  
歡迎使用 頁面會介紹 「 移轉精靈 」，並提供下列選項來啟動精靈。  
  
**啟動在啟動此精靈。**  
根據預設，當您啟動 SSMA SSMA 時，會啟動移轉精靈。 若要防止自動啟動精靈，請清除此核取方塊。  
  
## <a name="create-new-project-page"></a>建立新的專案頁面  
建立新的專案頁面是您用來輸入專案的檔案名稱、 位置和移轉專案類型 （以用於移轉的 SQL Server 為目標的版本）。 如需詳細資訊，請參閱[新專案 (SSMA)](https://msdn.microsoft.com/ca294f6d-eeb5-42ca-9306-156281a3f0f3)  
  
## <a name="add-access-databases-page"></a>新增存取 [資料庫] 頁面  
加入 Access 資料庫頁面是您將一或多個 Access 資料庫加入至專案。 您可以新增個別的資料庫，依序按一下**新增的資料庫**，然後選取 從資料庫**開啟**視窗。 或者，您可以使用來尋找資料庫**尋找資料庫** 按鈕。 如需詳細資訊，請參閱下列主題：  
  
-   [新增和移除 Access 資料庫檔案](adding-and-removing-access-database-files-accesstosql.md)  
  
-   [尋找資料庫精靈 （選取位置）](https://msdn.microsoft.com/00b2d32a-998b-47a7-b25c-589b5bd6777a)  
  
-   [尋找資料庫精靈 （選取檔案）](https://msdn.microsoft.com/2f574a34-4bab-40a4-89a8-ad4907ffc3fd)  
  
-   [尋找資料庫精靈 (驗證選取項目)](https://msdn.microsoft.com/62e20e03-50cc-4ac8-8072-524d194d2ec3)  
  
## <a name="select-objects-to-migrate-page"></a>選取要移轉頁面物件  
在 選取要移轉的頁面物件，您可以選取要轉換的物件。 您可以選取所有物件的物件或個別物件的群組。  
  
**若要選取物件**  
  
1.  依序展開**存取 metabase**，然後展開**資料庫**。  
  
2.  請進行下列任一或多項操作：  
  
    -   若要將所有的資料庫轉換，選取核取方塊旁**資料庫**。  
  
    -   若要將轉換或省略個別資料庫，選取或清除資料庫名稱旁邊的核取方塊。  
  
    -   要轉換，或省略查詢，請展開資料庫，然後選取或清除**查詢**核取方塊。  
  
    -   若要轉換，或省略個別資料表，展開資料庫，依序展開**資料表**，然後選取或清除資料表旁邊的核取方塊。  
  
如果您有許多物件時，您可能想要使用**進階物件選取項目**右窗格中的選項來篩選存取資料庫物件。 例如，如果您選取**資料表**在左窗格中，您可以接著篩選的資料表清單輸入字串中的**篩選** 方塊中。 然後，您可以選取或清除 使用窗格頂端的按鈕的 已篩選的資料表移轉。  
  
如需篩選的詳細資訊，請參閱 [選項] 區段的[進階物件選取項目 （SSMA 常見）](https://msdn.microsoft.com/f53b0c79-5473-410a-a0dc-d8f544f7a63c)。  
  
## <a name="connect-to-sql-server-page"></a>連接到 SQL Server 頁面  
在 [連接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]] 頁面上，您指定連接屬性，然後連線至[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 連接到 SQL Server](connect-to-sql-server-accesstosql.md)。
  
> [!IMPORTANT]  
> 一旦連線成功，您將會遇到**連結資料表**頁面，您必須在連結資料表的選項。 按一下 [**下一步]** 並啟動移轉。  
  
## <a name="connect-to-sql-azure-page"></a>連接到 SQL Azure 的頁面  
在 [連接到 SQL Azure] 頁面中，您可以指定連接屬性，然後連接到 SQL Azure。 若要建立新的 azure 資料庫，則可以使用**建立 Azure Database**選項會出現在上按一下**瀏覽** 按鈕。 如需詳細資訊，請參閱[連接到 SQL Azure](connect-to-azure-sql-db-accesstosql.md)  
  
> [!IMPORTANT]  
> 一旦連線成功，您將會遇到**連結資料表**頁面，您必須在連結資料表的選項。 按一下 [**下一步]** 開始移轉 [連結] 頁面上的按鈕。  
  
## <a name="link-tables-page"></a>連結資料表 頁面  
[連結資料表] 頁面可讓您將原始的 Access 資料表連結至移轉[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 資料表。 連結資料表，讓您查詢、 表單、 報表和資料存取頁面使用中的資料會修改您的 Access 資料庫[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 資料庫，而非 Access 資料庫中的資料。  
  
**連結資料表**  
選取 **連結的資料表**核取方塊以 Access 資料表連結至已移轉[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 資料表。 若要開始的移轉，您應該按一下**下一步**  按鈕。  
  
## <a name="migration-status-page"></a>移轉 [狀態] 頁面  
[移轉狀態] 頁面中顯示的轉換來存取結構描述進度[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 結構描述，載入將已轉換的結構描述[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure，然後移轉資料。  
  
如需有關此頁面的詳細資訊，請參閱[轉換、 載入和移轉](https://msdn.microsoft.com/4ec83e96-88a5-4b7b-8d5a-f3429d9a936b)  
  
## <a name="see-also"></a>另請參閱  
[Getting Started with SQL Server 移轉小幫手，存取&#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[將 Access 資料庫移轉至 SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[使用者介面 Reference(Access)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
