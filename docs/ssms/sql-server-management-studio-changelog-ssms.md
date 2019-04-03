---
title: SQL Server Management Studio - 變更記錄 (SSMS) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b9ee0c683c151a0edb8f8450d6d9bfbf901ae0b7
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658452"
---
# <a name="sql-server-management-studio---changelog-ssms"></a>SQL Server Management Studio - Changelog (SSMS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

本文提供目前版本和舊版本之 SSMS 的更新、改善和 Bug 修正詳細資料。 下載[舊版 SSMS](#previous-ssms-releases)。


## <a name="ssms-180-rc1download-sql-server-management-studio-ssmsmd"></a>[SSMS 18.0 (RC1)](download-sql-server-management-studio-ssms.md)

組建編號：15.0.18098.0<br>
發行日期：2019 年 3 月 28 日

候選版 1 (RC1) 是 SSMS 18.0 的最新公開預覽版。 如需 SSMS 的最新正式運作 (GA) 版本，請[下載並安裝 SSMS 17.9.1](#ssms-1791-latest-ga-release)。

### <a name="whats-new-in-rc1"></a>RC1 的新功能

本節列出 SSMS 18.0 RC1 的新功能。 如需 SSMS 17.9.1 以後的完整變更記錄，請參閱 [SSMS 18.0 Preview - 至 RC1 為止的累積變更記錄](#ssms-180-preview---cumulative-changelog-through-rc1)。

**SSMS 的改進**

- 啟用 Power Bi 資料集的 XMLA 端點連線。 XMLA 端點可讓您存取 Power BI 服務中的 Analysis Services 引擎。 這可讓 SSMS 和 SQL Profiler 之類的工具連線到 Power BI 資料集，以進行監視、管理、偵錯等作業。如需詳細資訊，請參閱 [XMLA 端點連線](https://go.microsoft.com/fwlink/?linkid=2085204)。

- **SMO**
  - 已在 SMO 和 SSMS 中新增「邊緣條件約束」的串聯刪除支援。
  - 已新增資料分類「讀取-寫入」權限的支援。

- **稽核檔案**
  - 已更新已知的稽核動作清單，而納入 FEATURE RESTRICTION ADD/CHANGE GROUP/DROP。

### <a name="bug-fixes"></a>錯誤修正

- **一般 SSMS**
  - 已修正使用者識別碼屬於多個租用戶時無法進行 MFA 驗證的問題。
  - 已修正效能儀表板報表會報告在子報表中找不到的 PAGELATCH 和 PAGEIOLATCH 等候的問題。

- **SSMS 編輯器**
  - 已修正有數個系統檢視和資料表值函式未正確以色彩標示的問題。

- **物件總管**
  - 已在物件總管篩選中新增適當的逸出。 如需詳細資訊，請參閱 [Azure 意見反應 36678803](https://feedback.azure.com/forums/908035/suggestions/36678803)。

- **SMO**
  - 已修正 GetDbComparer 會將所有 Azure 資料庫的定序不正確地預設為 CI 的問題。

- **受控執行個體支援**
  - 已改善受控執行個體伺服器的特定屬性 (硬體世代、服務層、已使用和保留的儲存體) 的顯示方式。

- **Azure SQL Database**
  - 已修正服務等級目標 (SLO) 會硬式編碼而導致 SSMS 難以支援較新 SQL Azure SLO 的問題。 現在，使用者可以登入 Azure，並且讓 SSMS 擷取所有適用的 SLO 資料 (版本和大小上限)。

- **結果方格**
  - 已修正在按一下方格時會導致「索引超出範圍」例外狀況的問題。
  - 已修正方格結果背景色彩遭到忽略的問題。 如需詳細資訊，請參閱 [Azure 意見反應 32895916](https://feedback.azure.com/forums/908035/suggestions/32895916)。

- **分析工具**
  - 已修正導致 SQL Profiler 無法在 Windows 7 SP1 上啟動的問題。

- **執行程序表**
  - 已在實際執行 XML 計畫的 RunTimeCountersPerThread 中新增下列 4 個屬性：HpcRowCount (HPC 裝置所處理的資料列數目)、HpcKernelElapsedUs (等候使用中核心執行的經過時間)、HpcHostToDeviceBytes (從主機傳輸至裝置的位元組數) 和 HpcDeviceToHostBytes (從裝置傳輸至主機的位元組數)。

- **資料層應用程式精靈**
  - 已修正使用者因為對伺服器的存取受到限制 (例如，無法存取相同伺服器上的所有資料庫) 而無法匯入資料層應用程式 (.dacpac) 的問題。
  - 已修正在多個資料庫裝載於相同的 Azure SQL 伺服器時會導致匯入極度緩慢的問題。

### <a name="deprecated-features"></a>已被取代的功能

- 已移除靜態資料遮罩 (預覽) 功能。

### <a name="known-issues"></a>已知問題

- 不適用

## <a name="ssms-180-preview---cumulative-changelog-through-rc1"></a>SSMS 18.0 Preview - 至 RC1 為止的累積變更記錄

若沒有 *Preview 5*、*Preview 6* 或 *Preview 7* 或 *RC1* 標籤，表示變更是出現在我們的第一個 SSMS 18.0 公開預覽版中，即 SSMS 18.0 *preview 4*。

### <a name="whats-new"></a>新功能

- **SSMS**
  - 較小的下載大小
    - 目前的套件組合大小不到 SSMS 17.x 大小的一半 (~400 MB)。 當您將 IS 元件新增回 SSMS 時，此大小最終會成長一些，但不應該像之前一樣大。
  - SSMS 是以新的 VS 2017 獨立 Shell 為基礎
    - 這意味著新式的 Shell (我們挑選的是 VS 2017 15.6.4)。 新的 Shell 會解除鎖定所有修復 SSMS 和 Visual Studio 的協助工具修正程式。
  - SSMS 協助工具改善
    - 為了解決所有工具 (SSMS、DTA 和分析工具) 中的協助工具問題，我們進行了大量的工作
  - SSMS 可以安裝在自訂資料夾中
    - 目前，這只適用於命令列安裝。 請將這個額外的引數傳遞給 SSMS-Setup-ENU.exe：
      - SSMSInstallRoot=C:\MySSMS18
      - 根據預設，新的 SSMS 安裝位置是：
      - %ProgramFiles(x86)%\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe
      - 注意：這並不表示 SSMS 是多重執行個體。
  - SSMS 不再與 SQL 引擎共用元件
    - 我們做了很多努力來避免與 SQL 引擎共用元件時，通常會導致某一方覆寫另一方所安裝檔案的服務性問題。
  - SSMS 需要 NetFx 4.7.2 或更新版本
    - 我們將最低需求從 NetFx4.6.1 升級至 NetFx4.7.2：這可讓我們善用新架構所公開的新功能。
  - Windows 8 和 Windows Server 2012 不支援 SSMS；Windows 10/Windows Server 2016 至少需要 1607 版 (10.0.14393)
    - 由於 NetFx 4.7.2 的新相依性之故，SSMS 18.0 不會安裝在 Windows 8、Windows Server 2012 以及舊版 Windows 10 和 Windows Server 2016 上。 這些 OS 將封鎖 SSMS 安裝程式。 注意:"Windows 8.1" 仍然受到支援。
  - SSMS 不會新增至 PATH 環境變數
    - SSMS.EXE (和一般工具) 的路徑不再新增至路徑中。 使用者可以自行新增；或者，可以在新式 Windows 上仰賴 [開始] 功能表。
  - SQL Server SQL2019 支援
    - 這是第一個完整「感知」SQL Server 2019 (compatLevel 150 等) 的 SSMS 版本
    - 支援 SQLSERVER2018 中的 "BATCH_STARTED_GROUP" 和 "BATCH_COMPLETED_GROUP"，以及 SSMS 中的受控執行個體
    - UDF 內嵌的 SMO 支援
    - GraphDB：在 Graph TC 序列的執行程序表中新增旗標
    - Always Encrypted：新增 AEv2/記憶體保護區支援
    - Always Encrypted：當使用者按一下 [選項] 按鈕來啟用/設定記憶體保護區支援時，連線對話方塊會有新的索引標籤 [Always Encrypted]。
  - 開發 SSMS 延伸模組不再需要套件識別碼
    - 在過去，SSMS 選擇性地只載入已知套件，因此需要開發人員註冊他們自己的套件。 現已不再是如此。
  - 預設會啟用對高 DPI 的支援
  - 改善 Azure SQL Database 支援
  - SLO/Edition/MaxSize 資料庫屬性現在可接受自訂名稱，讓您更輕鬆地支援未來版本的 SQL Azure 資料庫
  - 新增對最近所新增虛擬核心 SKU (一般用途和商務關鍵) 的支援：Gen4_24 及所有 Gen5。
  - 在 SSMS 中公開檔案群組的 AUTOGROW_ALL_FILES 設定選項
  - 從 SSMS GUI 移除具風險的 [輕量型共用] 和 [優先權提升] 選項 (如需詳細資料，請參閱 https://blogs.msdn.microsoft.com/arvindsh/2010/01/26/priority-boost-details-and-why-its-not-recommended/)
  - SQL 編輯器接受 CTRL+D 快速鍵來複製行 (如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32896594)
  - 用來建立檔案的新功能表和按鍵繫結關係：CTRL+ALT+N。 CTRL+N 會繼續建立新的查詢。 注意：如果您要從 "SSMS 18.0 Preview 1" 移轉，則必須從 [工具] | [匯入匯出設定] | [重設所有設定] 重設使用者設定。
  - [新增防火牆規則] 對話方塊現在可讓使用者指定規則名稱，而不是代替使用者自動產生規則 (如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32902039)=
  - 資料分類：更新建議
  - 專為 v140 T-SQL 改善了編輯器中的 IntelliSense
  - 在 [定序] 對話方塊上新增 SSMS UI 的 UTF-8 支援。
  - 針對連線對話方塊的 MRU 密碼，切換到「Windows 認證管理員」。 這可解決密碼持續性不總是可靠的長時間待處理問題。 如需詳細資訊，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32896486。
  - 確保在預期的監視器上顯示越來越多的對話方塊和視窗，藉以改善對多個監視器系統的支援。
  - 在 [伺服器屬性] 對話方塊的新 [資料庫設定] 頁面中公開 [備份總和檢查碼預設] 伺服器設定。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/34634974
  - [Preview 5 的新功能] 在 [設定 SQL Server 錯誤記錄檔] 下公開 [錯誤記錄檔大小上限]。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035/suggestions/33624115 
  - [Preview 6 的新功能] 在 [工具] 功能表下新增 [移轉到 Azure] - 我們已整合 [Database Migration Assistant](https://aka.ms/get-dma) 與 [Azure 資料庫移轉服務](https://aka.ms/get-dms)，可讓您快速輕鬆地存取，以協助加速移轉到 Azure。
  - [Preview 6 的新功能] 舊版 SSMS 18.0 (< Preview 6) 具有 [可用的資料庫] 快速鍵，其繫結至 **CTRL+ALT+J**。 在 Preview 6 和更新版本中，按鍵繫結關係已還原至 **CTRL+U**，如同 SSMS 17.x。
  - [Preview 6 的新功能] 新增邏輯以提示使用者在使用 [變更連線] 時認可已開啟的交易。
  - [Preview 7 的新功能] 新增 `UTF8_BIN2` 定序的支援。

- **SMO**
  - 擴充建立可繼續索引的 SMO 支援
  - 在 SMO 物件 ("PropertyMissing") 上新增新事件，以協助應用程式作者更快偵測到 SMO 的效能問題。  
  - 在 Configuration 物件上公開新的 DefaultBackupChecksum 屬性，該屬性對應至 [備份總和檢查碼預設] 伺服器設定
  - [Preview 5 的新功能] 在伺服器物件上公開新的 ProductUpdateLevel 屬性，該屬性對應至使用中 SQL 版本的服務層級 (例如 CU12、RTM 等…)
  - [Preview 5 的新功能] 在資料庫物件上公開新的 LastGoodCheckDbTime 屬性，該屬性對應至 "lastgoodcheckdbtime" 資料庫屬性。 如果沒有這類屬性可用，則會傳回預設值 1/1/1900 12:00:00 AM。
  - [Preview 5 的新功能] 將 RegSrvr.xml 檔案 (已註冊的伺服器設定檔) 位置移至 "%AppData%\Microsoft\SQL Server Management Studio" (未進行版本控制，因此可跨不同的 SSMS 版本共用)
  - [Preview 7 的新功能] 新增**雲端見證**作為 SMO 和 SSMS 中的新仲裁類型及新資源類型。
  - [Preview 7 的新功能] 新增 SMO 和 SSMS 中[邊緣條件約束](../relational-databases/tables/graph-edge-constraints.md)的支援。
  - [RC1 的新功能] 已在 SMO 和 SSMS 中新增「邊緣條件約束」的串聯刪除支援。
  - [RC1 的新功能] 已新增資料分類「讀取-寫入」權限的支援。


- **Azure Data Studio 整合**
  - 新增功能表項目以啟動/下載 Azure Data Studio
  - [Preview 5 的新功能] 將 [啟動 Azure Data Studio] 功能表項目新增至 [物件總管]
  - [Preview 7 的新功能] 在 Azure Data Studio 中，當您以滑鼠右鍵按一下 [物件總管] 中的資料庫時，啟用執行查詢或建立新的筆記本。

- **執行程序表**
  - 在執行程序表運算子節點下新增實際經過時間、實際值與估計值的資料列 (若有)。 這會讓實際計劃看起來與即時查詢統計資料計劃一致。
  - 按一下執行程序表的 [編輯查詢] 按鈕時已修改工具提示並新增了註解，以指示使用者如果查詢超過 4000 個字元，則 SQL 引擎可能會截斷執行程序表。
  - 新增邏輯以顯示「具體化程式運算子 (外部 Select)」
  - 新增執行程序表屬性 BatchModeOnRowStoreUsed，讓您輕鬆找出正在使用「資料列存放區批次模式掃描」功能的查詢。 只要查詢在資料列存放區上執行批次模式掃描，新的屬性 (BatchModeOnRowStoreUsed="true") 就會新增至 StmtSimple 元素。
  - [Preview 7 的新功能] 將執行程序表支援新增至 `DW ROLLUP` 和 `CUBE` 的 LocalCube RelOp。

- **資料庫相容性層級升級**
  - [Preview 5 的新功能] 在 [<Database name>] -> [工作] -> [資料庫升級] 下新增選項。 這會啟動新的 Query Tuning Assistant (QTA) (查詢調整小幫手) 來引導使用者完成下列程序：
    - 收集效能基準資料，再升級資料庫相容性層級。 
    - 升級至想要的資料庫相容性層級
    - 針對相同的工作負載，收集第二輪的效能資料。
    - 偵測工作負載迴歸，並提供經過測試的建議來提升工作負載效能。

    這與[在升級到新版 SQL Server 期間保持效能穩定性](../relational-databases/performance/query-store-usage-scenarios.md#CEUpgrade)中所述的資料庫升級過程相似，其不同處是在最後一個步驟中，QTA 不會依賴先前已知良好的狀態來產生建議。

- **查詢存放區**
  - [Preview 5 的新功能] 藉由對圖表 Y 軸上顯示的數值新增千位分隔符，改善了某些報表 (整體資源耗用量) 的可用性。
  - [Preview 5 的新功能] 新增「查詢等候統計資料」報表。

- **資料遮罩**
  - [Preview 5 的新功能] 新增靜態資料遮罩。 靜態資料遮罩是一項資料保護工具，可讓使用者建立其 SQL 資料庫的複本，並對複本上的敏感性資料進行遮罩。 這項功能經證實對於要與開發/測試小組或分析小組等非生產使用者共用其生產資料庫的人員很有用。 如需詳細資訊，請參閱 [Static Data Masking for Azure SQL Database and SQL Server](https://azure.microsoft.com/blog/static-data-masking-preview/) (適用於 Azure SQL Database 和 SQL Server 的靜態資料遮罩)。
  - [Preview 7 的新功能] 現已支援 JSON 設定檔
  - [Preview 7 的新功能] 變更 XML 設定檔格式，使其在向前邁進的過程中更具彈性。  現有的設定檔將需要重新建立。
  - [Preview 7 的新功能] 包含記憶體最佳化及暫存資料表的資料庫現在可以進行遮罩。  有些限制仍會套用到記憶體最佳化及暫存資料表本身。
  - [Preview 7 的新功能] 內部部署資料庫的資料庫複製操作現在會針對 `BACKUP DATABASE` 步驟使用 `COPY_ONLY` 選項。
  - [Preview 7 的新功能] 已遮罩資料庫現在會在遮罩操作進行中時設為 `SIMPLE` 復原模型，以減少使用記錄，並在完成後回到其原始值。
  - [Preview 7 的新功能] 已遮罩資料庫現在當操作進行中時會名為 `<output database name>-MaskInProgress`，並在遮罩操作成功後重新命名為 `<output database name>`。
  - [Preview 7 的新功能] 變更設定 UI 中資料行的顯示順序，使其根據序號而非字母順序。
  - [Preview 7 的新功能] 移除在設定 UI 中大量選取資料行的選項，避免未預期的行為。
  - [Preview 7 的新功能] 改善針對連線及命令失敗的內部重試邏輯。
 
- **Always On**
  - 重新雜湊 SSMS Always On 儀表板中的 RTO (預估復原時間) 和 RPO (估計的資料遺失)。 正在更新 https://docs.microsoft.com/sql/database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups 上的文件

- **稽核檔案**
  - 將驗證方法從儲存體帳戶金鑰驗證變更為 Azure AD 驗證
  - [RC1 的新功能] 已更新已知的稽核動作清單，而納入 FEATURE RESTRICTION ADD/CHANGE GROUP/DROP。

- **SSIS**
  - [Preview 5 的新功能] 新增支援，允許客戶對 Azure Government 雲端中 Azure-SSIS IR 上的 SSIS 套件進行排程
  - [Preview 6 的新功能] 當您使用 SSMS 所提供 MI 的 SQL Agent 時，您可以在 SSIS 代理程式作業步驟中設定參數和連線管理員。
  - [Preview 7 的新功能] 連線到 Azure SQL DB/受控執行個體時，您可以使用 "\<default\>" 作為初始資料庫來連線到它。
  - [Preview 7 的新功能] 在 [Integration Services 目錄] 節點下方新增新的重試項目 [在 Azure Data Factory 中嘗試 SSIS]，該項目可用於啟動 [Integration Runtime 建立精靈]，並可快速建立 Azure-SSIS Integration Runtime。
  - [Preview 7 的新功能] 在 [目錄建立精靈] 中新增 [建立 SSIS IR] 按鈕，該項目可用於啟動 [Integration Runtime 建立精靈]，並可快速建立 "Azure-SSIS Integration Runtime"。
  - [Preview 7 的新功能] ISDeploymentWizard 現在支援在命令列模式中進行 SQL 驗證、Azure Active Directory 整合式驗證，以及 Azure Active Directory 密碼驗證。

- **資料分類**
  - 重新組織資料分類工作功能表：新增資料庫工作功能表的子功能表，並新增選項讓您從功能表開啟報表，而不需要先開啟分類資料視窗。
  - [Preview 7 的新功能] 將新功能「資料分類」新增至 SMO。 資料行物件公開了新的屬性：SensitivityLabelName、SensitivityLabelId、SensitivityInformationTypeName、SensitivityInformationTypeId，及 IsClassified (唯讀)。 如需詳細資訊，請參閱： https://docs.microsoft.com/sql/t-sql/statements/add-sensitivity-classification-transact-sql?view=azuresqldb-current 
  - [Preview 7 的新功能] 將 [分類報告] 功能表項目新增至 [資料分類] 飛出視窗。

- **弱點評定**
  - [Preview 5 的新功能] 啟用 Azure SQL DW 上的 [弱點評定] 工作功能表。
  - [Preview 7 的新功能] 變更在 Azure SQL Database 受控執行個體伺服器上執行的弱點評定規則，使「弱點評定」的掃描結果與 Azure SQL DB 中的內容一致。 
  - [Preview 7 的新功能] 「弱點評定」現在支援 Azure SQL DW。

- **永遠加密**
  - [連線至伺服器] 對話方塊之新 [Always Encrypted] 索引標籤中的 [啟用 Always Encrypted] 核取方塊現在提供簡單的方法來啟用/停用資料庫連線的 Always Encrypted。 

- [**具有安全記憶體保護區的 Always Encrypted**](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves)
  - 在 SQL Server 2019 Preview 中，已完成數個增強功能來支援具有安全記憶體保護區的 Always Encrypted
    - [連線至伺服器] 對話方塊中用於指定記憶體保護區證明 URL 的文字欄位 (新的 [Always Encrypted] 索引標籤)。
    - [新增資料行主要金鑰] 對話方塊中用來控制新資料行主要金鑰是否允許記憶體保護區計算的新核取方塊。
    - 其他 Always Encrypted 金鑰管理對話方塊現在會公開哪些資料行主要金鑰允許記憶體保護區計算的資訊。

- **一般檔案匯入精靈**
  - [Preview 7 的新功能] 新增邏輯，通知使用者一般檔案匯入可能會導致重新命名資料行。

- **資料層應用程式精靈**
  - [Preview 7 的新功能] 新增使用圖形資料表匯入/匯出資料層應用程式的支援。

- **Azure SQL 受控執行個體**
  - [Preview 7 的新功能] 新增 **AAD 登入**作為 SMO 及 SSMS 中連線至 Azure SQL 受控執行個體時的新登入類型。

- **XEvent 檢視器**
  - [Preview 7 的新功能] 在 XEvent 檢視器中，啟用執行程序表視窗以取得更多 XEvent。




### <a name="bug-fixes"></a>錯誤修正

- **當機/停止回應**
  - 修正與 GDI 物件相關的常見 SSMS 當機來源
  - 修正選取「撰寫指令碼為 Create/Update/Drop」(已移除 SMO 物件的不必要提取) 時停止回應且效能不佳的常見來源
  - 修正啟用 ADAL 追蹤時，使用 MFA 連線至 Azure SQL DB 後造成的停止回應
  - 修正「即時查詢統計資料」從 [活動監視器] 叫用時的停止回應 (或發現到的停止回應) (使用 SQL Server 驗證但未設定 [保存安全性資訊] 時會列出此問題)。
  - 修正在 [物件總管] 中選取 [報表] 時的停止回應，而停止回應會出現高度延遲連線或暫時無法存取資源的情況。
  - [Preview 5 的新功能] 修正嘗試使用中央管理伺服器和 SQL Azure 伺服器時的 SSMS 當機問題。 如需詳細資訊，請參閱 https://feedback.azure.com/forums/908035/suggestions/33374884。 
  - [Preview 5 的新功能] 藉由最佳化 IsFullTextEnabled 屬性的擷取方式，修正了 [物件總管] 的停止回應問題
  - [Preview 5 的新功能] 藉由避免建置不必要的查詢來擷取資料庫屬性，修正了 [複製資料庫精靈] 的停止回應問題
  - [Preview 7 的新功能] 修正編輯 T-SQL 時造成 SSMS 停止回應/當機的問題。 

- **連線對話方塊**
  - 啟用按下 DEL 鍵從先前的使用者名稱清單移除使用者名稱的功能 (如需詳細資料，請參閱 https://feedback.azure.com/forums/908035/suggestions/32897632)

- **XEvent**
  - 新增 "action_name" 和 "class_type_desc" 這兩個資料行，它們會將動作識別碼及類別類型欄位顯示為可讀取字串。
  - 移除事件 XEvent 檢視器 1,000,000 個事件的上限。

- **外部資料表**
  - 新增範本、SMO、IntelliSense 和屬性方格對 Rejected_Row_Location 的支援

- **SSMS 選項**
  - 修正 [工具] | [選項] | [SQL Server 物件總管] | [命令] 頁面未正確調整大小的問題。
  - SSMS 現在預設會停用 XMLA 編輯器中的 DTD 自動下載功能 -- XMLA 指令碼編輯器 (使用 XML 語言服務) 現在預設會防止自動下載潛在惡意 XMLA 檔案的 DTD。  這可藉由在 [工具]->[選項]->[環境]->[文字編輯器]->[XML]->[其他] 中關閉 [自動下載 DTD 和結構描述] 設定進行控制。  
  - [Preview 5 的新功能] 將 CTRL+D 還原為舊版 SSMS 中所使用的快速鍵。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035/suggestions/35544754

- **一般 SSMS**
  - [Preview 7 的新功能] 修正編輯 T-SQL 時造成 SSMS 停止回應/當機的問題。
  - [Preview 7 的新功能] 修正 `ApplicationIntent` 並未在 `Registered Servers` 內的連線中一同傳遞的問題。
  - [Preview 7 的新功能] 修正在高 DPI 監視器中並未適當轉譯**新 XEvent 工作階段精靈 UI** 表單的問題。
  - [Preview 7 的新功能] 修正嘗試匯入 `.bacpac` 檔案時的問題。
  - [Preview 7 的新功能] 修正嘗試顯示具有 `FILEGROWTH > 2048GB` 資料庫屬性時擲回算數溢位錯誤的問題。
  - [Preview 7 的新功能] 修正在按兩下時 SSMS 無法開啟 .sql 檔案的問題。
  - [RC1 的新功能] 已修正使用者識別碼屬於多個租用戶時無法進行 MFA 驗證的問題。
  - [RC1 的新功能] 已修正效能儀表板報表會報告在子報表中找不到的 PAGELATCH 和 PAGEIOLATCH 等候的問題。

- **SSMS 編輯器**
  - 修正在「SQL 系統資料表」中，還原預設色彩是將色彩變更為檸檬綠，而不是預設綠色，而令人難以在白色背景上進行閱讀的問題 (如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32896906)
  - 修正 IntelliSense 在使用 AAD 驗證連線到 Azure SQLDW 時無法運作的問題。
  - 修正 IntelliSense 在使用者缺少 master 存取權時於 Azure 中的體驗
  - 修正用來建立「時態表」的程式碼片段，當目標資料庫的定序會區分大小寫時，此程式碼片段就會中斷。
  - [Preview 6 的新功能] IntelliSense 現在可識別新的 TRANSLATE 函式。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430
  - [Preview 6 的新功能] 已改善 FORMAT 內建函式的 IntelliSense。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676
  - [Preview 6 的新功能] LAG 和 LEAD 現在是內建函式。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757
  - [Preview 6 的新功能] 修正 IntelliSense 在使用 "ALTER TABLE...ADD CONSTRAINT...WITH(ONLINE=ON)" 時發出警告的問題
  - [RC1 的新功能] 已修正有數個系統檢視和資料表值函式未正確以色彩標示的問題。

- **物件總管**
  - 修正當嘗試在 OE 中展開 [管理] 節點時，SSMS 可能會擲回「物件無法從 DBNull 轉換為其他類型」例外狀況 (設定錯誤的 DataCollector) 的問題
  - 修正當重新命名節點時 DEL 鍵無法運作的問題 (如需詳細資料，請參閱 https://feedback.azure.com/forums/908035/suggestions/32910247 及其他重複項目)
  - 修正 OE 在叫用「編輯前 N 個...」之前未逸出引號而造成設計混淆的問題
  - 修正 [匯入資料層應用程式精靈] 無法從 Azure 儲存體樹狀結構啟動的問題。
  - 修正「Database Mail 設定」中沒有保存 SSL 核取方塊狀態的問題 (如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541)
  - 修正 SSMS 在嘗試使用 is_auto_update_stats_async_on 還原資料庫時，現有連線關閉選項呈現灰色的問題
  - 修正以滑鼠右鍵按一下 OE 節點 (例如「資料表」)，並想要執行動作 (例如移至 [篩選] > [篩選設定] 來篩選資料表)，篩選設定表單可能會出現在 SSMS 目前使用中畫面以外其他畫面上的問題。 如需詳細資訊，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106。
  - 修正當嘗試重新命名物件時，DELETE 鍵在 OE 中無法運作的長時間待處理問題。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510
  - 顯示現有資料庫檔案的屬性時，大小會出現在 [大小 (MB)] 資料行下方，而不是 [初始大小 (MB)]，後者是建立新資料庫時所顯示的項目。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024
  - 停用 [圖形資料表] 上的 [設計] 操作功能表項目，因為目前版本的 SSMS 並不支援這類資料表。
  - [Preview 5 的新功能] 修正 [新增作業排程] 對話方塊無法在高 DPI 監視器上正確轉譯的問題。 如需詳細資料，請參閱 https://feedback.azure.com/admin/v3/suggestions/35541262 
  - [Preview 5 的新功能] 修正/改善資料庫大小 ([大小 (MB)]) 在 [物件總管] 詳細資料中顯示方式的問題：僅限 2 個小數位數，並使用千位分隔符格式化。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035/suggestions/34379308
  - [Preview 5 的新功能] 修正造成「空間索引」建立失敗並出現「若要完成此動作，請設定屬性 PartitionScheme」之類錯誤的問題。
  - [Preview 5 的新功能] [物件總管] 中的次要效能改善，盡可能避免發出額外的查詢。
  - [Preview 5 的新功能] 將重新命名資料庫時要求確認的邏輯延伸到所有結構描述物件 (可設定及停用此設定)
  - [RC1 的新功能] 已在物件總管篩選中新增適當的逸出。 如需詳細資訊，請參閱 [Azure 意見反應 36678803](https://feedback.azure.com/forums/908035/suggestions/36678803)。

- **說明檢視器**
  - 改善接受線上/離線模式的邏輯 (可能仍有些問題待解決)
  - 修正 [檢視說明] 以接受線上/離線設定。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791

- **物件指令碼**
  - 整體效能改善 - 相較於 SSMS 17.7，產生 WideWorldImporters 指令碼只要一半的時間
  - 撰寫物件指令碼時，會省略具有預設值的資料庫範圍設定 
  - 撰寫指令碼時，不要產生動態 T-SQL (如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391)
  - 在 SQL Server 2016 及更早版本上撰寫資料表指令碼時，省略圖形語法 "as edge" 和 "as node"。
  - 修正搭配 MFA 使用 AAD 連線到 Azure SQL Database 時，撰寫資料庫物件指令碼失敗的問題。
  - [Preview 6 的新功能] 修正嘗試在 Azure SQL Database 上使用 GEOMETRY_AUTO_GRID/GEOGRAPHY_AUTO_GRID 撰寫空間索引指令碼時擲回錯誤的問題。
  - [Preview 7 的新功能] 修正即使 [物件總管] 指令碼設定已設為符合來源，仍會造成 Azure SQL Database 資料庫指令碼一律瞄準內部部署 SQL Server 執行個體的問題。
- [Preview 7 的新功能] 修正嘗試針對 Azure SQL 資料倉儲資料庫中涉及叢集及非叢集索引的資料表撰寫產生不正確 T-SQL 陳述式指令碼時，所產生的問題。
- [Preview 7 的新功能] 修正嘗試針對 Azure SQL 資料倉儲資料庫中具有叢集資料行存放區索引及叢集索引資料表撰寫產生不正確 T-SQL 的指令碼 (重複陳述式) 時，所產生的問題。
- [Preview 7 的新功能] 修正沒有範圍值的資料分割資料表指令碼 (Azure SQL 資料倉儲資料庫)。
- [Preview 7 的新功能] 修正防止撰寫稽核或稽核規格 `SERVER_PERMISSION_CHANGE_GROUP` 指令碼的問題。
- [Preview 7 的新功能] 修正防止撰寫來自 Azure SQL 資料倉儲統計資料指令碼的問題。 請參閱 [Microsoft Azure 意見反應論壇](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897296)。

- **資料表設計工具**
  - [Preview X 的新功能，X<4] 修正「編輯 200 個資料列」的當機問題
  - 修正設計工具在連線至 Azure SQL Database 時，允許新增至資料表的問題

- **SMO**
  - 修正 SMO/ServerConnection 不正確地處理 SqlCredential 連線的問題。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941
  - [Preview 6 的新功能] 修正使用 SMO 撰寫的應用程式若嘗試列舉多個執行緒上相同伺服器的資料庫時發生錯誤的問題 (即使在每個執行緒上使用個別的 SqlConnection 執行個體仍會發生錯誤)。
  - [Preview 7 的新功能] 修正從外部資料表傳輸時效能降低的問題。
  - [Preview 7 的新功能] 修正瞄準 Azure SQL DB 時，`ServerConnection` 執行緒安全性造成 SMO 流失 `SqlConnection` 執行個體的問題。
  - [Preview 7 的新功能] 修正在嘗試復原名稱中具有大括弧 `{}` 的資料庫時，造成 `StringBuilder.FormatError` 的問題。
  - [RC1 的新功能] 已修正 SMO 中的 Azure 資料庫預設為所有字串比較皆採用不區分大小寫的定序，而不是使用為資料庫指定之定序的問題。
 
- **AS**
  - 修正已裁剪 AS Xevent UI [進階設定] 的問題
  - [Preview 5 的新功能] 修正 DAX 剖析擲回找不到檔案例外狀況的問題
  - [Preview 5 的新功能] 將 [部署精靈] 捷徑新增回 [開始] 功能表

- **IS**
  - [Preview 5 的新功能] 修正 SQL Server 2019 與 SSMS 18.0 安裝在同一部電腦時，[部署精靈] 無法連線到 SQL Server 的 SxS 問題。
  - [Preview 5 的新功能] 修正設計維護計畫時，無法編輯維護計畫工作的問題。
  - [Preview 5 的新功能] 修正重新命名部署中專案時，[部署精靈] 當掉的問題。
  - [Preview 5 的新功能] 啟用 Azure-SSIS IR 排程功能中的環境設定。

- **一般檔案匯入精靈**
  - 修正目的地資料表已存在時，[一般檔案匯入] 不允許變更資料表的問題。如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186)
  - 修正 [匯入一般檔案精靈] 不正確地處理雙引號 (逸出) 的問題 (如需詳細資料，請參閱 https://feedback.azure.com/forums/908035/suggestions/32897998)
  - 修正與浮點類型處理方式不正確 (在對浮點使用不同分隔符號的地區設定上) 相關的問題
  - 修正值為 0 或 1 時，與匯入位元相關的問題。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535
  - 修正浮點數輸入為 Null 的問題。 
  - [Preview 7 的新功能] 修正匯入精靈無法處理負小數值的問題。
  - [Preview 7 的新功能] 修正精靈無法從單一資料行 CSV 檔案匯入的問題。

- **HADR/AG**
  - [Preview 5 的新功能] 修正 [容錯移轉可用性群組精靈] 中的角色一律顯示為 [解析中] 的問題 
  - [Preview 5 的新功能] 修正 SSMS 在 [AG 儀表板] 中顯示截斷警告的問題。

- **資料分類** 
  - 修正導致資料分類建議組件不適用於全新安裝的安裝程式問題。
  - [Preview 6 的新功能] 修正在資料分類窗格中儲存分類時，若其他資料庫上已開啟其他資料分類窗格的問題。

- **備份/還原/附加/卸離資料庫**
  - 修正當 .mdf 檔案的實體檔案名稱與原始檔案名稱不相符時，使用者無法附加資料庫的問題
  - 修正 SSMS 可能找不到有效的還原計畫，或者可能找到次佳還原計畫的問題。 如需詳細資訊，請參閱 https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752。
  - 修正嘗試還原 URL 備份時的 SSMS 當機問題 (這是先前預覽中引進的迴歸問題)。
  - [Preview 5 的新功能] 修正 [附加資料庫精靈] 未顯示已重新命名次要檔案的問題。 現在會顯示檔案，並新增其相關註解 (例如「找不到」)。 如需詳細資料，請參閱 https://feedback.azure.com/forums/908035/suggestions/32897434

- **作業活動監視器**
  - 修正使用作業活動監視器 (含篩選) 時的當機問題

- **受控執行個體支援**
  - 改善/完善對受控執行個體的支援：停用 UI 中不受支援的選項，並修正 [檢視稽核記錄] 選項來處理 URL 稽核目標。
  - [產生和發佈指令碼精靈] 會撰寫不受支援的 CREATE DATABASE 子句指令碼
  - CL 執行個體已停用即時查詢統計資料
  - [資料庫屬性]->[檔案] 不正確地撰寫 ALTER DB ADD FILE 指令碼
  - 修正使用 SQL Agent 排程器的迴歸問題，在其中即使選擇了其他某個排程類型，還是會選擇 ONIDLE 排程
  - 調整 MAXTRANSFERRATE、MAXBLOCKSIZE，以便在 Azure 儲存體上執行備份
  - 在 RESTORE 作業之前撰寫結尾記錄備份指令碼的問題 (CL 不支援此作業)。
  - [建立資料庫精靈] 不正確地撰寫 CREATE DATABASE 陳述式指令碼
  - 修正在連線至受控執行個體的情況下，當嘗試使用「活動監視器」時顯示錯誤的問題。
  - [Preview 5 的新功能] 改善 AAD 登入 (SSMS 總管中) 的支援。
  - [Preview 5 的新功能] 改善 SMO 檔案群組物件的指令碼撰寫。
  - [Preview 5 的新功能] 改善認證和稽核的 UI。
  - [Preview 5 的新功能] 新增邏輯複寫的支援。
  - [Preview 7 的新功能] 修正造成以滑鼠右鍵按一下資料庫，並選擇 [匯入資料層應用程式] 時失敗的問題。
  - [Preview 7 的新功能] 修正造成以滑鼠右鍵按一下 `TempDB` 以顯示錯誤時的問題。
  - [Preview 7 的新功能] 修正為 SMO 中的 `ALTER DB ADD FILE` 陳述式撰寫指令碼時，造成所產生 T-SQL 指令碼空白的問題。
  - [RC1 的新功能] 已改善受控執行個體伺服器的特定屬性 (硬體世代、服務層、已使用和保留的儲存體) 的顯示方式。

- **Azure SQL Database**
  - 修正當連線至 Azure SQL DB 中的使用者資料庫 (而非 master) 時，Azure SQL DB 查詢視窗的資料庫清單不正確地填入資料的問題。
  - 修正無法將「時態表」新增至 SQL Azure DB 的問題。
  - [Preview 6 的新功能] 在 Azure 中的 [統計資料] 功能表下啟用 [統計資料屬性] 子功能表選項，因為到目前為止已完全支援一段時間。
  - 修正通用 Azure UI 控制項中防止使用者顯示 Azure 訂用帳戶 (若未超過 50 個) 的問題。 此外，排序已變更為依名稱，而不是依訂用帳戶識別碼。 例如，當使用者嘗試從 URL 還原備份時，可能遇到這個問題。
  - 修正通用 Azure UI 控制項在列舉訂用帳戶時發生的問題，當使用者在一些租用戶中沒有任何訂用帳戶時，這可能會產生「索引超出範圍。 必須為非負數且小於集合的大小。」 錯誤。 例如，當使用者嘗試從 URL 還原備份時，可能遇到這個問題。
  - [RC1 的新功能] 已修正服務等級目標 (SLO) 會硬式編碼而導致 SSMS 難以支援較新 SQL Azure SLO 的問題。 現在，使用者可以登入 Azure，並且讓 SSMS 擷取所有適用的 SLO 資料 (版本和大小上限)。

- **查詢資料存放區**
  - [Preview 6 的新功能] 修正可能擲回 "DocumentFrame (SQLEditors)" 例外狀況的問題。
  - [Preview 6 的新功能] 修正嘗試在內建查詢存放區報表中設定自訂時間間隔時，使用者無法在開始/結束間隔上選取上午或下午的問題

- **結果方格**
  - 修正造成高對比模式 (看不到選取的行號) 的問題。
  - [RC1 的新功能] 已修正在按一下方格時會導致「索引超出範圍」例外狀況的問題。
  - [RC1 的新功能] 已修正方格結果背景色彩遭到忽略的問題。 如需詳細資訊，請參閱 [Azure 意見反應 32895916](https://feedback.azure.com/forums/908035/suggestions/32895916)。

- **XEvent 分析工具**
  - 修正當連線至含 96 個核心的 SQL Server 時，XEvent 分析工具無法啟動的問題。

- **DAC 匯入精靈**
  - [Preview 5 的新功能] 修正使用 AAD 連線時，[DAC 匯入精靈] 無法運作的問題。

- **XEvent 檢視器**
  - [Preview 5 的新功能] 修正嘗試使用「延伸事件工具列選項」群組事件時，XEvent 檢視器將當機的問題

- **弱點評定**
  - [Preview 5 的新功能] 修正掃描結果未正確載入的問題。

- **複製資料庫精靈**
  - [Preview 6 的新功能] [產生指令碼/傳輸/複製資料庫精靈] 嘗試使用記憶體內部資料表建立資料表時，不會強制開啟 ansi_padding
  - [Preview 6 的新功能] SQL 2017 和 SQL 2019 上已中斷 [傳輸資料庫工作/複製資料庫精靈]
  - [Preview 6 的新功能] 在建立相關聯的外部資料來源之前，須建立 [產生指令碼/傳輸/複製資料庫精靈] 指令碼資料表

- **分析工具**
  - [Preview 6 的新功能] 將「彙總資料表重寫查詢」事件新增至分析工具事件。
  - [RC1 的新功能] 已修正導致 SQL Profiler 無法在 Windows 7 SP1 上啟動的問題。

- **執行程序表**
  - [Preview 6 的新功能] 新的記憶體授與運算子屬性在有多個執行緒時不正確地顯示。
  - [RC1 的新功能] 已在實際執行 XML 計畫的 RunTimeCountersPerThread 中新增下列 4 個屬性：HpcRowCount (HPC 裝置所處理的資料列數目)、HpcKernelElapsedUs (等候使用中核心執行的經過時間)、HpcHostToDeviceBytes (從主機傳輸至裝置的位元組數) 和 HpcDeviceToHostBytes (從裝置傳輸至主機的位元組數)。

- **資料遮罩**
  - [Preview 7 的新功能] 修正自動複製具有多個記錄及 Filestream 記憶體最佳化資料表檔案的內部部署資料庫時會失敗的 Bug。

- **資料層應用程式精靈**
  - [RC1 的新功能] 已修正使用者因為對伺服器的存取受到限制 (例如，無法存取相同伺服器上的所有資料庫) 而無法匯入資料層應用程式 (.dacpac) 的問題。
  - [RC1 的新功能] 已修正在多個資料庫裝載於相同的 Azure SQL 伺服器時會導致匯入極度緩慢的問題。

### <a name="deprecated-features"></a>已被取代的功能

SSMS 中不再提供下列功能：

- T-SQL 偵錯工具
- 資料庫圖表
- OSQL.EXE
- Dreplay 系統管理 UI
- Configuration Manager 工具：
  - SQL Server 組態管理員和 Reporting Server 設定管理員不再是 SSMS 安裝程式的一部分。

- DMF 標準原則
  - 這些原則不再與 SSMS 一起安裝。 它們會移至 Git。 只要使用者想要，就能參與及下載/安裝這些原則。

- 已移除 SSMS 命令列選項 -P
  - 基於安全性考量，已移除命令列上指定純文字密碼的選項。

- 已移除 [產生指令碼] | [發佈到 Web 服務] 已從 SSMS UI 中移除這個 (已淘汰) 功能。
- 已移除 [物件總管] 中的「維護 |舊版」節點。 [產生和發佈指令碼] | [發佈到 Web 服務] 選項已移除。 您再也無法存取「舊的」[資料庫維護計劃] 與 [SQL Mail] 節點。 新式的 [Database Mail] 和 [維護計劃] 節點會繼續如往常般運作。
- [RC1 的新功能] 已移除靜態資料遮罩 (預覽) 功能。

### <a name="known-issues"></a>已知問題

- 不適用


## <a name="ssms-1791-latest-ga-release"></a>SSMS 17.9.1 (最新的 GA 版本)

![下載](../ssdt/media/download.png) [SSMS 17.9.1](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)

- 版本號碼：17.9.1<br>
- 組建編號：14.0.17289.0<br>
- 發行日期：2018 年 11 月 21 日

17.9.1 是 17.9 的小型更新，其中包括下列錯誤修正：

- 修正在搭配使用 SQL 查詢編輯器和「支援 MFA 的 Active Directory - Universal」驗證時，使用者可能會遇到每一次查詢叫用時連線都會關閉並重新開啟的問題。 這類連線關閉的副作用包括在未預期的情況下卸除全域暫存資料表，以及有時候會給予連線新的 SPID。
- 修正一個長期未解決的問題，即還原計畫找不到還原計畫，或者在某些情況下會產生無效率的還原計畫。
- 修正 [匯入資料層應用程式] 精靈中的一個問題，該問題會在連接到 Azure SQL Database 時導致錯誤。



> [!NOTE]
> SSMS 17.x 的非英文當地語系化版本若安裝在下列項目上，則需要 [KB 2862966 安全性更新程式套件](https://support.microsoft.com/kb/2862966)：Windows 8、Windows 7、Windows Server 2012 和 Windows Server 2008 R2。

[簡體中文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40a)

## <a name="ssms-179"></a>SSMS 17.9

![下載](../ssdt/media/download.png) [SSMS 17.9](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409)

組建編號：14.0.17285.0<br>
發行日期：2018 年 9 月 4 日

> [!NOTE]
> SSMS 17.x 的非英文當地語系化版本若安裝在下列項目上，則需要 [KB 2862966 安全性更新程式套件](https://support.microsoft.com/kb/2862966)：Windows 8、Windows 7、Windows Server 2012 和 Windows Server 2008 R2。

[簡體中文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40a)


### <a name="whats-new"></a>新功能

**一般 SSMS**

執行程序表：

- 圖形化執行程序表現在會顯示新資料列模式記憶體授與回應屬性 (當此功能已針對特定方案啟用時)：IsMemoryGrantFeedbackAdjusted 與 LastRequestedMemory 會新增至 MemoryGrantInfo 查詢計畫 XML 元素。 如需資料列模式記憶體授與回應的詳細資料，請參閱 [SQL 資料庫中的彈性查詢處理](https://docs.microsoft.com/sql/relational-databases/performance/adaptive-query-processing)。

Azure SQL： 

- 新增對建立 Azure DB 時的 vCore SKU 支援。 如需詳細資訊，請參閱[以虛擬核心為基礎的購買模型](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers#vcore-based-purchasing-model)。
 

### <a name="bug-fixes"></a>錯誤修正

**一般 SSMS**
    
複寫監視器：

- 修正導致複寫監視器 (SqlMonitor.exe) 未啟動的問題 (User Voice 項目： https://feedback.azure.com/forums/908035-sql-server/suggestions/34791079)。

匯入一般檔案精靈：

- 修正 [一般檔案精靈] 對話方塊說明頁面的連結 
- 修正當資料表已存在時，精靈不允許變更目的地資料表的問題：這可讓使用者重試，而不需要結束精靈、刪除失敗的資料表，然後重新輸入資訊到精靈 (User Voice 項目： https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186)。

匯入/匯出資料層應用程式：

- 修正 DacFx 中導致當處理具有已定義且在資料表上無索引的資料表時匯入 .bacpac 失敗並顯示「錯誤 SQL72014: .Net SqlClient 資料提供者:訊息 9108、層級 16、狀態 10、行 1 此類型的統計資料不支援累加。 訊息的問題。

IntelliSense：

- 修正搭配 MFA 使用 AAD 時，intellisense 完成無法運作的問題。

物件總管：

- 修正在隨機監視器上而非 SSMS 執行所在監視器 (多監視器系統) 上顯示 [篩選對話方塊] 的問題。

Azure SQL：

- 修正與 [可用資料庫] 中的列舉相關的問題，其中當連線到特定資料庫時，"master" 未顯示在下拉式清單中。
- 修正搭配 MFA 使用 ADD 連線到 Azure SQL Database 時，嘗試產生指令碼 (「資料」或「結構描述與資料」) 失敗的問題。
- 修正在檢視表設計工具 (檢視表) 無法在已連線到 Azure SQL Database 的情況下從 UI 選取 [新增資料表] 的問題。
- 修正 SSMS 查詢編輯器在 MFA 權杖更新期間自動關閉並重新開啟連線的問題。 這可以防止發生使用者不知情的副作用 (例如關閉交易而且絕不重新開啟)。 此變更會將權杖到期時間加到屬性視窗。 
- 修正 SSMS 未搭配 MFA 登入使用 AAD 針對 MSA 帳戶強制密碼提示的問題。 

活動監視器： 

- 修正導致「即時查詢統計資料」從活動監視器啟動並使用 SQL 驗證時停止回應的問題。 

Microsoft Azure 整合： 

- 修正 SSMS 只顯示前 50 的訂用帳戶 (Always Encrypted 對話、來自 URL 對話方塊的備份/還原等…) 的問題。 
- 修正 SSMS 在嘗試登入沒有任何儲存體帳戶的 Microsoft Azure 帳戶時擲回例外狀況 (「索引超出範圍」) 的問題 (在 [從 URL 還原備份] 對話方塊中)。 

物件指令碼： 

- 編寫「Drop 及 Create」指令碼時，SSMS 現在會避免產生動態 T-SQL。
- 編寫資料庫物件指令碼時，SSMS 現在不會產生指令碼以設定資料庫範圍設定 (若它們是設定為預設值)。

說明：

- 修正「如何使用輔助說明」未遵循線上/離線模式這個長期未解決的問題。
- 當按一下 [說明 | 社群專案與範例] 時，SSMS 現在會開啟指向 Git 頁面的網頁瀏覽器，而且不會因未使用舊瀏覽器而顯示錯誤/警告。

### <a name="known-issues"></a>已知問題


> [!IMPORTANT]
> 搭配使用 SQL 查詢編輯器和 *支援 MFA 的 Active Directory - Universal* 驗證時，使用者可能會遇到每一次查詢叫用時連線都會關閉並重新開啟的問題。 這類關閉的副作用包括在未預期的情況下卸除全域暫存資料表，以及有時候會給予連線新的 SPID。 若連線上有開啟中的交易，則不會發生此關閉。 若要因應此問題，使用者可在連線參數中設定 `persist security info=true`。




## <a name="previous-ssms-releases"></a>舊版 SSMS

按一下下列各節中的標題連結，以下載舊版 SSMS：

## <a name="downloadssdtmediadownloadpng-ssms-1781httpsgomicrosoftcomfwlinklinkid875802"></a>![下載](../ssdt/media/download.png) [SSMS 17.8.1](https://go.microsoft.com/fwlink/?linkid=875802)
17.8 中發現一個與佈建 SQL 資料庫有關的 BUG，因此以 SSMS 17.8.1 取代 17.8。

組建編號：14.0.17277.0<br>
發行日期：2018 年 6 月 26 日

[簡體中文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40a)


### <a name="whats-new"></a>新功能

**一般 SSMS**

資料庫屬性：

- 這項改進會公開檔案群組的 **AUTOGROW_ALL_FILES** 設定選項。 這個新的設定選項已新增至 [資料庫屬性] > [檔案群組] 視窗之下，採用的形式是為每個可用檔案群組 (除了 Filestream 和記憶體最佳化檔案群組之外) 提供新的核取方塊資料行 ([所有檔案自動成長])。 使用者只要切換對應的 Autogrow_All_Files 核取方塊，就能啟用或停用特定檔案群組的 AUTOGROW_ALL_FILES。 同樣地，針對資料庫 (SQL2016 和更新版本) 的 CREATE (建立)/產生指令碼，編寫資料庫指令碼時也已正確地編寫 **AUTOGROW_ALL_FILES** 選項的指令碼。
    
SQL 編輯器：

- 已改善當使用者沒有 master 存取權時，在 Azure SQL Database 中的 IntelliSense 體驗。

指令碼：

- 一般效能改進，特別是透過高延遲連線的情況。
    
**Analysis Services (AS)**

- Analysis Services 用戶端程式庫與資料提供者已更新至最新版本，其中加入了對新 Azure Government AAD 授權單位 (login.microsoftonline.us) 的支援。



### <a name="bug-fixes"></a>錯誤修正

**一般 SSMS**
    
維護計畫：

- 已修正搭配 SQL 驗證編輯維護計畫時，「通知操作員工作」會在使用 SQL 驗證時失敗的問題。
    
指令碼：

- 已修正 SMO 中的 PostProcess 動作導致資源耗盡及 SQL 登入失敗的問題
    
SMO：

- 已修正新增包含預設條件約束的資料行且資料表已經有資料時，Table.Alter() 會失敗的問題。 如需詳細資訊，請參閱[新增資料行至已含有資料的資料表時 sql server smo 會產生內嵌預設條件約束](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895625)。
    
Always Encrypted：

- 已修正在分割的資料表上啟用 Always Encrypted 時會造成鎖定逾時錯誤的問題 (在 DacFx 中)
    

**Analysis Services (AS)**

- 已修正在 Tabular Analysis Services 1400 層級相容性模型中修改 OAuth 資料來源時發生的問題，該問題會造成在 OAuth 權杖中所做的變更不會在資料來源中更新。
- 已修正在 Analysis Services Tabular 1400 層級相容性模型的 Power Query (例如，Oracle) 中，使用某些無效的資料來源認證，或編輯不支援變更資料來源移轉的資料來源時，SSMS 中可能發生損毀的問題。


### <a name="known-issues"></a>已知問題

- 在 [特性] 視窗中修改任何檔案群組特性之後按一下 [指令碼] 按鈕，會產生兩個指令碼：其中一個指令碼會包含 *USE <database>* 陳述式，另一個指令碼則會包含 *USE master* 陳述式。  產生包含 *USE master* 的指令碼是一項錯誤，而且應予捨棄。 執行包含 *USE <database>* 陳述式的指令碼。
- 使用新的「一般目的」或「商務關鍵性」Azure SQL Database 版本時，某些對話方塊顯示版本無效錯誤。
- 可觀察到 XEvents 檢視器中的一些延遲。 這是 [.Net Framework](https://github.com/Microsoft/dotnet/blob/master/releases/net472/dotnet472-changes.md#sql) 中的已知問題。 請考慮升級到 NetFx 4.7.2。




## <a name="downloadssdtmediadownloadpng-ssms-177httpsgomicrosoftcomfwlinklinkid873126"></a>![下載](../ssdt/media/download.png) [SSMS 17.7](https://go.microsoft.com/fwlink/?linkid=873126)

組建編號：14.0.17254.0<br>
發行日期：2018 年 5 月 9 日

[簡體中文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40a)


### <a name="whats-new"></a>新功能

**一般 SSMS**

複寫監視器：   
- 針對發行者資料庫及/或散發者資料庫是可用性群組一部分的情況，複寫監視器現在支援註冊接聽程式。 您現在可以監視發行者資料庫及/或散發資料庫是 AlwaysOn 一部分的複寫環境。 
 
Azure SQL 資料倉儲： 
- 針對 Azure SQL 資料倉儲中的外部資料表，新增「拒絕的資料列位置」支援。 

**Integration Services (IS)**

- 針對部署到 Azure SQL Database 的 SSIS 套件，新增排程功能。 不同於具有 SQL Server Agent 作為首要工作排程器的內部部署 SQL Server 和 SQL Database 受控執行個體，SQL Database 並沒有內建排程器。 此新的 SSMS 功能提供類似於 SQL Server Agent 的熟悉使用者介面，來排程部署到 SQL Database 的套件。 如果您使用 SQL Database 來裝載 SSIS 目錄資料庫 SSISDB，您可以使用此 SSMS 功能，產生排程 SSIS 套件所需的 Data Factory 管線、活動和觸發程序。 然後，您可以編輯並擴充 Data Factory 中的這些物件。 如需詳細資訊，請參閱[使用 SSMS 排程 Azure SQL Database 上的 SSIS 套件執行](../integration-services/lift-shift/ssis-azure-schedule-packages-ssms.md)。 若要深入了解 Azure Data Factory 管線、活動和觸發程序，請參閱 [Azure Data Factory 中的管道及活動](https://docs.microsoft.com/azure/data-factory/concepts-pipelines-activities)和 [Azure Data Factory 中的管道執行和觸發程序](https://docs.microsoft.com/azure/data-factory/concepts-pipeline-execution-triggers)。
- 支援在 SQL 受控執行個體上的 SQL Agent 中排程 SSIS 套件。 您現在可以建立 SQL Agent 工作，在受控執行個體上執行 SSIS 套件。 

### <a name="bug-fixes"></a>錯誤修正

**一般 SSMS** 

維護計畫：   
- 已修正嘗試變更現有維護計畫的排程會擲回例外狀況的問題。 如需詳細資料，請參閱 [SSMS 17.6 crashes when clicking on a schedule in a maintenance plan](https://feedback.azure.com/forums/908035-sql-server/suggestions/33712924) (按一下維護計畫中的排程時 SSMS 17.6 損毀)。

一律開啟： 
- 已修正 AlwaysOn 延遲儀表板無法搭配 SQL Server 2012 使用的問題。
 
指令碼： 
- 已修正對 Azure SQL 資料倉儲編寫預存程序指令碼不適用於非管理使用者的問題。
- 已修正對 Azure SQL Database 編寫資料庫指令碼無法編寫 *SCOPED CONFIGURATION* 屬性指令碼的問題。
 
遙測： 
- 已修正退出傳送遙測之後，嘗試連線到伺服器時 SSMS 損毀的問題。
 
Azure SQL Database： 
- 已修正使用者無法設定或變更相容性層級 (從空白下拉) 的問題。 注意：若要將相容性層級設定為 150，使用者仍需要使用 [指令碼] 按鈕並手動編輯指令碼。 
 
SMO： 
- 在 SMO 中公開錯誤記錄檔大小設定。 如需詳細資料，請參閱 [Set the Maximum Size of the SQL Server Error Logs](https://feedback.azure.com/forums/908035-sql-server/suggestions/33624115) (設定 SQL Server 錯誤記錄檔大小上限)。  
- 修正 Linux 上 SMO 的換行字元指令碼處理。
- 擷取不常使用之屬性時的其他效能提升。  

IntelliSense： 
- 效能提升：減少 IntelliSense 查詢的資料行資料量。 這在使用具有大量資料行的資料表時特別有幫助。 

SSMS 使用者設定：
- 已修正 [選項] 畫面未正確調整大小的問題。

其他：  
- 已改善「統計資料詳細資料」頁面上的文字顯示方式。 

**Integration Services (IS)**

- 改善 Azure SQL Database 受控執行個體的支援。
- 已修正使用者無法為 SQL Server 2014 或舊版建立目錄的問題。
- 已修正報表的兩個問題：
   - 已移除 Azure 伺服器的電腦名稱。
   - 已改善當地語系化物件名稱的處理方式。


### <a name="known-issues"></a>已知問題

使用新的「一般目的」或「商務關鍵性」Azure SQL Database 版本時，某些對話方塊顯示版本無效錯誤。

## <a name="downloadssdtmediadownloadpng-ssms-176httpsgomicrosoftcomfwlinklinkid870039"></a>![下載](../ssdt/media/download.png) [SSMS 17.6](https://go.microsoft.com/fwlink/?linkid=870039)

組建編號：14.0.17230.0<br>
發行日期：2018 年 3 月 20 日

[簡體中文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40a)

### <a name="whats-new"></a>新功能

**一般 SSMS**

SQL Database 受控執行個體：

- 針對 [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)新增支援。 Azure SQL Database 受控執行個體幾乎達到 100% 的 SQL Server 內部部署相容性，這是解決常見安全性問題的原生[虛擬網路 (VNet)](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) 實作，也是有利於內部部署 SQL Server 客戶的[商務模型](https://azure.microsoft.com/pricing/details/sql-database/)。
- 支援常見的管理案例，例如：
   - 建立和改變資料庫。
   - 備份和還原資料庫。
   - 匯入、匯出、擷取及發佈資料層應用程式。
   - 檢視與改變伺服器屬性。
   - 完整的物件總管支援。
   - 撰寫資料庫物件。
   - 支援 SQL 代理程式工作。
   - 連結的伺服器支援。
- 請前往[這裡](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/)深入了解受控執行個體。

物件總管：
- 新增設定，以便從物件總管拖曳並置放於查詢視窗時，不強制以名稱周圍的括弧來括住。 (使用者建議 [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933) 和 [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051)。)

資料分類：
- 一般改善和 Bug 修正。

**Integration Services (IS)**

- 新增支援以部署套件至 [SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)。

### <a name="bug-fixes"></a>錯誤修正

**一般 SSMS**

資料分類：

- 修正「資料分類」中導致新增分類顯示為「資訊類型」和「敏感度標籤」的問題。
- 已修正將伺服器設定為區分大小寫的定序時，「資料分類」無法正常運作的問題。
        
一律開啟：

- 已修正 AG Show Dashboard 中的一個問題；當伺服器設定為區分大小寫的定序時，按一下「收集延遲資料」可能會導致錯誤。
- 已修正在叢集服務關閉時，SSMS 錯誤地將 AG 報告為「分散式」的問題。
- 在使用 [建立可用性群組] 對話方塊來建立 AG 時，已修正需要 *ReadOnlyRoutingUrl* 的問題。
- 修正當主要伺服器關閉並手動容錯移轉至次要伺服器時，NullReferenceException 會擲回的問題。
- 修正使用備份與還原來建立可用群性組以初始化資料庫時，會在次要複本中預設目錄上建立資料庫檔案的問題。 修正包含下列：
   - 新增資料與記錄檔目錄的驗證程式。
   - 只有當複本在不同於主要複本的作業系統上時，才執行檔案重新配置。
- 已修正 SSMS 精靈不產生 *CLUSTER_TYPE* 選項，而導致次要聯結失敗的問題。

安裝程式：
- 已修正 SSMS 安裝在非預設位置時，透過安裝「升級套件」升級 SSMS 失敗的問題。

SMO：
- 已修正 SQL Server 2016 及更新版本上的指令碼資料表撰寫可能需要長達 30 秒 (現在少於 1 秒) 的效能問題。

物件總管：
- 已修正當嘗試在物件總管中展開 [Management] 節點時，SSMS 可能會擲回的問題，如「物件無法從 DBNull 轉換為其他類型」。
- 已修正當使用者定義的 PS 設定檔發出輸出時，「啟動 PowerShell」 未偵測到 SQLServer 模組的問題。
- 已修正在物件總管中以右鍵按一下資料表或索引節點時，可能發生的間歇性停止回應。

Database Mail：
- 已修正當嘗試顯示與管理超過 16 個設定檔時，[Database Mail 設定精靈] 會擲回的問題。


**Analysis Services (AS)**

- 已修正在 SSMS 中修改 1400 相容性層級模型上的資料來源時，所進行的變更未儲存至伺服器的問題。

**Integration Services (IS)**

- 已修正當 SSMS 連線到 SQL Database 受控執行個體時，未顯示 SSIS 目錄節點和報表的問題

### <a name="known-issues"></a>已知問題

> [!WARNING]
> 已知問題：當使用[維護計劃](../relational-databases/maintenance-plans/maintenance-plans.md)時，SSMS 17.6 會變得不穩定且會當機的問題。 若您使用維護計劃，請勿安裝 SSMS 17.6。 若您已經安裝 17.6 且有這項問題的影響，請降級至 SSMS 17.5。 



## <a name="downloadssdtmediadownloadpng-ssms-175httpsgomicrosoftcomfwlinklinkid867670"></a>![下載](../ssdt/media/download.png) [SSMS 17.5](https://go.microsoft.com/fwlink/?linkid=867670)
正式運作 | 組建編號：14.0.17224.0

[簡體中文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40a)

### <a name="whats-new"></a>新功能

**一般 SSMS**

資料探索與分類：

- 已新增 SQL 資料探索與分類功能，以探索、分類、標示和報告您資料庫中的敏感性資料。 
- 自動探索和分類最敏感的資料 (商務、財務、醫療保健、個人資料等) 可能扮演組織資訊保護成長的關鍵角色。
- 深入了解 [SQL 資料探索與分類](../relational-databases/security/sql-data-discovery-and-classification.md)。

查詢編輯器：

- 已將 SkipRows 選項的支援新增至 Azure SQL DW 的分隔文字外部檔案格式。 這項功能可讓使用者在將分隔文字檔載入至 SQL DW 時略過指定數目的資料列。 也會新增 FIRST_ROW 關鍵字的對應 IntelliSense/SMO 支援。 

執行程序表：

- 啟用顯示 SQL 資料倉儲的預估計畫按鈕
- 新增執行程序表屬性 *EstimateRowsWithoutRowGoal*，並將新的執行程序表屬性新增至 *QueryTimeStats*：*UdfCpuTime* 和 *UdfElapsedTime*。 如需詳細資訊，請參閱 [Optimizer row goal information in query execution plan added in SQL Server 2017 CU3](https://support.microsoft.com/help/4051361) (SQL Server 2017 CU3 中已新增之查詢執行計畫的最佳化工具資料列目標資訊)。



### <a name="bug-fixes"></a>錯誤修正

**一般 SSMS**

執行程序表：

- 修正即時查詢統計資料耗用時間，以顯示引擎執行時間，而不是 LQS 連線的耗用時間。
- 修正執行程序表無法辨識套用邏輯運算子 (例如 GbApply 和 InnerApply) 的問題。
- 修正 ExchangeSpill 相關問題。

查詢編輯器：

- 修正 SSMS 可擲回下列這類錯誤的 SPID 相關問題：「輸入字串格式不正確。 (mscorlib)」(執行前面加上 "SET SHOWPLAN_ALL ON" 的簡單查詢時)。 


SMO：

- 修正 SMO 在伺服器定序區分大小寫時無法提取 AvailabilityReplica 屬性的問題 (因此，SSMS 可以顯示「無法繫結多部分識別碼 "a.delimited"」這類錯誤訊息。
- 修正 DatabaseScopedConfigurationCollection 類別中不正確地處理定序的問題 (因此，以滑鼠右鍵按一下在具有區分大小寫定序之伺服器上執行的資料庫時，在含土耳其文地區設定之 ma 電腦上執行的 SSMS 會顯示「舊版基數估計不是有效的範圍設定」這類錯誤)。
- 修正 JobServer 類別中 SMO 無法提取 SQL 2005 伺服器上 SQL Agent 屬性的問題 (因此，SSMS 將會擲回下列這類錯誤：「無法將預設值指派給區域變數。 必須宣告純量變數 "\@ServiceStartMode"，且最後不會在物件總管中顯示 SQL Agent 節點)。

範本： 

- "Database Mail"：已修正幾個拼字錯誤 [(https://feedback.azure.com/forums/908035/suggestions/33143512)](https://feedback.azure.com/forums/908035/suggestions/33143512)。  

物件總管：
- 已修正受控壓縮針對索引失敗的問題 (https://feedback.azure.com/forums/908035-sql-server/suggestions/32610058-ssms-17-4-error-when-enabling-page-compression-o)。

稽核：
- 修正「合併稽核檔案」功能問題。
<br>

### <a name="known-issues"></a>已知問題

資料分類：
- 移除分類後手動新增相同資料行的新分類，會導致要指派給主檢視中資料行的舊資訊類型和敏感性標籤。<br>
*因應措施*：將分類新增回主檢視之後並在儲存之前，指派新的資訊類型和敏感性標籤。


## <a name="downloadssdtmediadownloadpng-ssms-174httpsgomicrosoftcomfwlinklinkid864329"></a>![下載](../ssdt/media/download.png) [SSMS 17.4](https://go.microsoft.com/fwlink/?linkid=864329)
正式運作 | 組建編號：14.0.17213.0

[簡體中文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40a)


### <a name="whats-new"></a>新功能

**一般 SSMS**

弱點評定：
- 已加入新的 SQL 弱點評定服務，可在您的資料庫中掃描潛在的弱點和偏離最佳做法的項目，例如錯誤的設定、過多的權限和公開的機密資料。 
- 評定結果包含可以解決個別問題的可操作步驟，以及合適情況下的自訂補救指令碼。 您可以針對每個環境和特定需求來自訂評定報告。 於 [SQL 弱點評定](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment)深入了解。

SMO：
- 修正 HasMemoryOptimizedObjects 在 Azure 上擲回例外狀況的問題。
- 已加入新 CATALOG_COLLATION 功能的支援。

Always On 儀表板：
- 改進了可用性群組中延遲分析。
- 新增兩個報表：*AlwaysOn\_Latency\_Primary* 和 *AlwaysOn\_Latency\_Secondary*。

執行程序表：
- 已更新連結，以指向正確的文件。
- 允許直接從產生的實際計劃進行單一計劃分析。
- 新的圖示集。
- 已加入辨識 GbApply、InnerApply 等「套用邏輯運算子」的支援。
        
XE 分析工具：
- 已重新命名為 XEvent 分析工具。
- 停止/啟動功能表命令現在預設會停止/啟動工作階段。
- 已啟用鍵盤快速鍵 (例如，CTRL-F 可進行搜尋)。
- 已加入 database\_name 與 client\_hostname 動作至 XEvent 分析工具工作階段中適當的事件。 若要讓變更生效，您可能需要刪除伺服器上現有的 QuickSessionStandard 或 QuickSessionTSQL 工作階段執行個體 - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)

命令列：
- 新增新的命令列選項 ("-G")，可用來讓 SSMS 使用 Active Directory 驗證 (「整合式」或「密碼」)，自動連線至伺服器/資料庫。 如需詳細資訊，請參閱 [Ssms 公用程式](ssms-utility.md)。

匯入一般檔案精靈：
- 已加入在建立資料表時可以挑選結構描述名稱的方法，而不是只能使用預設值 ("dbo")。

查詢存放區：
- 已還原展開「查詢存放區」可用報告清單時的「迴歸查詢」報告。

**Integration Services (IS)**
- 已加入「部署精靈」中的套件驗證功能，以協助使用者了解 Azure-SSIS IR 中不支援的 SSIS 套件內元件。

### <a name="bug-fixes"></a>錯誤修正

**一般 SSMS**

- 物件總管：已修正資料庫快照集未顯示「資料表值函式」節點的問題 - [Connect 3140161](https://connect.microsoft.com/SQLServer/feedback/details/3140161)。
已改進當伺服器有 autoclose 資料庫時展開 *Databases* 節點的效能。
- 查詢編輯器：已修正 IntelliSense 針對沒有 master 資料庫存取權的使用者會失敗的問題。
已修正遠端電腦連線關閉時，在某些情況下會造成 SSMS 當機的問題 - [Connect 3142557](https://connect.microsoft.com/SQLServer/feedback/details/3142557)。
- XEvent 檢視器：已重新啟用匯出到 XEL 的功能。
已修正某些情況下使用者無法載入整個 XEL 檔案的問題。
- XEvent 分析工具：已修正當使用者沒有 *VIEW SERVER STATE* 權限時，造成 SSMS 當機的問題。
已修正關閉 [XE 分析工具即時資料] 視窗無法停止底層工作階段的問題。
- 已註冊的伺服器：修正 [移至...] 命令停止運作的問題 - [Connect 3142862](https://connect.microsoft.com/SQLServer/feedback/details/3142862) 和 [Connect 3144359](https://connect.microsoft.com/SQLServer/feedback/details/3144359/)。
- SMO：已修正 TransferData 方法在傳送物件上無法運作的問題。
已修正 Server 資料庫針對暫停的 SQL DW 資料庫擲回例外狀況的問題。
修正針對 SQL 資料倉儲撰寫 SQL 資料庫指令碼時，產生不正確 T-SQL 參數值的問題。
已修正編寫延伸資料庫指令碼時，不正確地發出 *DATA\_COMPRESSION* 選項的問題。
- 作業活動監視器：已修正使用者在嘗試依類別篩選時，出現「索引超出範圍。 必須為非負數且小於集合的大小。 
      參數名稱：index (System.Windows.Forms)」錯誤的問題 - [Connect 3138691](https://connect.microsoft.com/SQLServer/feedback/details/3138691)。
- 連線對話方塊：修正網域使用者沒有讀取/寫入網域控制站存取權時，無法使用 SQL 驗證登入 SQL Server 的問題 - [Connect 2373381](https://connect.microsoft.com/SQLServer/feedback/details/2373381)。
- 複寫：已修正當查看 SQL Server 中提取訂閱的屬性時，顯示類似「無法將值 'null' 套用至 ServerInstance 屬性」錯誤的問題。
- SSMS 安裝程式：已修正 SSMS 安裝程式不正確地造成電腦上所有已安裝產品重新設定的問題。
- 使用者設定：
   - 藉由此修正，Azure Government 使用者將可透過通用驗證和 Azure Active Directory 登入，使用 SSMS 持續存取其 Azure SQL Database 和 Azure Resource Manager 資源。  舊版 SSMS 使用者需要開啟 [工具]|[選項]|[Azure 服務]，並在 [資源管理] 下將 [Active Directory 授權單位] 屬性的設定變更為 https://login.microsoftonline.us。

**Analysis Services (AS)**

- 分析工具：已修正嘗試使用 Window 驗證對 Azure AS 進行連線的問題。
- 已修正在 1400 模型上取消連線詳細資料時造成當機的問題。
- 當重新整理認證時，在 [連接屬性] 對話方塊中設定 Azure Blob 索引鍵之際，現在會把它遮住不被看見。
- 已修正 [Azure Analysis Services 使用者選項] 對話方塊的問題，以便在進行搜尋時會顯示應用程式識別碼 GUID，而非物件識別碼。
- 已修正瀏覽資料庫\MDX 查詢設計工具工具列中，造成圖示不正確地對應部分按鈕的問題。
- 已修正使用 msmdpump IIS http/https 位址連線無法至 SSAS 的問題。
- [Azure Analysis Services 使用者選擇器] 對話方塊中的數個字串，現在已翻譯為更多種語言。
- 表格式模型中的資料來源現在可看見 MaxConnections 屬性。
- 部署精靈現在將針對 Azure AS 角色成員產生正確的 JSON 定義。
- 已修正在 SQL 分析工具中針對 Azure AS 選取 Windows 驗證時仍會提示登入的問題。



## <a name="downloadssdtmediadownloadpng-ssms-173httpsgomicrosoftcomfwlinklinkid858904"></a>![下載](../ssdt/media/download.png) [SSMS 17.3](https://go.microsoft.com/fwlink/?linkid=858904)
正式運作 | 組建編號：14.0.17199.0

[簡體中文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)


### <a name="enhancements"></a>功能增強

- 新增 [匯入一般檔案精靈]，其使用智慧型架構來簡化 CSV 檔案的匯入體驗，需要最少使用者介入或專業領域知識。 如需詳細資料，請參閱[匯入一般檔案至 SQL 精靈](../relational-databases/import-export/import-flat-file-wizard.md)。
- 已將 [XEvent Profiler] 節點新增至物件總管。 如需詳細資料，請參閱[使用 SSMS XEvent Profiler](../relational-databases/extended-events/use-the-ssms-xe-profiler.md)。
- 已更新效能儀表板等候歷程記錄報表中的等候篩選和分類。
- 已新增 "Predict" 函式的語法檢查。
- 已新增外部程式庫管理查詢的語法檢查。
- 已新增外部程式庫管理的 SMO 支援。
- 已將 [啟動 PowerShell] 支援新增至 [已註冊的伺服器] 視窗 (需要新的 SQL PowerShell 模組)。
- AlwaysOn：已新增對可用性群組的[唯讀路由支援](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)。
- 已將傳送追蹤詳細資料的選項新增至 [具 MFA 支援的 Active Directory - 通用] 登入的 [輸出] 視窗 (預設為關閉；需要在 [工具] > [選項] > [Azure 服務] > [Azure 雲端] > [ADAL 輸出視窗的追蹤層級] 下的 [使用者設定] 中開啟)。 
- 查詢存放區： 
  - 只要 QDS 已記錄任何資料，即使 QDS 處於 [關閉] 狀態，仍可存取 [查詢存放區] UI。
  - [查詢存放區] UI 現在會在所有現有的報表中公開等候分類。 這可讓客戶解除鎖定熱門等候查詢及更多案例。
- 已選擇性包括指令碼參數標頭 (預設為關閉；可在 [工具] > [選項] > SQL Server 物件總管 > [指令碼] > [包括指令碼參數標頭] 下的 [使用者設定] 中啟用)- [Connect 項目 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199)。
- 已移除 "RC" 商標。

### <a name="bug-fixes"></a>錯誤修正

**一般 SSMS**

- XEvent： 
   - 已修正 SSMS 只會開啟 .xel 檔案中部分事件的問題。
   - 已改善預設資料庫不是 'master' 時的「監看即時資料」體驗 - [Connect 項目 1222582](https://connect.microsoft.com/SQLServer/feedback/details/1222582)。
- 一律開啟：修正「還原記錄備份」可能因錯誤「在 LSN x 結束登入這個備份組，其太早套用至資料庫」而失敗的問題。
- 作業活動監視器：已修正不一致的圖示 - [Connect 項目 3133100](https://connect.microsoft.com/SQLServer/feedback/details/3133100)。
- 查詢存放區：修正使用者無法針對查詢存放區報表選擇「自訂」日期範圍的問題。 已連結至下列 Connect 項目。
   - [Connect 項目 3139842](https://connect.microsoft.com/SQLServer/feedback/details/3139842)
   - [Connect 項目 3139399](https://connect.microsoft.com/SQLServer/feedback/details/3139399)
- 修正連線對話方塊未「清除」最近使用之資料庫的問題；當儲存的資訊包含具名資料庫且使用者選取預設時，就會發生此問題。
- 物件指令碼：已修正「產生資料庫指令碼」無法運作並擲回錯誤的問題；當使用者在伺服器上有已暫停的 DW 資料庫，但選取了另一個非 DW 資料庫並嘗試對其進行指令碼處理時，就會發生此問題。
修正指令碼預存程序的標頭不符合指令碼設定，而導致可能造成誤導的指令碼問題 - [Connect 項目 3139784](https://connect.microsoft.com/SQLServer/feedback/details/3139784)。
已重新啟用目標為 SQL Azure 物件時的「指令碼按鈕」。
  修正 SSMS 不允許在某些物件 (UDF、檢視、SP、觸發程序) 上撰寫「改變」或「執行」指令碼的問題；當連線到 Azure SQL Database 時，就會發生此問題 - [Connect 項目 3136386](https://connect.microsoft.com/SQLServer/feedback/details/3136386)。
- 查詢編輯器：
  - 已改善目標為 Azure SQL Database 時的 IntelliSense。
  - 已修正查詢因驗證權杖 (通用驗證) 過期而失敗的問題。
  - 已改善針對 Azure SQL Database 使用時的 IntelliSense (特別是連接到 Azure SQL Database 時，將會使用最新的 T-SQL 文法 (140))。
  - 已修正開啟連接到伺服器上非 DataWarehouse 資料庫的查詢視窗，會導致該伺服器對 DataWarehouse 資料庫的所有後續查詢視窗擲回未支援類型/選項之各種相關錯誤的問題。
- 一律開啟：
   - 將植入模式資料行新增至 Always On 儀表板和 AG 屬性頁面。
   - 已修正主要在 Windows 上時無法建立 Linux AG 的問題 - [Connect 項目 3139856](https://connect.microsoft.com/SQLServer/feedback/details/3139856)。
- 已修正執行查詢時 SSMS 中的數種「記憶體不足」問題 - [Connect 項目 2845190](https://connect.microsoft.com/SQLServer/feedback/details/2845190)、[Connect 項目 3123864](https://connect.microsoft.com/SQLServer/feedback/details/3123864)。
- Profiler： 
   - 修正目標為 SQL 2005 時 Profiler 無法運作的問題。
   - 已修正 Profiler 不允許 [信任伺服器憑證] 連接選項的問題。
- 活動監視器：已修正活動監視器在指向 Linux 上執行的 SQL Server 時無法運作的問題。
- 已修正 SMO 傳送類別無法傳送外部資料來源或外部檔案格式物件的問題，這些類型的物件現在應該可以正確地包含在傳送中。
- 已註冊的伺服器：
   - 啟用 UA 伺服器的多伺服器查詢 (它會嘗試對群組中的每部 UA 伺服器使用相同的權杖)。
- AD 通用驗證：
   - 已修正不支援 Azure AD 驗證的問題。
   - 已修正資料表/檢視表設計工具無法運作的問題。
   - 已修正 [選取前 1000 個資料列] 和 [編輯前 200 個資料列] 無法運作的問題。
- 資料庫還原：已修正還原作業在將檔案移至其他位置時省略路徑中最後一個資料夾的問題。
- 壓縮精靈：
   - 修正為索引管理 [壓縮精靈] 的問題；修正 [壓縮資料精靈] 在 SQL 2016 和舊版中遭中斷的問題。
        https://connect.microsoft.com/SQLServer/feedback/details/3139342
   - 已將 [壓縮精靈] 新增至 Azure 資料表和索引。
- 執行程序表： 
   - 已修正無法辨識 PDW 運算子的問題。
- 伺服器屬性：
   - 已修正無法修改伺服器處理器親和性的問題。


**Analysis Services (AS)**

- 已修正 [部署精靈] 的一些問題來支援表格式 1400 相容性層級模型和 Power Query 資料來源。
- 從命令列執行時，[部署精靈] 現在可以部署至 AS Azure。
- 在 AS Azure 中使用 Windows 驗證時，使用者現在會在 [物件總管] 中看到正確的使用者帳戶名稱。


### <a name="known-issues-in-this-173-release"></a>此 17.3 版本的已知問題：

**一般 SSMS**

- 使用具 MFA 之 UA 的 Azure AD 驗證不支援下列 SSMS 功能：
   - Azure AD 驗證不支援 Database Engine Tuning Advisor；有一個已知問題，亦即向使用者呈現不太容易了解的錯誤訊息：「無法載入檔案或組件 'Microsoft.IdentityModel.Clients.ActiveDirectory'...」，而非預期的：「Database Engine Tuning Advisor 不支援 Microsoft Azure SQL Database。 (DTAClient)」。
- 嘗試分析 DTA 中的查詢會導致錯誤：「物件必須實作 IConvertible。 (mscorlib)」。
- 物件總管中報表的 [查詢存放區] 清單遺漏「迴歸查詢」。
   - 因應措施以滑鼠右鍵按一下 [查詢存放區] 節點，然後選取 [檢視迴歸查詢]。

**Integration Services (IS)**

- [catalog].[event_messagea] 中的 [execution_path] 不是 Scale Out 中正確的套件執行路徑。[execution_path] 會以 "\Package" 開頭，而不是套件可執行檔的物件名稱。 在 SSMS 中檢視套件執行的概觀報表時，[執行概觀] 中 [執行路徑] 的連結無法運作。 因應措施是按一下概觀報表中的 [檢視訊息] 以檢查所有事件訊息。


## <a name="downloadssdtmediadownloadpng-ssms-172httpsgomicrosoftcomfwlinklinkid854085"></a>![下載](../ssdt/media/download.png) [SSMS 17.2](https://go.microsoft.com/fwlink/?linkid=854085)
正式運作 | 組建編號：14.0.17177.0

[簡體中文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

### <a name="enhancements"></a>功能增強

- Multi-Factor Authentication (MFA)
  - 適用於具 Multi-Factor Authentication 的通用驗證 (具 MFA 的 UA) 的多使用者 Azure AD 驗證
  - 已針對具 MFA 的通用驗證新增使用者認證輸入欄位，以支援多使用者驗證。
- 連接對話方塊現在支援下列 5 種驗證方法：
  - Windows 驗證
  - SQL Server 驗證
  - Active Directory - 含 MFA 的通用支援
  - Active Directory - 密碼
  - Active Directory - 整合式

- DacFx 的資料庫匯入/匯出精靈現在可以使用具 MFA 的通用驗證。
- 如需 API 支援，請參閱 [IUniversalAuthProvider 介面](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx)。
- 具 MFA 的 Azure AD 通用驗證所使用的 ADAL Managed 程式庫已升級至 3.13.9 版。
- 此外，所提供 CLI 介面可支援 SQL Database 和 SQL 資料倉儲的 Azure AD 管理員設定。

 如需 Active Directory 驗證方法的詳細資訊，請參閱 [SQL Database 和 SQL 資料倉儲的通用驗證 (MFA 的 SSMS 支援)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) 和[設定適用於 SQL Server Management Studio 的 Azure SQL Database Multi-Factor Authentication](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure)。

- 輸出視窗包含在展開 [物件總管] 節點期間所執行查詢的項目
- Azure SQL Database 的已啟用檢視表設計工具
- SSMS 中從物件總管編寫物件指令碼的預設指令碼選項已變更：
  - 以前，新安裝上的預設值是讓產生的指令碼以最新版的 SQL Server (目前為 SQL Server 2017) 為目標。
  - 在 SSMS 17.2 中，已新增一個選項：[使指令碼設定與來源相符]。 設定為 True 時，產生的指令碼是以與從中編寫物件指令碼之伺服器相同的版本、引擎類型和引擎版本為目標。
  - [使指令碼設定與來源相符] 值預設為 *True*，讓新的 SSMS 安裝自動預設為一律將物件指令碼編寫成與原始伺服器相同的目標。
  - [使指令碼設定與來源相符] 值設定為 *False* 時，會啟用一般指令碼目標選項，並且運作方式與以前一樣。
此外，所有指令碼選項都已移至其專屬區段：[版本選項]。 它們不再位於 [一般指令碼選項] 下方。

- [從 URL 還原] 中已新增國內雲端支援
- QueryStoreUI 報表現在支援來自 sys.query_store_runtime_stats 的其他計量 (RowCount、DOP、CLR 時間等)。
- Azure SQL Database 現在支援 IntelliSense https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- 安全性：連接對話方塊將會預設為不信任伺服器憑證，並要求加密 Azure SQL DB 連接
- Linux 上 SQL Server 支援的一般改善：
 - 已回復 Database Mail 節點
 - 解決其他路徑相關問題
 - 活動監視器更為穩定
 - [連接屬性] 對話方塊會顯示正確平台
- 效能儀表板伺服器報表現在可作為預設報表：
  - 可以連接至 SQL Server 2008 和較新版本。
  - 遺漏索引子報表使用計分來協助識別最有用的索引。
  - 歷程記錄等候統計資料子報表現在會彙總為類別的等候。 預設已篩選出閒置和睡眠等候。
  - 新的閂鎖歷史記錄子報表。
- 執行程序表節點搜尋允許在計畫屬性中搜尋。 輕鬆地尋找任何運算子屬性，例如資料表名稱。 在檢視計畫時使用此選項：
  - 以滑鼠右鍵按一下計畫，並按一下內容功能表中的 [尋找節點] 選項
  - 使用 CTRL+F


**Analysis Services (AS)**

- 在 SSMS 的 AS Azure 模型中，沒有電子郵件地址之使用者的新 AAD 角色成員選擇

**Integration Services (IS)**

- 已將新的資料行 ([已執行的計數]) 新增至 SSIS 的執行報表

### <a name="known-issues-in-this-release"></a>此版本的已知問題：

- 在開啟一小時之後嘗試執行查詢時，使用「具 MFA 支援的 Active Directory - 通用」驗證的查詢視窗可能會發生與下列類似的錯誤：

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of ConnectRetryCount to increase the number of recovery attempts.`

   重新執行查詢應該可通過錯誤並成功。

- 使用具 MFA 之通用驗證的 Azure AD 驗證不支援下列 SSMS 功能：
  - [新增資料表/檢視] 設計工具會顯示舊式登入提示，並不適用於 Azure AD 驗證。
  - [編輯前 200 個資料列] 功能不支援 Azure AD 驗證。
  - [已註冊的伺服器] 元件不支援 Azure AD 驗證。
  - 不支援 **Database Engine Tuning Advisor** 進行 Azure AD 驗證。 有一個已知問題，亦即向使用者呈現不太有用的錯誤訊息：「無法載入檔案或組件 'Microsoft.IdentityModel.Clients.ActiveDirectory'...」，而非預期的「Database Engine Tuning Advisor 不支援 Microsoft Azure SQL Database。*(DTAClient)*.

**Analysis Services (AS)**

- SSAS 中的物件總管不會在 AS Azure 連接內容中顯示「Windows 驗證」使用者名稱。

### <a name="bug-fixes"></a>錯誤修正

- 修正在嘗試列印查詢結果 (文字格式) 時的問題。  如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3055225/
- 修正 SSMS 在 SQL Azure Database 上編寫這類物件刪除指令碼時不正確地卸除資料表和其他物件的問題。
- 修正 SSMS 偶而因下列這類錯誤而拒絕啟動的問題：「找不到一或多個元件。 請重新安裝該應用程式」。
- 修正 SSMS UI 中的 SPID 可能過時和不同步的問題。 https://connect.microsoft.com/SQLServer/feedback/details/1898875
- 修正將 /passive 引數視為 /quiet 的 SSMS (無訊息) 安裝程式問題。
- 修正 SSMS 偶而在啟動時擲回「物件參考未設定成物件的執行個體」錯誤的問題。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3134698
- 修正 [資料壓縮精靈] 上導致 SSMS 在 [圖形資料表] 上按 [計算] 時當機的問題
- 解決以滑鼠右鍵按一下資料表索引 (透過慢速的網際網路連線) 時的效能問題。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3120783
- 修正 SSMS 無法在具有區分大小寫定序之伺服器上列舉備份檔案的問題。 https://connect.microsoft.com/SQLServer/feedback/details/3134787 和 https://connect.microsoft.com/SQLServer/feedback/details/3137000
- 執行程序表和執行程序表比較綜合修正
- 修正除非已在執行 SSMS 的電腦上安裝 SQL Server，否則 [連接] 對話方塊不允許使用者指定 [網路通訊協定] 用於連接的問題。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3134997
- 改善在「隨機」位置上顯示某個 SSMS 對話方塊的多監視器組態支援。 已在 [SQL Server 物件總管 | 命令] 使用者設定下新增選項 [工作對話方塊]，允許記住工作對話方塊或屬性工作表在關閉時的位置。 https://connect.microsoft.com/SQLServer/feedback/details/889169、 https://connect.microsoft.com/SQLServer/feedback/details/1158271、 https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- 修正 SSMS 無法變更加密 Azure SQL DB 之 DB 內容的問題
- 改善 [執行之後捨棄結果] 選項。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/1196581
- 改善/修正使用者無法存取他們不是系統管理員之 Azure 訂用帳戶的問題。
- 改善 [資料庫還原精靈] 以在 OE 中持續選取目標資料庫，不論是否選取來源資料庫。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3118581
- 修正物件總管未排序錯誤新增之「原生編譯的預存程序」的問題。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3133365
- 修正 [選取前 n 個資料列] 未包含 "TOP" 子句的問題。 適用於 Azure SQLDW。 https://connect.microsoft.com/SQLServer/feedback/details/3133551 和 https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI：修正非自訂時間間隔未正確地作用於所有報表的問題。
- Always Encrypted：改善 [新增資料行主要金鑰] 對話方塊中 AKV 權限狀態的傳訊。將工具提示新增至 CEK 下拉式清單，以更輕鬆地區別具有完整名稱的 CEK。修正未針對 Always Encrypted 將某些 CNG 金鑰存放區提供者顯示在 [新增資料行主要金鑰] 對話方塊中的問題
- 修正 SSMS 連接的不一致「應用程式名稱」。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3135115
- 修正 SSMS 未產生 SQL Azure 之正確指令碼的問題 (使用 DATA_COMPRESSIONS 選項的資料表和索引)。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3133148
- 修正問題：使用者無法使用 CTRL+Q 快速鍵進行快速啟動 (注意：在 [查詢編輯器] 中切換 [IntelliSense 已啟用] 選項的新按鍵繫結關係現在是 CTRL+B、CTRL+I)。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3131968
- 修正 [還原資料庫] 中 SSMS 在嘗試從具有已定義自訂網域之帳戶的訂閱中選取儲存體帳戶時擲回例外狀況的問題
- 修正 [資料庫圖表] 中 SSMS 擲回「索引在陣列的界限之外」錯誤的問題；而且，使用者無法將 [資料表檢視] 變更為任何項目，只能變更為標準。 https://connect.microsoft.com/SQLServer/feedback/details/3133792 和 https://connect.microsoft.com/SQLServer/feedback/details/3135326
- 修正 [備份/還原至 URL] 中 SSMS 未列舉傳統儲存體帳戶的問題。
- 修正嘗試將結構描述繫結安全性實體新增至 DB 角色時擲回例外狀況的問題。 如何：使用資料來源檢視精靈來定義資料來源檢視 (Analysis Services)https://connect.microsoft.com/SQLServer/feedback/details/3118143
- 修正 SSMS 間歇地顯示下列錯誤的問題：「資料為 Null」。 無法在值為 Null 的情況下呼叫這個方法或屬性。」 展開資料表節點時 https://connect.microsoft.com/SQLServer/feedback/details/3136283
- DTA：修正在評估具有特定界限值的資料分割函數時，DTAEngine.exe 因堆積損毀而終止的問題。


**Analysis Services (AS)**

- 修正 DB 的名稱和識別碼不同時，[AS 還原資料庫] 因錯誤而失敗的問題
- 修正導致 DAX 查詢視窗捨棄切換 [IntelliSense 已啟用] 之功能表選項的問題
- 修正避免透過 msmdpump IIS http/https 位址連接至 SSAS 的問題
- 允許使用包含分號的密碼連線到 AS Azure
- 與 SQL Server 2017 AS 伺服器或 AS Azure 搭配使用時，具有 [略過成員資格] 選項的 [正在產生 AS 還原資料庫的指令碼] 命令會包含新的對應 JSON 選項
- 修正導致刪除資料庫對話方塊在載入時引發錯誤的極罕見問題
- 修正嘗試檢視包含混用 SQL 查詢和 M 資料分割定義的 1400 相容性層級模型中的資料分割時可能發生的問題

**Integration Services (IS)**
- 修正無法顯示 SSISDB 目錄之執行資訊報表的問題
- 解決 SSMS 中大量專案/套件之效能不良的相關問題

## <a name="downloadssdtmediadownloadpng-ssms-171httpsgomicrosoftcomfwlinklinkid849819"></a>![下載](../ssdt/media/download.png) [SSMS 17.1](https://go.microsoft.com/fwlink/?linkid=849819)
正式運作 | 組建編號：14.0.17119.0

[簡體中文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

### <a name="enhancements"></a>功能增強

- Profiler：[說明] > [關於] 現在會顯示發行版本號碼 (例如 17.1)
- 分析服務使用者可以從資料來源的內容功能表，針對 1200 TM 模型和更高版本重新整理其資料來源的認證
- 內建的 SSIS 報表現在顯示 CTP 2.1 中 SSIS 向外延展執行的記錄
- SSIS 向外延展管理應用程式
  - 檢視向外延展 master 的基本資訊。
  - 輕鬆地將背景工作角色加入向外延展部署。
  - 檢視所有的向外延展背景工作角色和基本相關資訊，也可以輕鬆地進行啟用或停用。

### <a name="bug-fixes"></a>錯誤修正
- 一律開啟：
  - 已修正下列問題：可用性複本的屬性一律顯示為 WSFC AG 的「自動容錯移轉」模式。
  - 已修正下列問題：更新可用性群組時，覆寫了唯讀的路由清單
- 永遠加密：已修正下列問題：產生的記錄檔遺漏了 DacFx 所產生的資訊。
- 執行程序表：修正下列問題：UI 一律顯示非自適性聯結運算子的實際聯結類型屬性。
- 安裝程式：
  - 已修正下列問題：SSMS 17.0 已在 Visual Studio 2013 上中斷 SSDT [連接項目 3133479]
  - 已修正下列問題：按一下安裝程式結尾處的 [重新啟動]，並不會重新啟動電腦
- 指令碼：藉由停用該選項，在嘗試指令碼刪除時防止 SSMS 意外刪除 Azure 資料庫物件。  正確的修復程式將位於即將發佈的 SSMS 版本中。
- 物件總管：已修正下列問題：連接至使用 "AS COPY" 建立的 Azure 資料庫時，「資料庫」節點未展開

## <a name="downloadssdtmediadownloadpng-ssms-170httpsgomicrosoftcomfwlinklinkid847722"></a>![下載](../ssdt/media/download.png) [SSMS 17.0](https://go.microsoft.com/fwlink/?LinkID=847722)
正式運作 | 組建編號：14.0.17099.0

[簡體中文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40a)

### <a name="enhancements"></a>功能增強 

- 升級套件和 Windows Software Update Services (WSUS) 未來的 17.X 版包含較小的累積更新套件 
  - 更新封裝也將發佈至 WSUS 目錄  
- 圖示更新：圖示已更新為與 VS Shell 所提供圖示一致，而且支援高 DPI 解析度、新的 SSMS 和 Profiler 程式圖示，以區分 16.X 和 17.X 版
- SQL PowerShell 模組
  - SQL Server PowerShell 模組已從 SSMS 中移除，現在是透過 PowerShell 資源庫 (目前需要有 PowerShell 5.0 才能支援模組版本設定) 提供
  - 針對某些 SMO 物件呈現方式 (格式化) 的其他改進 (例如，資料庫現在會顯示大小及可用空間，且資料表會顯示資料列計數和空間使用量)
  - 新增從 OE 中的 [啟動 PowerShell] 功能表叫用 PowerShell 命令提示字元時的顏色標示
  - 新增 -ClusterType 和 -RequiredCopiesToCommit 參數至 AG Cmdlet (New-SqlAvailabilityGroup、Join-SqlAvailabilityGroup 及 Set-SqlAvailabilityGroup Cmdlet)
  - 新增參數 -ActiveDirectoryAuthority 和 -AzureKeyVaultResourceId 至 Add-SqlAzureAuthenticationContext Cmdlet
  - 新增 Revoke-SqlAvailabilityGroupCreateAnyDatabase、Grant-SqlAvailabilityGroupCreateAnyDatabase 和 Set-SqlAvailabilityReplicaRoleToSecondary Cmdlet
  - 將 -seedingMode 參數新增至 Set-SqlAvailabilityReplica 和 New-SqlAvailabilityReplica Cmdlet
  - 在 Get-SqlDatabase 中新增 -ConnectionString 參數
- Linux 上的 SQL Server：記錄傳送的一般改善和修正
  - 新增原生 Linux 路徑附加、還原和備份資料庫的支援
  - 新增原生 Linux 路徑對稽核記錄目的地資料夾的支援
- Analysis Services
  - XMLA 查詢視窗：
    - 編輯器中的括號匹配
    - DEFINE MEASURE 和 DEFINE VAR 語法支援
    - 各種 Intellisense 增強功能
  - 通用驗證
    - 允許使用者指定使用者名稱和任何密碼，而 [Azure 登入] 對話方塊會處理連線
  - SSMS PQ 整合： 
    - 結構化資料來源的指令碼可運作 
    - 在 PQ UI 中檢視及編輯結構化資料來源
- 新的「加入唯一條件約束」範本
- 執行程序表：在已耗用時間的屬性視窗中顯示所有執行緒的最大值，而非加總、公開新的記憶體授與運算子屬性、啟用 [即時查詢統計資料] 中的 [編輯查詢] 按鈕、支援交錯執行
  - [分析實際執行計畫] 的新選項
  - 執行程序表比較的一般增強功能
  - 執行程序表比較功能中引進了功能，以找出兩個查詢計劃的相符節點之間，基數估計的顯著差異，並執行可能根本原因的基本分析
- 移除「已註冊的伺服器總管」中的 [組態管理員]
- 啟用讀取來自 Azure Blob 儲存體的稽核記錄
- 為 Always Encrypted 新增參數化，如需詳細資料，請參閱[此頁面](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/) 
- 目標為 Azure SQL DB 的 AAD 通用驗證連線支援自訂租用戶識別碼 
- 為 Azure SQL Database 產生指令碼，現在可編寫全文、規則及資料庫指令碼
- 修正 SSMS 和 Profiler 啟動顯示畫面的商標
- 從 SSMS 移除公用程式控制點 UI
- SSMS 現在可以建立 "PremiumRS" 版本的 SQL Azure 資料庫
- AlwaysOn 可用性群組
  - 新增新叢集類型的支援：EXTERNAL 和 NONE。新增 Linux 上的 SQL Server 支援。新增自動植入作為初始資料同步的選項。修正一些缺陷，例如端點 URL 處理、資料庫重新整理和 UI 配置。移除 Azure 複本相關功能
  - 改進 IntelliSense 的數個可用性群組關鍵字
- 活動監視器
  - 在 [SSMS 輸出]視窗中新增新的 [活動監視器] 窗格
  - 變更連線錯誤/逾時訊息，將資訊記錄到輸出視窗，而不是快顯訊息
  - 移除 [概觀] 區段中的空白圖表 (第 5 個圖表)
  - 已暫停活動監視器資料收集時，在概觀標題中新增 (暫停)
  - SQL Server 的圖形延伸模組：適用於圖形節點和邊緣資料表的新圖示、圖形節點和邊緣資料表將顯示在圖形資料表資料夾之下、用來建立圖形節點和邊緣資料表的範本
- 簡報模式 3 個可透過快速啟動 (Ctr-Q) 使用的新工作 PresentOn - 開啟簡報模式 PresentEdit - 編輯簡報模式的簡報字型大小。  查詢編輯器的「文字編輯器字型」。  其他組件的「環境字型」。
RestoreDefaultFonts - 還原至預設設定。
*注意：目前沒有 PresentOff 命令。請使用 RestoreDefaultFonts 來關閉簡報模式*

### <a name="bug-fixes"></a>錯誤修正

- 修正透過 Surface Book 觸控板捲動執行程序表時 SSMS 當機的問題
- 修正 SSMS 在取得所還原或離線資料庫的屬性時，長時間停止回應的問題 
- 修正「說明檢視器」無法在 RC 組建中開啟的問題
- 修正 SSMS 中可能遺失「維護計畫工作工具箱」項目的問題。
- 修正 SSMS 中當資料庫名稱包含大括號時，使用者無法壓縮資料庫的問題。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3122618)
- 修正 SSMS 嘗試撰寫指令碼以刪除 Azure 資料庫時，實際上造成刪除資料庫本身的問題。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3131458/)
- 修正預設值沒有針對使用者定義資料表類型撰寫指令碼的問題。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3119027)
- 針對索引上操作功能表的另一輪效能改進。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3120783)
- 修正當滑鼠游標暫留在執行計畫中的遺失索引上時，會造成過度閃爍的問題。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3118510)
- 修正 SSMS 在編寫指令碼時會使 DB 離線的問題 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3118550)
- SSMS 當地語系化 (非英文) 版本的其他 UI 修正。
- 修正以 SQL 2016 SP1 Standard Edition 為目標時，[Always Encrypted 金鑰] 節點會遺失的問題。
- Always Encrypted：當以 SQL 2016 RTM Standard Edition 或任何 SQL 2014 (及以下) 伺服器為目標時，[Always Encrypted] 功能表會不正確地啟用。修正當使用 CREATE OR ALTER 語法時，IntelliSense 會報告錯誤的問題。修正當 CMK/CEK 中包含需要逸出 (例如以括弧括住) 的字元時，加密會失敗的問題。當 SSMS 中出現「記憶體不足」例外狀況時，使用者會看到建議改用原生 (64 位元) PowerShell 的錯誤。
修正當使用者使用資源群組管理員訂用帳戶，而不是使用傳統 Azure 訂用帳戶時，AE 精靈會失敗的問題、修正當使用者在訂用帳戶中沒有任何權限或 Azure 金鑰保存庫時，AE 精靈會顯示不正確錯誤的問題。
修正在 AE 精靈具有多個 AAD 的情況下，Azure Key Vault 登入頁面不會顯示 Azure 訂用帳戶的問題、修正在 AE 精靈中，Azure Key Vault 登入頁面不會顯示使用者具有讀取權限的 Azure 訂用帳戶問題
  - 修正目前可能不會載入資源檔，因此導致錯誤訊息不正確的問題
- 改進 SSMS 安裝頁面上超連結的對比
- 修正連線到 SQL Server Express (2016 SP1) 時不會顯示 PolyBase 節點的問題
- 修正 SSMS 無法將 Azure 資料庫的 [相容性層級] 變更為 [v140] 的問題
- 改進 [物件總管] 在展開 Azure 資料庫清單時的效能 [Connect 項目 (英文)](https://connect.microsoft.com/SQLServer/feedback/details/3100675)
- 修正 [檢視 SQL Server 記錄檔] 操作功能表項目針對非關聯式伺服器類型 (AS\RS\IS) 會不正確顯示的問題 
- 修正使用 SQL 驗證檢查 Analysis Services 分割區查詢的語法時，可能會導致出現登入失敗訊息的問題
- 修正在 SSMS 中重新命名預覽 1400 相容性層級 AS 表格式模型會導致失敗的問題
- 修正在 AS 伺服器上嘗試無效作業之後，在罕見情況下可能會產生「模型上作業失敗」的問題，並在無法成功於模型上儲存之後還原本機變更
- 修正 [Analysis Services 同步處理資料庫] 快顯對話方塊中的錯字
- 在多個監視器安裝程式的畫面上，看不到備份/還原容器對話方塊。 
- 如果目標物件名稱中有 `]`，SecurityPolicy，則建立會失敗。
- SSMS 2016 [開啟最近使用的項目] 功能表未顯示最近儲存的檔案。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)
- 移除 VS Shell 更新時，使用者設定的重設。
- 修正導致使用者無法在 SQL Server 2017 上變更資料庫相容性層級的問題。
- 使用 AAD 通用驗證的查詢視窗在一小時後無法重新整理查詢。
- 公用程式控制點 UI 已從 SSMS 移除。
- AD 通用驗證連線在初始權杖過期後無法查詢資料。
- 無法將 Rules from Azure SQL DB 編碼為 Azure SQL DB。
- 修正 SQL PowerShell 無法連線舊版 SQL 執行個體 (2014 及更早版本) 的問題。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)
- 修正在 SSMS 無法匯入註冊的伺服器時造成損毀的問題。
- 修正如果使用者有資料庫的特定權限，會造成 SSMS 當機的問題。
- SSMS - 在檢閱檢視時，資料表會從設計介面消失。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views) 
- 資料表捲軸不允許使用者捲動資料表內容，只有向上/下箭號允許這個動作。 也有可能在嘗試使用捲軸捲動後，捲動資料表內容，而這是一項 Bug。 [Connect 項目](
https://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view) 
- 註冊的伺服器在重新整理根節點後未顯示圖示。
- Azure v12 伺服器上 [建立資料庫] 的指令碼按鈕會執行指令碼，然後顯示訊息「沒有要編寫指令碼的動作」。
- SSMS [連接到伺服器] 對話方塊未清除每個新連線的 [其他屬性] 索引標籤。
- [產生工作] 指令碼未為 Azure SQL DB 產生 [建立資料庫] 指令碼。
- 檢視設計工具中的捲軸顯示為已停用。
- Always Encrypted AVK 金鑰路徑未包含版本識別碼。
- 減少查詢視窗中的引擎版本查詢數。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3113387)
- 未正確處理加密後來自重新整理模組的 Always Encrypted 錯誤。
- 將 OLTP 與 OLAP 的預設連線逾時從 15 秒變更為 30 秒，以修正略過連線的這類失敗。 
- 修正自訂報表啟動時，SSMS 中的損毀。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3118856)
- 已修正在 Azure SQL 資料庫中「產生指令碼...」會失敗的問題。
- 修正 [編寫指令碼為] 及 [產生指令碼精靈]，不要在編寫預存程序等物件的指令碼時新增額外新行。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3115850)
- SQLAS PowerShell 提供者：將 LastProcessed 屬性新增至 Dimension 和 MeasureGroup 資料夾。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3111879)
- 即時查詢統計資料：修正其只顯示批次中第一個查詢的問題。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- 執行程序表：在視窗中顯示執行緒的最大值，而非加總。
- 查詢存放區：對具有高執行變化的查詢新增報表。
- [物件總管] 效能問題：[Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3114074)。資料表的操作功能表會短暫停止回應。SSMS 在以滑鼠右鍵按一下資料表索引時 (透過遠端 (網際網路) 連線) 很緩慢。 避免發行依伺服器排序的資料表查詢
- 從 SSMS 移除 Azure 部署精靈 (將資料庫部署到 Azure VM)
- 修正遺漏的索引未在 SSMS 中的執行計劃顯示的問題 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3114194)
- 修正 SSMS 中常見的關機時當機問題
- 修正在 [物件總管] 中於 PolyBase|向外延展群組節點上帶出操作功能表時發生錯誤的問題 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3115128)
- 修正 SSMS 可能在嘗試顯示資料庫權限時損毀的問題
- 查詢存放區：在操作功能表項目中，為查詢存放區報表的結果方格進行一般功能增強
- 為現有資料表設定 Always Encrypted 失敗，不相關的物件發生錯誤。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3103181)
- 無法為具有多個結構描述的現有資料庫設定 Always Encrypted。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3109591)
- Always Encrypted、加密資料行精靈失敗，原因是資料庫包含參考系統檢視的檢視。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3111925)
- 使用 Always Encrypted 進行加密時，未正確處理加密後來自重新整理模組的錯誤。
- 修正 [新增伺服器註冊] 對話方塊上的 UI 截斷問題
- 修正 DMF 條件 UI 未正確更新其字串常值中有引號的運算式
- 修正執行自訂報表時可能造成 SSMS 損毀的問題
- 將 [Scale Out 中的執行...] 功能表項目新增至資料夾節點
- 修正 Azure SQL DB 防火牆允許清單 IP 地址功能的問題
- 修正 SSMS 中在編輯 AS 多維磁碟分割來源時，導致物件參考未設定例外狀況的問題
- 修正 SSMS 中從多維 AS 伺服器刪除客戶組件時，導致物件參考未設定例外狀況的問題
- 修正重新命名 AS 表格式 1400 資料庫失敗的問題
- 修正從 [連線屬性] 對話方塊中，為 1400 相容性層級 AS 表格式資料來源撰寫指令碼的問題
- 移除 AS 1400 相容性層級模型中的資料表至少有一個資料分割的假設
- Ctrl-R 現在可於 SSMS DAX 查詢編輯器中切換結果窗格


## <a name="downloadssdtmediadownloadpng-ssms-1653httpsgomicrosoftcomfwlinklinkid840946"></a>![下載](../ssdt/media/download.png) [SSMS 16.5.3](https://go.microsoft.com/fwlink/?LinkID=840946)
正式運作 | 組建編號：13.0.16106.4

[簡體中文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)

這個版本已修正下列問題：

* 修正 SSMS 16.5.2 中出現的問題，這造成 'Table' 節點會在資料表有多個疏鬆資料行時展開。

* 使用者可以將包含 OData 連線管理員且連線到 Microsoft Dynamics AX/CRM Online 資源的 SSIS 套件部署到 SSIS 目錄。 如需詳細資訊，請參閱 [OData 連線管理員](../integration-services/connection-manager/odata-connection-manager.md)。

* 在現有資料表上設定 Always Encrypted 失敗，不相關的物件發生錯誤。 [Connect 識別碼 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* 無法為具有多個結構描述的現有資料庫設定 Always Encrypted。 [Connect 識別碼 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* Always Encrypted、加密資料行精靈失敗，原因是資料庫包含參考系統檢視的檢視。 [Connect 識別碼 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* 使用 Always Encrypted 進行加密時，未正確處理加密後來自重新整理模組的錯誤。

* 「開啟最近使用的項目」功能表未顯示最近儲存的檔案。 [Connect 識別碼 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS 在以右鍵按一下資料表索引時 (透過遠端 (網際網路) 連線) 很緩慢。 [Connect 識別碼 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)
 
* 修正 SQL Designer 捲軸的問題。 [Connect 識別碼 3114856](https://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* 資料表的操作功能表會短暫停止回應 
 
* SSMS 有時會擲回活動監視器的例外狀況及損毀。 [Connect 識別碼 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* SSMS 2016 會損毀，並出現錯誤「處理序因位於 IP 71AF8579 (71AE0000) 的 .NET 執行階段發生內部錯誤而終止，錯誤碼為 80131506」


## <a name="uninstall-and-reinstall-ssms-17x"></a>解除並重新安裝 SSMS 17.x

如果您的 SSMS 安裝遇到問題，而且無法經由標準的解除並重新安裝來解決，您可以先嘗試[修復](https://support.microsoft.com/help/4028054/windows-10-repair-or-remove-programs) Visual Studio 2015 IsoShell。 若修復 Visual Studio 2015 IsoShell 未解決問題，下列幾個步驟可以修正許多非特定的問題：

1.  以您解除安裝任何應用程式的相同方式，解除安裝 SSMS (使用 [應用程式與功能]、[程式與功能] 等，取決於您的 Windows 版本)。

2.  **從提升權限的命令提示字元**解除安裝 Visual Studio 2015 IsoShell：
   
    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```

    ```vs_isoshell.exe /Uninstall /Force /PromptRestart```

3.  以您解除安裝任何應用程式的相同方式，解除安裝 Microsoft Visual C++ 2015 可轉散發套件。 若電腦上有 x86 及 x64，則兩者都解除安裝。

4.  **從提升權限的命令提示字元**重新安裝 Visual Studio 2015 IsoShell：  

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```  
 
    ```vs_isoshell.exe /PromptRestart```

5.  重新安裝 SSMS。

6.  若您目前不是最新狀態，請升級為[最新版的 Visual C++ 2015 可轉散發套件](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)。


## <a name="additional-downloads"></a>其他下載  
如需所有 SQL Server Management Studio 的下載清單，請搜尋 [Microsoft 下載中心](https://www.microsoft.com/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending)。  
  
若要取得最新版的 SQL Server Management Studio，請參閱[下載 SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md)。  
