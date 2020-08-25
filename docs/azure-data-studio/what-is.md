---
title: 什麼是 Azure Data Studio
description: Azure Data Studio 是在 Windows、macOS 和 Linux 上執行，以便管理 SQL Server、Azure SQL Database 和 Azure SQL 資料倉儲的免費輕量型工具。
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: overview
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18, sqlfreshmay19
ms.date: 01/15/2020
ms.openlocfilehash: b58a54e99c269db113bdd1e1821ba55ce3d83ff5
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "88765507"
---
# <a name="what-is-azure-data-studio"></a>什麼是 Azure Data Studio？

Azure Data Studio 是跨平台資料庫工具，適合在 Windows、macOS 和 Linux 上使用 Microsoft 系列內部部署和雲端資料平台的資料專業人員。

Azure Data Studio 提供新式編輯器體驗，其中包含 IntelliSense、程式碼片段、原始檔控制整合及整合式終端。 在工程設計時，考量到資料平台使用者，並內建查詢結果集的圖表和可自訂的儀表板。

Azure Data Studio 及其提供者的原始程式碼根據原始程式碼 EULA 提供在 GitHub 上，該合約提供修改和使用軟體的權限，但不能在雲端服務中進行重新散發或裝載。 如需詳細資訊，請參閱 [Azure Data Studio 常見問題集](faq.md)。

**[下載並安裝 Azure Data Studio](./download-azure-data-studio.md?view=sql-server-ver15)**

## <a name="sql-code-editor-with-intellisense"></a>具備 IntelliSense 的 SQL 程式碼編輯器

Azure Data Studio 提供新式、以鍵盤為主的 SQL 程式碼撰寫體驗，利用多個索引標籤視窗、豐富的 SQL 編輯器、IntelliSense、關鍵字完成、程式碼片段、程式碼導覽和原始檔控制整合 (Git) 等內建功能，讓您能夠輕鬆執行日常工作。 執行隨選 SQL 查詢、檢視結果並將其儲存為文字、JSON 或 Excel。 在熟悉的物件瀏覽體驗中編輯資料、管理您慣用的資料庫連線，以及瀏覽資料庫物件。 若要了解如何使用 SQL 編輯器，請參閱[使用 SQL 編輯器建立資料庫物件](tutorial-sql-editor.md)。

## <a name="smart-sql-code-snippets"></a>智慧型 SQL 程式碼片段

SQL 程式碼片段會產生適當的 SQL 語法，來建立資料庫、資料表、檢視、預存程序、使用者、登入、角色，以及更新現有的資料庫物件。 使用智慧型程式碼片段，快速建立資料庫的複本以供進行開發或測試，以及產生和執行 CREATE 和 INSERT 指令碼。

Azure Data Studio 也提供建立自訂 SQL 程式碼片段的功能。 若要深入了解，請參閱[建立和使用程式碼片段](code-snippets.md)。

## <a name="customizable-server-and-database-dashboards"></a>可自訂的伺服器和資料庫儀表板

建立可自訂的豐富儀表板來監視資料庫效能瓶頸，並針對這些瓶頸進行快速疑難排解。 若要了解深入解析小工具，以及資料庫 (和伺服器) 儀表板，請參閱[使用深入解析小工具管理伺服器和資料庫](insight-widgets.md)。

## <a name="connection-management-server-groups"></a>連線管理 (伺服器群組)

伺服器群組可讓您管理所使用的伺服器和資料庫連線資訊。 如需詳細資訊，請參閱[伺服器群組](server-groups.md)。

## <a name="integrated-terminal"></a>整合式終端

在 Azure Data Studio 使用者介面的整合式終端視窗中，使用您慣用的命令列工具 (例如 Bash、PowerShell、sqlcmd、bcp 與 ssh)。 若要了解整合式終端，請參閱[整合式終端](integrated-terminal.md)。

## <a name="extensibility-and-extension-authoring"></a>擴充性和延伸模組撰寫

透過擴充基底安裝的功能來增強 Azure Data Studio 體驗。 Azure Data Studio 提供資料管理活動的擴充點，以及對於延伸模組撰寫的支援。

若要了解 Azure Data Studio 中的擴充性，請參閱[擴充性](extensibility.md)。
若要了解如何撰寫延伸模組，請參閱[延伸模組撰寫](extension-authoring.md)。

## <a name="feature-comparison-with-sql-server-management-studio-ssms"></a>與 SQL Server Management Studio (SSMS) 的功能比較

**在下列情況下使用 Azure Data Studio：**

- 需要在 macOS 或 Linux 上執行
- 正在連線到 SQL Server 2019 巨量資料叢集
- 將大部分的時間花在編輯或執行查詢
- 需要能夠快速繪製圖表和視覺化結果集
- 可以使用 sqlcmd 或 Powershell 透過整合式終端執行大部分的管理工作
- 對精靈體驗的需求最少
- 不需要深層管理設定

**在下列情況下使用 SQL Server Management Studio：**

- 將大部分的時間花在資料庫管理工作
- 正在執行深層管理設定
- 正在執行安全性管理，包括使用者管理、弱點評定，以及安全性功能的設定
- 使用 SQL Server 查詢存放區的報表
- 需要使用效能調整建議程式和儀表板
- 正在執行 DACPAC 的匯入/匯出
- 需要存取已註冊的伺服器，並想要控制 Windows 上的 SQL Server 服務

### <a name="shell"></a>殼層

|功能|Azure Data Studio|SSMS|
|:---|:---|:---|
|Azure 登入|是|是|
|儀表板|是||
|延伸模組|是||
|整合式終端|是||
|物件總管|是|是|
|物件指令碼|是|是|
|專案系統|是||
|從資料表選取|是|是|
|原始程式碼控制|是||
|工作窗格|是||
|佈景主題|是||
|深色模式|是||
|Azure 資源總管|預覽||
|產生指令碼精靈||預覽|
|匯入/匯出 DACPAC||是|
|物件屬性||預覽|
|資料表設計工具||是|

### <a name="query-editor"></a>查詢編輯器

|功能|Azure Data Studio|SSMS|
|:---|:---|:---|
|圖表檢視器|是||
|將結果匯出至 CSV、JSON、XLSX|是||
|IntelliSense|是|是|
|程式碼片段|是|是|
|顯示計畫|預覽|是|
|用戶端統計資料||是|
|即時查詢統計資料||是|
|查詢選項||是|
|將結果存檔||是|
|以文字顯示結果||是|
|空間檢視器||是|
|SQLCMD||是|
|Notebooks|是||
|將查詢儲存為程式碼片段|是||

### <a name="operating-system-support"></a>作業系統支援

|功能|Azure Data Studio|SSMS|
|:---|:---|:---|
|Linux|是||
|macOS|是||
|Windows|是|是|

### <a name="data-engineering"></a>資料工程

|功能|Azure Data Studio|SSMS|
|:---|:---|:---|
|建立外部資料表精靈|是||
|HDFS 整合|是||
|Notebooks|是||

### <a name="database-administration"></a>資料庫管理

|功能|Azure Data Studio|SSMS|
|:---|:---|:---|
|備份 / 還原|是|是|
|巨量資料叢集支援|是||
|一般檔案匯入|預覽|是|
|SQL Agent|預覽|是|
|SQL Profiler|預覽|是|
|永遠開啟||是|
|Always Encrypted||是|
|複製資料精靈||是|
|Database Engine Tuning Advisor||是|
|錯誤記錄檔檢視器||是|
|維護計畫||是|
|多伺服器查詢||是|
|原則式管理||是|
|PolyBase||是|
|查詢存放區||是|
|已註冊的伺服器||是|
|複寫||是|
|安全性管理||是|
|Service Broker||是|
|SQL Mail||是|
|範本總管||是|
|弱點評量||是|
|XEvent 管理||是|
|SQL 評定 API 整合||是|

## <a name="next-steps"></a>後續步驟

- [下載並安裝 Azure Data Studio](./download-azure-data-studio.md?view=sql-server-ver15)
- [連線及查詢 SQL Server](quickstart-sql-server.md)
- [連線及查詢 Azure SQL Database](quickstart-sql-database.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]