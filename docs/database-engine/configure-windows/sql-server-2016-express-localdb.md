---
title: SQL Server 2016 Express LocalDB | Microsoft Docs
ms.custom: 
ms.date: 08/10/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user instances
- LocalDB, described
- local database runtime
- file database
- LocalDB
ms.assetid: 5a641a46-7cfb-4d7b-a90d-6e4625719d74
caps.latest.revision: 42
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 64d008b25aacd5ad76b711662f9b6ffd3e5e5926
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-2016-express-localdb"></a>SQL Server 2016 Express LocalDB

 > 如需舊版 SQL Server 的相關內容，請參閱 [SQL Server 2014 Express LocalDB](https://msdn.microsoft.com/en-US/library/hh510202(SQL.120).aspx)。

Microsoft SQL Server 2016 Express **LocalDB** 是 [SQL Server Express](https://msdn.microsoft.com/library/ms144275(SQL.130).aspx) 的功能，專供開發人員使用。 SQL Server 2016 Express with Advanced Services 中也會提供。  

 **LocalDB** 安裝會複製啟動 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]所需的最少檔案。 安裝 LocalDB 後，您可以使用特殊連接字串來起始連線。 連接時，就會自動建立及啟動必要的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基礎結構，應用程式不需複雜的組態工作即可開始使用資料庫。 Developer Tools 為開發人員提供 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，讓他們撰寫和測試 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，而不需要管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的完整伺服器執行個體。 
 
 
 ## <a name="try-it-out"></a>現在就試試看！ 
  
-   若要下載並安裝 SQL Server 2016 Express，請移至 **[SQL Server 下載](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)**。 LocalDB 是您在安裝期間選取的功能，而且可以在下載媒體時使用。 如果您下載媒體，請選擇 [Express Advanced] 或 [LocalDB] 套件。 
  
-   有 Azure 帳戶嗎？  接著前往 **[這裡](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/)** ，來加速已安裝 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 的虛擬機器。  
  
## <a name="install-localdb"></a>安裝 LocalDB  
 透過安裝精靈或使用 SqlLocalDB.msi 程式來安裝 **LocalDB** 。 **LocalDB** 是安裝 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] 時的選項。 
 
在安裝期間，您可以在 [功能選擇/共用功能] 頁面上選取 [LocalDB]。 每個主要 **版本只能有** LocalDB [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 二進位檔案的一個安裝。 多個 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 處理序可以啟動，而且全部都會使用相同的二進位檔案。 以 LocalDB [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 方式啟動的 **LocalDB** 執行個體與 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]  

 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] **LocalDB** 的執行個體是使用 **SqlLocalDB.exe** 公用程式來管理。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] **LocalDB** 應該用來取代已被取代的 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 使用者執行個體功能。 
  
## <a name="description"></a>描述  
 **LocalDB** 安裝程式使用 SqlLocalDB.msi 程式在電腦上安裝必要的檔案。 在安裝後， **LocalDB** 就是可建立及開啟 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。 資料庫的系統資料庫檔案儲存在使用者本機上通常處於隱藏狀態的 AppData 路徑。 例如 **C:\Users\\<使用者\>\AppData\Local\Microsoft\Microsoft SQL Server Local DB\Instances\LocalDBApp1\\**。 使用者資料庫檔案儲存在使用者指定的位置，通常是在 **C:\Users\\<使用者\>\Documents\\** 資料夾中的某個位置。  
  
 如需在應用程式中併入 **LocalDB** 的詳細資訊，請參閱 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 文件：[Local Data Overview](http://msdn.microsoft.com/library/ms233817\(VS.110\).aspx) (本機資料概觀)、[Walkthrough: Creating a SQL Server LocalDB Database](http://msdn.microsoft.com/library/ms233763\(VS.110\).aspx) (逐步解說：建立 SQL Server LocalDB 資料庫) 與 [Walkthrough: Connecting to Data in a SQL Server LocalDB Database (Windows Forms)](http://msdn.microsoft.com/library/ms171890\(VS.110\).aspx) (逐步解說：連接至 SQL Server LocalDB 資料庫中的資料 (Windows Form))。  
  
 如需有關 **LocalDB** API 的詳細資訊，請參閱＜ [SQL Server Express LocalDB 執行個體 API 參考](http://msdn.microsoft.com/library/hh234692\(SQL.110\).aspx) ＞和＜ [LocalDBStartInstance 函數](http://msdn.microsoft.com/library/hh217143\(SQL.110\).aspx)＞。  
  
 SqlLocalDb 公用程式可以建立 **LocalDB**的新執行個體，啟動及停止 **LocalDB**執行個體，並包含協助您管理 **LocalDB**的選項。  如需 SqlLocalDb 公用程式的詳細資訊，請參閱 [SqlLocalDB 公用程式](../../tools/sqllocaldb-utility.md)。  
  
 **LocalDB** 的執行個體定序設定為 SQL_Latin1_General_CP1_CI_AS，無法變更。 通常支援資料庫層級、資料行層級和運算式層級定序。 自主資料庫遵循 [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md)所定義的中繼資料和 tempdb 定序規則。  
  
### <a name="restrictions"></a>限制  
 **LocalDB** 不得為合併式複寫訂閱者。  
  
 **LocalDB** 不支援 FILESTREAM。  
  
 **LocalDB** 針對 Service Broker 只允許本機佇列。  
  
 內建帳戶 (例如 NT AUTHORITY\SYSTEM) 所擁有的 **LocalDB** 執行個體，可能因為 Windows 檔案系統重新導向而會有管理能力問題。請改為使用一般 Windows 帳戶作為擁有者。  
  
### <a name="automatic-and-named-instances"></a>自動和具名執行個體  
 **LocalDB** 支援兩種類型的執行個體：自動執行個體和具名執行個體。  
  
-   **LocalDB** 自動執行個體是公用的。 這些執行個體會自動為使用者建立及管理，並且可供任何應用程式使用。 使用者電腦上安裝的每一個 **LocalDB** 版本各存在一個 **LocalDB** 自動執行個體。 **LocalDB** 自動執行個體提供順暢的執行個體管理。 無需建立執行個體，它就會運作。 這允許應用程式輕鬆安裝和移轉到另一部電腦。 如果目標電腦已安裝指定的 **LocalDB** 版本，該目標電腦可以使用此版本的 **LocalDB** 自動執行個體。 **LocalDB** 自動執行個體的執行個體名稱採用屬於保留命名空間的特殊模式。 這麼做可避免與 **LocalDB**具名執行個體發生名稱衝突。 自動執行個體的名稱是 **MSSQLLocalDB**。  
  
-   **LocalDB** 具名執行個體是私用的。 這些執行個體是由負責建立及管理該執行個體的單一應用程式所擁有。 具名執行個體與其他執行個體隔離，並透過減少與其他資料庫使用者的資源競爭來提高效能。 具名執行個體必須由使用者透過 **LocalDB** 管理 API 以明確的方式建立，或透過 Managed 應用程式的 app.config 檔案以隱含的方式建立 (儘管需要時 Managed 應用程式也可以使用此 API)。 每個 **LocalDB** 具名執行個體都有相關聯的 **LocalDB** 版本，指向各自的 **LocalDB** 二進位檔案集。 **LocalDB** 執行個體名稱是 **sysname** 資料類型，最多可以包含 128 個字元 (這不同於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的一般具名執行個體，其名稱限制為 16 個 ASCII 字元的一般 NetBIOS 名稱)。**LocalDB** 執行個體名稱可以在檔案名稱內包含任何合法的 Unicode 字元。  使用自動執行個體名稱的具名執行個體會成為自動執行個體。  
  
 電腦的不同使用者可有同名的執行個體。 每個執行個體都是以不同使用者身分執行的不同處理序。  
  
## <a name="shared-instances-of-localdb"></a>LocalDB 的共用執行個體  
 為了支援電腦的多個使用者需要連接到單一 **LocalDB**執行個體的案例， **LocalDB** 支援執行個體共用。 執行個體擁有者可以選擇允許電腦上的其他使用者連接到他的執行個體。 **LocalDB** 自動執行個體和具名執行個體都可以共用。 若要共用 **LocalDB** 執行個體，使用者必須為它選取共用名稱 (別名)。 因為電腦上的所有使用者都可以看到共用名稱，此共用名稱在電腦上必須是唯一的。 **LocalDB** 執行個體的共用名稱與 **LocalDB**具名執行個體具有相同的格式。  
  
 僅電腦上的系統管理員可以建立 **LocalDB**共用執行個體。 **LocalDB** 共用執行個體可由系統管理員或 **LocalDB**共用執行個體的擁有者取消共用。 若要共用及取消共用 **LocalDB**執行個體，請使用 `LocalDBShareInstance` LocalDB `LocalDBUnShareInstance` API 的 **和** 方法，或 SqlLocalDb 公用程式的共用和取消共用選項。  
  
## <a name="starting-localdb-and-connecting-to-localdb"></a>啟動 LocalDB 以及連接到 LocalDB  
  
### <a name="connecting-to-the-automatic-instance"></a>連接到自動執行個體  
 使用 **LocalDB** 最簡單的方式是透過連接字串 **"Server=(localdb)\MSSQLLocalDB;Integrated Security=true"**連接到目前使用者所擁有的自動執行個體。 若要使用檔案名稱來連接到特定的資料庫，請使用類似於 **"Server=(LocalDB)\MSSQLLocalDB; Integrated Security=true ;AttachDbFileName=D:\Data\MyDB1.mdf"**的連接字串進行連接。  
  
> [!NOTE]  
>  電腦使用者初次嘗試連接至 **LocalDB**時，自動執行個體必須已建立及啟動。 建立執行個體所需的額外時間可能會導致連接嘗試失敗並顯示逾時訊息。 發生這種情況時，請等候幾秒鐘，讓建立程序完成，然後再重新連接。  
  
### <a name="creating-and-connecting-to-a-named-instances"></a>建立及連接到具名執行個體  
 除了自動執行個體之外， **LocalDB** 也支援具名執行個體。 您可以使用 SqlLocalDB.exe 程式來建立、啟動及停止 **LocalDB**的具名執行個體。 如需 SqlLocalDB.exe 的詳細資訊，請參閱 [SqlLocalDB 公用程式](../../tools/sqllocaldb-utility.md)。  
  
```ms-dos  
REM Create an instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" create LocalDBApp1  
REM Start the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" start LocalDBApp1  
REM Gather information about the instance of LocalDB  
"C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe" info LocalDBApp1  
```  
  
 以上最後一行傳回的資訊如下所示。  
  
|||  
|-|-|  
|名稱|"LocalDBApp1"|  
|Version|\<目前版本>|  
|共用名稱|""|  
|擁有者|"\<您的 Windows 使用者>"|  
|自動建立|否|  
|State|執行中|  
|上次啟動時間|\<日期和時間>|  
|執行個體管道名稱|np:\\\\.\pipe\LOCALDB#F365A78E\tsql\query|  
  
> [!NOTE]  
>  如果應用程式使用 .NET 4.0.2 之前的版本，您必須直接連接到 **LocalDB**的具名管道。 執行個體管道名稱值是 **LocalDB** 執行個體接聽所在的具名管道。 執行個體管道名稱中 LOCALDB# 後面的部分會隨著每次 **LocalDB** 執行個體啟動而變更。 若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 連接到 **LocalDB** 執行個體，請在 [連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]] 對話方塊的 [伺服器名稱] 方塊中，輸入執行個體管道名稱。 從您的自訂程式，您可以使用類似於 **LocalDB** LocalDB `SqlConnection conn = new SqlConnection(@"Server=np:\\.\pipe\LOCALDB#F365A78E\tsql\query");`  
  
### <a name="connecting-to-a-shared-instance-of-localdb"></a>連接到 LocalDB 的共用執行個體  
 若要連接到 **LocalDB** 共用執行個體，請在連接字串中加入 **所需的最少檔案。\\** 在連接字串中加入 (點 + 反斜線)，以參考保留給共用執行個體的命名空間。 例如，若要連接到名稱為  的 LocalDB `AppData` 共用執行個體，請使用連接字串，例如 `(localdb)\.\AppData` ，做為連接字串的一部分。 使用者若要連接到他們並未擁有的 **LocalDB** 共用執行個體，則必須有 Windows 驗證或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入。  
  
## <a name="troubleshooting"></a>疑難排解  
 如需有關疑難排解 **LocalDB**的詳細資訊，請參閱＜ [疑難排解 SQL Server 2012 Express LocalDB](http://social.technet.microsoft.com/wiki/contents/articles/4609.aspx)＞。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)]**LocalDB** 執行個體是使用者建立、專供其使用的執行個體。 電腦上的任何使用者都可以使用 **LocalDB**執行個體建立資料庫、在其使用者設定檔之下儲存檔案，並在其認證之下執行此處理序。 根據預設，對 **LocalDB** 執行個體的存取只限其擁有者。 **LocalDB** 中所容納的資料受到資料庫檔案之檔案系統存取的保護。 如果使用者資料庫檔案儲存在共用位置，擁有該位置之檔案系統存取權的任何人都可以使用其擁有的 **LocalDB** 執行個體開啟資料庫。 如果資料庫檔案位於受保護的位置，例如使用者資料夾，則只有該使用者和擁有該資料夾存取權的任何系統管理員才可以開啟資料庫。 **LocalDB** 檔案一次只能由一個 **LocalDB** 執行個體開啟。  
  
> [!NOTE]  
>  **LocalDB** 永遠都會在使用者安全性內容之下執行，也就是說， **LocalDB** 絕對不會使用本機系統管理員群組的認證執行。 這表示， **LocalDB** 執行個體使用的所有資料庫檔案都必須可使用擁有使用者的 Windows 帳戶加以存取，而不必考量本機系統管理員群組的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [SqlLocalDB 公用程式](../../tools/sqllocaldb-utility.md)  
  
  

