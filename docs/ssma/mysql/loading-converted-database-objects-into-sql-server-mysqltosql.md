---
title: 已轉換的資料庫物件載入至 SQL Server (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ac993a6d-0283-4823-8793-6b217677dfa3
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: a6966209300e6959e7ba9cb1afa11eb42b855d82
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67909009"
---
# <a name="loading-converted-database-objects-into-sql-server-mysqltosql"></a>將轉換的資料庫物件載入 SQL Server (MySQLToSQL)
轉換 MySQL 資料庫之後[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure，您可以載入到產生的資料庫物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure。 您可以讓 SSMA 建立物件，或者您可以編寫物件指令碼，然後自己執行的指令碼。 此外，SSMA 可讓您更新目標中繼資料的實際內容[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 資料庫。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同步處理和指令碼之間進行選擇  
如果您想要轉換之資料庫物件載入至[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure，而不需修改，您可以讓 SSMA 上直接建立或重新建立資料庫物件。 方法既快速又簡單，但不允許自訂定義的 TRANSACT-SQL 程式碼[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 物件。  
  
如果您想要修改用來建立物件，TRANSACT-SQL 或您想要更充分掌控物件建立時，使用 SSMA 建立指令碼。 您可以修改這些指令碼，會個別建立每個物件即使使用 SQL Server Agent 來排程建立這些物件。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>使用 SSMA 與 SQL Server 同步處理物件  
若要使用 SSMA 建立 SQL Server 或 SQL Azure 資料庫物件，您可以選取中的物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 中繼資料總管，然後再同步處理的物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure，如下列程序中所示。 根據預設，如果物件已存在於[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure，而且如果 SSMA 中繼資料有一些本機變更或更新這些非常的物件，定義則 SSMA 會改變中的物件定義[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure。 您可以變更預設行為，藉由編輯**專案設定**。  
  
> [!NOTE]  
> 您可以選取現有的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或未轉換從 MySQL 資料庫的 SQL Azure 資料庫物件。 不過，這些物件將不會重新建立或更改 SSMA。  
  
##### <a name="to-synchronize-objects-with-sql-server-or-sql-azure"></a>若要同步處理的物件，與 SQL Server 或 SQL Azure  
  
1.  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 中繼資料總管，展開最上方[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 節點中，然後展開**資料庫**。  
  
2.  選取要處理的物件：  
  
    -   若要同步處理完整的資料庫，請選取資料庫名稱旁邊的核取方塊。  
  
    -   若要同步處理，或省略個別物件或類別目錄的物件，選取或清除的物件或資料夾旁邊的核取方塊。  
  
3.  選取要在 SQL Server 或 SQL Azure 中繼資料總管 中處理的物件之後，以滑鼠右鍵按一下**資料庫**，然後按一下**同步處理資料庫**。  
  
    您也可同步個別物件或類別目錄的物件，該物件或其父資料夾上按一下滑鼠右鍵，然後按一下**同步處理資料庫**。  
  
    之後，將會顯示的 SSMA**同步處理資料庫**對話方塊中，您可以在其中看到兩個項目群組。 在左側，SSMA 會顯示選取的資料庫物件，表示在樹狀目錄中。 在右側，您可以看到代表 SSMA 中繼資料中的相同物件的樹狀結構。 您可以展開樹狀目錄，按一下向左或向 [+] 按鈕。 放置兩個樹狀結構之間的 [動作] 欄中顯示的同步處理方向。  
  
    動作號可以是下列三種狀態：  
  
    -   向左箭號表示的中繼資料內容會儲存在資料庫 （預設值）。  
  
    -   向右箭號表示資料庫內容將會覆寫的 SSMA 中繼資料。  
  
    -   跨正負號表示將會採取任何動作。  
  
    -   按一下動作正負號，以變更狀態。 當您按一下時，將會執行實際的同步處理 **[確定]** 按鈕**同步處理資料庫**對話方塊。  
  
## <a name="scripting-objects"></a>編寫物件指令碼  
若要儲存[!INCLUDE[tsql](../../includes/tsql-md.md)]定義的轉換後的資料庫物件，或改變的物件定義，然後自己執行指令碼，您可以將儲存已轉換的資料庫物件定義以便[!INCLUDE[tsql](../../includes/tsql-md.md)]指令碼。  
  
**若要將物件儲存為指令碼**  
  
1.  選取要儲存到指令碼的物件之後，以滑鼠右鍵按一下**資料庫**，然後按一下**儲存為指令碼**。  
  
    您也可以編寫個別物件或類別目錄的物件，該物件或其父資料夾上按一下滑鼠右鍵，然後按一下**儲存為指令碼**。  
  
2.  在 [**另存新檔**對話方塊方塊中，找出您想要用來儲存指令碼中，輸入中的檔案名稱的資料夾**檔案名稱**] 方塊中，然後[!INCLUDE[clickOK](../../includes/clickok-md.md)]SSMA 會將.sql 副檔名的附加。  
  
### <a name="modifying-scripts"></a>修改指令碼  
儲存 SQL Server 或 SQL Azure 物件定義做為指令碼之後，您可以使用 SQL Server Management Studio 修改指令碼。  
  
**若要修改指令碼**  
  
1.  在 Management Studio**檔案**功能表上，指向**開放**，然後按一下**檔案**。  
  
2.  在 [開啟] 對話方塊中，找出並選取您的指令碼檔案，然後按一下**確定**。  
  
3.  使用查詢編輯器中編輯指令碼檔案。如需有關查詢編輯器的詳細資訊，請參閱 [編輯器便利命令和功能] SQL Server 線上叢書 》 中。  
  
4.  若要儲存指令碼，在 [檔案] 功能表上，選取**儲存**。  
  
### <a name="running-scripts"></a>執行指令碼  
您可以在 SQL Server Management Studio 中執行指令碼或個別的陳述式。  
  
**若要執行指令碼**  
  
1.  在 SQL Server Management Studio**檔案**功能表上，指向**開放**，然後按一下 **檔案**。  
  
2.  在 [開啟] 對話方塊中，找出並選取您的指令碼檔案，然後按一下**確定**。  
  
3.  若要執行完整的指令碼，請按**F5**索引鍵。  
  
4.  若要執行一組陳述式，選取陳述式在查詢編輯器 視窗，然後按**F5**索引鍵。  
  
5.  如需如何使用查詢編輯器來執行指令碼的詳細資訊，請參閱 「 SQL Server Management Studio Transact SQL 查詢"SQL Server 線上叢書 》 中。  
  
6.  您也可以執行從命令列指令碼，利用**sqlcmd**公用程式，並從 SQL Server Agent。 如需詳細資訊**sqlcmd**，請參閱 SQL Server 線上叢書 》 中的 「 sqlcmd 公用程式 」。 如需有關 SQL Server Agent 的詳細資訊，請參閱 「 自動化系統管理工作 (SQL Server Agent) 」 在 SQL Server 線上叢書 》 中。  
  
## <a name="securing-objects-in-sql-server"></a>保護 SQL Server 中的物件  
轉換的資料庫物件載入 SQL Server 之後，您可以授與和拒絕這些物件的權限。 它是個不錯的主意，若要這樣做之前移轉至 SQL Server 的資料。 如需如何協助保護 SQL Server 中的物件資訊，請參閱 「 安全性考量的資料庫和資料庫應用程式"SQL Server 線上叢書 》 中。  
  
## <a name="next-step"></a>下一個步驟  
移轉程序的下一個步驟是[移轉到 SQL Server-Azure SQL DB 的 MySQL 資料&#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
## <a name="see-also"></a>另請參閱  
[移轉 MySQL 資料庫到 SQL Server-Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
