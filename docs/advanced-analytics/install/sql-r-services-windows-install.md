---
title: 安裝 SQL Server 2016 R 服務 (資料庫內)
description: 為 Windows 上 SQL Server 2016 R Services 上的資料庫引擎新增 R 程式設計語言支援。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 6fcb4245d4efff00002dea9b490312792e0d83d6
ms.sourcegitcommit: b4ad3182aa99f9cbfd15f4c3f910317d6128a2e5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73707000"
---
# <a name="install-sql-server-2016-r-services"></a>安裝 SQL Server 2016 R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

本文說明如何安裝及設定 **SQL Server 2016 R Services**。 如果您有 SQL Server 2016，請安裝此功能以便能夠在 SQL Server 中執行 R 程式碼。

在 SQL Server 2017 中，是在[機器學習服務](../r/r-server-standalone.md)中提供 R 整合，反映了 Python 的新增。 如果您想要 R 整合及擁有 SQL Server 2017 安裝媒體，請參閱[安裝 SQL Server 機器學習服務](sql-machine-learning-services-windows-install.md)來新增該功能。 

<a name="bkmk_prereqs"> </a> 

## <a name="pre-install-checklist"></a>預先安裝檢查清單

+ 需要資料庫引擎執行個體。 您無法只安裝 R，不過可以藉由累加方式將其新增至現有的執行個體。

+ 針對商務持續性，R 服務支援 [Always On 可用性群組](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server)。 您必須在每個節點上都安裝 R 服務，並設定套件。

+ 請勿在容錯移轉叢集上安裝 R 服務。 用來隔離 R 程序的安全性機制與 Windows Server 容錯移轉叢集環境不相容。

+ 請勿在網域控制站上安裝 R 服務。 安裝程式的 R 服務部分將會失敗。

+ 請勿在執行資料庫內執行個體的同一部電腦上安裝 [共用功能]   > [R Server (獨立式)]  。 

  可以與其他版本的 R 和 Python 並存安裝，因為 SQL Server 執行個體使用自己的開放原始碼 R 和 Anaconda 散發套件副本。 不過，在 SQL Server 外的 SQL Server 電腦上執行使用 R 和 Python 的程式碼可能會導致各種問題：
    
  + 與在 SQL Server 中執行時相比，您可以使用不同的程式庫和不同的可執行檔，並取得不同的結果。
  + 在外部程式庫中執行的 R 和 Python 指令碼無法由 SQL Server 管理，因而導致資源競爭。
  
如果您使用任何舊版 Revolution Analytics 開發環境或 RevoScaleR 套件，或已安裝任何 SQL Server 2016 發行前版本，就必須先將它們解除安裝。 不支援執行較舊或較新版本的 RevoScaleR 及其他專屬套件。 如需有關移除舊版的說明，請參閱 [SQL Server 機器學習服務的升級和安裝常見問題集](../r/upgrade-and-installation-faq-sql-server-r-services.md)。

> [!IMPORTANT]
> 安裝完成之後，請務必完成本文中所述的額外設定後步驟。 這些步驟包括讓 SQL Server 使用外部指令碼，以及新增 SQL Server 代替您執行 R 作業所需的帳戶。 設定變更通常需要重新啟動執行個體，或重新啟動啟動控制板服務。

## <a name="get-the-installation-media"></a>取得安裝媒體

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

<a name="bkmk_ga_instalpatch"></a>

 ### <a name="install-patch-requirement"></a>安裝修補程式需求 

Microsoft 發現特定版本的 Microsoft VC++ 2013 Runtime 二進位檔問題，SQL Server 必須安裝這些二進位檔。 如果未安裝 VC Runtime 二進位檔的這項更新，SQL Server 就可能在特定情況下遇到穩定性問題。 安裝 SQL Server 之前，請先遵循 [SQL Server 版本資訊](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)的指示，查看您的電腦是否需要 VC Runtime 二進位檔的修補程式。  

<a name="bkmk2016top"></a>

## <a name="run-setup"></a>執行安裝程式

如果是本機安裝，您必須以管理員身分執行安裝程式。 如果您是從遠端共用位置安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則必須使用對遠端共用位置具有讀取和執行權限的網域帳戶。

1. 啟動 SQL Server 2016 的安裝精靈。

2. 在 [安裝]  索引標籤上，選取 [新增 SQL Server 獨立安裝或將功能加入至現有安裝]  。
    
   ![安裝 R Services (資料庫內)](media/2016-setup-installation-rsvcs.png "開始搭配 R Services 安裝資料庫引擎")
   
3. 在 [特徵選取]  頁面上，選取下列選項：

   - 選取 [資料庫引擎服務]  。 每個使用機器學習的執行個體都需要資料庫引擎。
   - 選取 [R Services (資料庫內)]  。 安裝適用於在資料庫內使用 R 的支援。
    
     ![R Services 特徵選取](media/2016setup-rsvcs-features.png "選取這些適用於 R Services (資料庫內) 的功能")

    > [!IMPORTANT]
    > 請勿同時安裝 R Server 和 R Services。 您通常會安裝 R Server (獨立式) 來建立資料科學家或開發人員用來連線至 SQL Server 並部署 R 解決方案的環境。 因此，不需要在相同的電腦上同時安裝 R Server 和 R Services。

4.  在 [同意安裝 Microsoft R Open]  頁面上，按一下 [接受]  。
  
    此授權合約是下載 Microsoft R Open 的必要合約，其中包含開放原始碼 R 基底套件和工具的散發套件，以及來自 Microsoft R 開發小組的增強型 R 套件和連接提供者。
  
5. 接受授權合約之後，在準備安裝程式時會有短暫的暫停。 當 [下一步]  按鈕變成可用時，按一下該按鈕。

6. 在 [準備安裝]  頁面上，確認包含下列項目，然後選取 [安裝]  。

   + Database Engine 服務
   + R Services (資料庫內)

    請注意組態檔儲存所在資料夾 (路徑 `..\Setup Bootstrap\Log` 底下) 的位置。 當安裝程式完成時，您可以在摘要檔案中檢閱已安裝的元件。

7. 在安裝程式完成之後，如果系統要求您重新啟動電腦，請立即重新啟動。 當您完成安裝時，請務必閱讀安裝精靈所提供的訊息。 如需詳細資訊，請參閱＜ [View and Read SQL Server Setup Log Files](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files)＞。

## <a name="set-environment-variables"></a>設定環境變數

僅針對 R 功能整合，您應該設定 **MKL_CBWR** 環境變數，以確保來自 Intel Math Kernel Library (MKL) 計算的輸出[會保持一致](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) \(英文\)。

1. 在 [控制台] 中，按一下 [系統及安全性]   > [系統]   > [進階系統設定]   > [環境變數]  。

2. 建立新的使用者或系統變數。 

  + 將變數名稱設定為 `MKL_CBWR`
  + 將變數值設定為 `AUTO`

此步驟需要重新啟動伺服器。 如果您即將啟用指令碼執行，則可以推遲重新啟動，直到完成所有設定工作為止。

<a name="bkmk_enableFeature"></a>

##  <a name="enable-script-execution"></a>啟用指令碼執行

1. 開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。 

    > [!TIP]
    > 您可以從這個頁面下載並安裝適當的版本：[下載 SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > 您也可以使用 [Azure Data Studio](../../azure-data-studio/what-is.md)，它支援針對 SQL Server 的系統管理工作與查詢。
  
2. 連線到您安裝機器學習服務的執行個體，按一下 [新增查詢]  開啟查詢視窗，然後執行下列命令：

   ```sql
   sp_configure
   ```
    屬性 `external scripts enabled` 的值目前應該為 **0**。 這是因為該功能預設是關閉的。 系統管理員必須明確地啟用該功能，您才能執行 R 或 Python 指令碼。
     
3. 若要啟用外部指令碼功能，請執行下列陳述式：
  
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>重新啟動服務

當安裝完成時，請先重新啟動資料庫引擎，然後再繼續執行下一步，以啟用指令碼執行。

重新啟動服務也會自動重新啟動相關的 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] 服務。

您可以針對 SSMS 中的執行個體，使用滑鼠右鍵按一下 [重新啟動]  命令，或使用 [控制台] 中的 [服務]  面板，或使用 [SQL Server 組態管理員](../../relational-databases/sql-server-configuration-manager.md)來重新啟動服務。

## <a name="verify-installation"></a>確認安裝

使用[自訂報表](../r/monitor-r-services-using-custom-reports-in-management-studio.md)來檢查執行個體的安裝狀態。

使用下列步驟確認用於啟動外部指令碼的所有元件都正在執行。

1. 在 SQL Server Management Studio 中，開啟新的 [查詢] 視窗，並執行下列命令︰
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    **run_value** 現在應該設定為 1。

2. 開啟 [服務]  面板或 SQL Server 組態管理員，並確認 **SQL Server Launchpad 服務**正在執行。 您應該為每個安裝 R 或 Python 的資料庫引擎執行個體都提供一個服務。 如需服務的詳細資訊，請參閱[擴充性架構](../concepts/extensibility-framework.md)。

7. 如果 Launchpad 正在執行，您應該能夠執行簡單 R 來確認外部指令碼執行階段可以與 SQL Server 通訊。 

    在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中開啟新的 [查詢]  視窗，然後執行如下所示的指令碼：
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    第一次載入外部指令碼執行階段時，該指令碼可能需要一些時間才能執行。 結果應該類似這樣：

    | hello |
    |----|
    | 1|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>套用更新

我們建議您將最新的累積更新套用至資料庫引擎和機器學習元件。

在連線到網際網路的裝置上，累積更新通常會透過 Windows Update 套用，但您也可以使用下列步驟來進行受控制的更新。 當您套用資料庫引擎的更新時，安裝程式會針對您在相同執行個體上安裝的 R 程式庫提取累積更新。 

在中斷連線的伺服器上，需要額外的步驟。 如需詳細資訊，請參閱[在沒有網際網路存取的電腦上安裝 > 套用累積更新](sql-ml-component-install-without-internet-access.md#apply-cu)。

1. 從已經安裝的基準執行個體開始：SQL Server 2016 初始版本、SQL Server 2016 SP 1 或 SQL Server 2016 SP 2。

2. 移至累積更新清單：[SQL Server 2016 更新](https://sqlserverupdates.com/sql-server-2016-updates/) \(英文\)

3. 選取最新的累積更新。 可執行檔會自動下載並解壓縮。

4. 執行安裝程式。 接受授權條款，然後在 [特徵選取] 頁面上，檢閱已套用累積更新的功能。 您應該會看到針對目前執行個體安裝的每個功能，包括 R Services。 安裝程式會下載更新所有功能所需的 CAB 檔案。

5. 繼續執行精靈，並接受 R 散發套件的授權條款。 

<a name="bkmk_FollowUp"></a> 

## <a name="additional-configuration"></a>其他組態

如果外部指令碼驗證步驟成功，您就可以從 SQL Server Management Studio、Visual Studio Code 或任何其他可以將 T-SQL 陳述式傳送到伺服器的用戶端，執行 Python 命令。

如果您在執行命令時遇到錯誤，請檢閱此節中的其他設定步驟。 您可能需要對服務或資料庫進行其他適當的設定。

在執行個體層級，其他設定可能包括：

* [SQL Server 機器學習服務的防火牆設定](../../advanced-analytics/security/firewall-configuration.md)
* [啟用其他網路通訊協定](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [啟用遠端連線](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [管理磁碟配額](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas)，以避免外部指令碼執行耗盡磁碟空間的工作

<a name="bkmk_configureAccounts"></a>
<a name="bkmk_AllowLogon"></a>

在資料庫上，您可能需要下列設定更新：

* [授與使用者 SQL Server 機器學習服務的權限](../../advanced-analytics/security/user-permission.md)
* [新增 SQLRUserGroup 作為資料庫使用者](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)

> [!NOTE]
> 並非所有列出的變更都是必要的，且可能不需要任何變更。 需求取決於您的安全性結構描述、SQL Server 的安裝位置，以及預期使用者如何連線至資料庫並執行外部指令碼。 如需其他疑難排解秘訣，請參閱這裡：[升級及安裝常見問題集](../r/upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="suggested-optimizations"></a>建議的最佳化

既然一切正常，您可能還需要最佳化伺服器以支援機器學習，或安裝預先定型模型。

### <a name="add-more-worker-accounts"></a>新增更多背景工作帳戶

如果您認為自己可能經常使用 R，或預期會有許多使用者同時執行指令碼，您可以增加指派給 Launchpad 服務的背景工作帳戶數目。 如需詳細資訊，請參閱[修改 SQL Server 機器學習服務的使用者帳戶集區](../administration/modify-user-account-pool.md)。

<a name="bkmk_optimize"></a>

### <a name="optimize-the-server-for-external-script-execution"></a>將伺服器最佳化以執行外部指令碼

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式的預設設定是為了最佳化伺服器的平衡，以處理資料庫引擎支援的各種服務，其中可能包含解壓縮、轉換和載入 (ETL) 程序、報告、稽核，以及使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料的應用程式。 因此，在預設設定下，您可能會發現機器學習的資源有時會受到限制或遭遇瓶頸，尤其是需要大量記憶體的作業。

為確保機器學習優先處理且獲得適當的資源，建議您使用 SQL Server 資源管理員設定外部資源集區。 您也可能想要變更配置給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫引擎的記憶體量，或增加 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] 服務下所執行的帳戶數目。

- 若要設定用來管理外部資源的資源集區，請參閱[建立外部資源集區](../../t-sql/statements/create-external-resource-pool-transact-sql.md)。
  
- 若要變更為資料庫保留的記憶體量，請參閱[伺服器記憶體設定選項](../../database-engine/configure-windows/server-memory-server-configuration-options.md)。
  
- 若要變更 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] 可以啟動的 R 帳戶數目，請參閱[修改機器學習的使用者帳戶集區](../administration/modify-user-account-pool.md)。

如果您使用標準版且沒有 Resource Governor，則可以使用「動態管理檢視」(DMV) 和「擴充事件」，以及 Windows 事件監視，來協助管理 R 所使用的伺服器資源。如需詳細資訊，請參閱[監視和管理 R Services](../r/managing-and-monitoring-r-solutions.md)。

### <a name="install-additional-r-packages"></a>安裝其他 R 套件

您為 SQL Server 建立的 R 解決方案可以呼叫基本 R 函式、與 SQL Server 一起安裝之專屬套件中的函式，以及與 SQL Server 所安裝的開放原始碼 R 版本相容的協力廠商 R 套件。

您想要從 SQL Server 使用的套件，必須安裝在執行個體所使用的預設程式庫中。 如果您在電腦上有分開安裝的 R，或您將套件安裝到使用者程式庫，則無法從 T-SQL 使用這些套件。

安裝和管理 R 套件的程序在 SQL Server 2016 與 SQL Server 2017 中有所不同。 在 SQL Server 2016 中，資料庫管理員必須安裝使用者所需的 R 套件。 在 SQL Server 2017 中，您可以將使用者群組設定為在每個資料庫層級上共用套件，或設定資料庫角色以讓使用者安裝自己的套件。 如需詳細資訊，請參閱[安裝新的 R 套件](../r/install-additional-r-packages-on-sql-server.md)。

## <a name="next-steps"></a>後續步驟

R 開發人員可以從一些簡單的範例開始，並了解 R 如何搭配 SQL Server 使用的基本概念。 如需下一個步驟，請參閱下列連結：

+ [教學課程：在 T-SQL 中執行 R](../tutorials/quickstart-r-create-script.md)
+ [教學課程：適用於 R 開發人員的資料庫內分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

若要檢視以真實世界案例為基礎的機器學習範例，請參閱[機器學習服務教學課程](../tutorials/machine-learning-services-tutorials.md)。