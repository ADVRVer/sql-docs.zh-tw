---
title: "載入已轉換成 SQL Server (OracleToSQL) 資料庫物件 |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Synchronization, Securing Objects in SQL Server
- Synchronization,Scripting Objects
ms.assetid: a8ae33b2-1883-4785-922b-ea0e31c0b37a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6fd5616c61af419d5d2ff3134177ae296b317d57
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="loading-converted-database-objects-into-sql-server-oracletosql"></a>載入已轉換成 SQL Server (OracleToSQL) 資料庫物件
Oracle 結構描述轉換至 SQL Server 之後，您可以載入 SQL Server 來產生資料庫物件。 您可以讓 SSMA 建立物件，或您可以編寫物件指令碼，並自行執行指令碼。 此外，SSMA 可讓您更新 SQL Server 資料庫的實際內容目標中繼資料。  
  
## <a name="choosing-between-synchronization-and-scripts"></a>同步處理和指令碼之間選擇  
如果您想要轉換的資料庫物件載入 SQL Server，而不需修改，您可以讓 SSMA 直接建立或重新建立資料庫物件。 方法既快速又簡單，但不允許的自訂[!INCLUDE[tsql](../../includes/tsql_md.md)]定義 SQL Server 物件，預存程序之外的程式碼。  
  
如果您想要修改[!INCLUDE[tsql](../../includes/tsql_md.md)]用來建立物件，或如果您想要更充分掌控物件建立時，使用 SSMA 建立指令碼。 您可以修改這些指令碼、 個別建立每個物件和甚至可以使用 SQL Server Agent 排程建立這些物件。  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>若要同步處理的物件與 SQL Server 使用 SSMA  
若要使用 SSMA 建立 SQL Server 資料庫物件，您在 SQL Server 中繼資料總管 選取的物件，並再同步處理的物件與 SQL Server，如下列程序中所示。 根據預設，如果物件已存在於 SQL Server，而且如果 SSMA 中繼資料是比 SQL Server 中的物件 SSMA 會變更 SQL Server 中的物件定義。 您可以變更預設行為，藉由編輯**專案設定**。  
  
> [!NOTE]  
> 您可以選取現有未轉換從 Oracle 資料庫的 SQL Server 資料庫物件。 不過，這些物件將不會重新建立或更改 SSMA。  
  
**若要同步處理 SQL Server 的物件**  
  
1.  SQL Server 中繼資料總管 中展開最上層的 SQL Server 節點，然後再展開**資料庫**。  
  
2.  選取要處理的物件：  
  
    -   若要同步處理完整的資料庫，請選取資料庫名稱旁邊的核取方塊。  
  
    -   若要同步處理，或省略個別物件或類別目錄的物件，選取或清除的物件或資料夾旁邊的核取方塊。  
  
3.  選取要在 SQL Server 中繼資料總管] 處理的物件之後，以滑鼠右鍵按一下**資料庫**，然後按一下 [**同步處理資料庫**。  
  
    您也可同步個別物件或類別目錄的物件，該物件或其父資料夾上按一下滑鼠右鍵，然後按一下**同步處理資料庫**。  
  
    之後，將會顯示 SSMA**同步處理資料庫**對話方塊中，您可以在其中看到兩個群組的項目。 在左邊，SSMA 會顯示選取的資料庫物件，代表在樹狀目錄中。 在右側，您可以看到代表 SSMA 中繼資料中的相同物件的樹狀結構。 您可以展開樹狀目錄，按一下向左或向 ' +' 按鈕。 放置於兩個樹系之間的 [動作] 欄會顯示同步處理方向。  
  
    動作符號可以是三種狀態：  
  
    -   向左箭號表示中繼資料的內容將會儲存在資料庫 （預設值）。  
  
    -   向右箭號表示資料庫的內容將會覆寫的 SSMA 中繼資料。  
  
    -   跨號表示將會採取任何動作。  
  
按一下動作正負號，以變更狀態。 將會執行實際的同步處理，當您按一下**確定**按鈕**同步處理資料庫**對話方塊。  
  
## <a name="scripting-objects"></a>編寫物件指令碼  
若要儲存[!INCLUDE[tsql](../../includes/tsql_md.md)]轉換的資料庫物件，或要變更的物件定義和執行指令碼自行定義，您可以儲存轉換的資料庫物件定義要[!INCLUDE[tsql](../../includes/tsql_md.md)]指令碼。  
  
**若要儲存物件做為指令碼**  
  
1.  選取要儲存到指令碼的物件之後，以滑鼠右鍵按一下**資料庫**，然後按一下 **將儲存為指令碼**。  
  
    您也可以編寫個別物件或類別目錄的物件，該物件或其父資料夾上按一下滑鼠右鍵，然後按一下**將儲存為指令碼**。  
  
2.  在**另存新檔**對話方塊方塊中，找出您要儲存指令碼中，輸入中的檔案名稱的資料夾**檔案名稱**方塊，然後再按一下 [確定] SSMA 會將附加.sql 檔案的副檔名。  
  
### <a name="modifying-scripts"></a>修改指令碼  
您已儲存的 SQL Server 物件的定義以一個或多個指令碼之後，您可以使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]來檢視和修改指令碼。  
  
**若要修改指令碼**  
  
1.  在[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]**檔案**功能表上，指向**開啟**，然後按一下**檔案**。  
  
2.  在**開啟**對話方塊中，選取您的指令碼檔案，然後按一下 [確定]。
  
3.  使用查詢編輯器，編輯指令碼檔案。  
  
    如需查詢編輯器的詳細資訊，請參閱 「 編輯器便利命令和功能，SQL Server 線上叢書 》 中。  
  
4.  若要儲存指令碼，在 [檔案] 功能表按一下**儲存**。  
  
### <a name="running-scripts"></a>執行指令碼  
您可以在執行指令碼或個別的陳述式， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]。  
  
**執行指令碼**  
  
1.  在[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]**檔案**功能表上，指向**開啟**，然後按一下**檔案**。  
  
2.  在**開啟**對話方塊，並選取您的指令碼檔案，然後按一下 [確定]  
  
3.  若要執行完整的指令碼，請按**F5**索引鍵。  
  
4.  若要執行一組陳述式，選取陳述式在查詢編輯器 視窗，然後按**F5**索引鍵。  
  
如需如何使用查詢編輯器來執行指令碼的詳細資訊，請參閱 「[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)]查詢 「 SQL Server 線上叢書 》 中。  
  
您也可以執行從命令列指令碼，使用**sqlcmd**公用程式，並從 SQL Server Agent。 如需有關**sqlcmd**，請參閱 SQL Server 線上叢書 》 中的 「 sqlcmd 公用程式 」。 如需有關 SQL Server Agent 的詳細資訊，請參閱"自動化管理工作 （SQL Server 代理程式） 「 SQL Server 線上叢書 》 中。  
  
## <a name="securing-objects-in-sql-server"></a>保護 SQL Server 中的物件  
轉換的資料庫物件載入 SQL Server 之後，您可以 grant 和 deny 權限的物件。 最好執行這項操作，然後再移轉到 SQL Server 的資料。 如需如何協助保護物件的 SQL Server 中的資訊，請參閱 「 安全性考量的資料庫和資料庫應用程式"SQL Server 線上叢書 》 中。  
  
## <a name="next-step"></a>下一個步驟  
移轉程序的下一個步驟是[將資料移轉至 SQL Server](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13)。  
  
## <a name="see-also"></a>另請參閱  
[將 Oracle 資料庫移轉至 SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  

