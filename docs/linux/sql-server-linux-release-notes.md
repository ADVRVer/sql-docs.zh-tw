---
title: "在 Linux 上的 SQL Server 2017 的版本資訊 |Microsoft 文件"
description: "本主題包含的版本資訊，並支援在 Linux 上執行的 SQL Server 2017 的功能。 版本資訊會包含以 RC2 和先前版本。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/07/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: baa5826e9722bfb23afacf729d80bebf88985ed3
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>在 Linux 上的 SQL Server 2017 的版本資訊

下列版本資訊適用於 SQL Server 2017 在 Linux 上執行。 這個版本支援 SQL Server database engine 功能的許多 for Linux。 下列主題會分成區段，每個版本中，從最新版本，也就是 RC2。 請參閱每個支援的平台、 工具、 功能和已知的問題的章節中的資訊。

下表列出本主題中涵蓋的 SQL Server 2017 的發行版本。

| 版本 | 版本 | 發行日期 |
|-----|-----|-----|
| [RC2](#RC2) | 14.0.900.75 | 8-2017 |
| [RC1](#RC1) | 14.0.800.90 | 7-2017 |
| [CTP 2.1](#ctp21) | 14.0.600.250 | 5-2017 |
| [CTP 2.0](#ctp20) | 14.0.500.272 | 4-2017 |
| [CTP 1.4](#ctp14) | 14.0.405.198 | 3-2017 |
| [CTP 1.3](#ctp13) | 14.0.304.138 | 2-2017 |
| [CTP 1.2](#ctp12) | 14.0.200.24 | 1-2017 |
| [CTP 1.1](#ctp11) | 14.0.100.187 | 12-2016 |
| [CTP 1.0](#ctp10) | 14.0.1.246 | 11-2016 |

## <a id="RC2"></a>RC2 (第 2017 年 8 月)

此版本的 SQL Server 引擎版本是 14.0.900.75。

### <a name="supported-platforms"></a>支援的平台

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [安裝指南](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE]
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎已在此階段中測試 1.5 TB 的記憶體。

### <a name="package-details"></a>封裝詳細資料

下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 請注意，您不需要直接下載這些封裝，如果您使用下列的安裝指南中的步驟：

- [安裝 SQL Server 封裝](sql-server-linux-setup.md)
- [安裝全文檢索搜尋的套件](sql-server-linux-setup-full-text-search.md)
- [安裝 SQL Server 代理程式套件](sql-server-linux-setup-sql-agent.md)

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| Red Hat RPM 套件 | 14.0.900.75-1 | [引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| SLES RPM 套件 | 14.0.900.75-1 | [mssql 伺服器引擎 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.900.75-1.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.900.75-1.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.900.75-1.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.900.75-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 封裝 | 14.0.900.75-1 | [引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.900.75-1_amd64.deb)</br>[高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.900.75-1_amd64.deb)</br>[全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.900.75-1_amd64.deb)</br>[SQL Server Agent Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.900.75-1_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools for Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 |

### <a name="unsupported-features-and-services"></a>不支援的功能和服務

下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 異動複寫 |
| &nbsp; | 合併式複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | 合作對象第 3 層連線與分散式的查詢 |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| &nbsp; | 緩衝集區擴充 |
| **SQL Server Agent** |  子系統： CmdExec、 PowerShell、 佇列讀取器、 SSIS、 SSAS、 SSRS |
| &nbsp; | 警示 |
| &nbsp; | 記錄讀取器代理程式 |
| &nbsp; | 異動資料擷取 |
| &nbsp; | 受管理備份 |
| **高可用性** | 資料庫鏡像  |
| **安全性** | 可延伸金鑰管理 |
| **服務** | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題

下列章節說明在 Linux 上的這一版的 SQL Server 2017 RC2 的已知的問題。

#### <a name="general"></a>一般

- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- 預設語言**sa**登入是英文。

    - **解析**： 變更語言**sa**登入，而且**ALTER LOGIN**陳述式。

#### <a name="databases"></a>資料庫

- Master 資料庫無法移動 mssql conf 公用程式。 可將其他系統資料庫移具備 mssql configuration manager

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

- 某些演算法 （加密套件） 的傳輸層安全性 (TLS) 無法正常運作的 SQL Server on Linux。 這會導致連接失敗時嘗試連線到 SQL Server，以及建立高可用性群組複本之間的連線問題。

   - **解析**： 修改**mssql.conf**組態指令碼的 SQL Server on Linux 停用有問題的加密套件，執行下列步驟：

      1. 將下列加入至 /var/opt/mssql/mssql.conf。

      ```
      [network]
      tlsciphers=ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

      1. 使用下列命令，重新啟動 SQL Server。
   
      ```
      sudo systemctl restart mssql-server
      ```

- 在 Linux 上的 SQL Server 2017，無法還原使用記憶體內部 OLTP 的 Windows 上的 SQL Server 2014 資料庫。 若要還原使用記憶體內部 OLTP 的 SQL Server 2014 資料庫，先將資料庫升級到 SQL Server 2016 或 Windows 上的 SQL Server 2017 之前將其移至 SQL Server on Linux 透過備份/還原或卸離/附加。

#### <a name="remote-database-files"></a>遠端資料庫檔案

- 在此版本中不支援裝載於 NFS 伺服器上的資料庫檔案。 這包括使用 NFS 共用的磁碟容錯移轉叢集資料庫以及非叢集執行個體上。 我們正在研究如何啟用即將發行版本中的 NFS 伺服器支援。

#### <a name="localization"></a>當地語系化

- 如果您的地區設定不是英文 (en_us) 在安裝期間，您必須使用 utf-8 編碼您 bash 工作階段/終端機中。 如果您使用 ASCII 編碼方式，您可能會看到類似下面的錯誤：

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   如果您無法使用 utf-8 編碼方式，執行安裝程式使用 MSSQL_LCID 環境變數來指定您選擇的語言。

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name="full-text-search"></a>全文檢索搜尋
- 並非所有的篩選是適用於此版本中，包括 Office 文件的篩選。 如需支援的篩選器的清單，請參閱[Linux 上安裝 SQL Server 全文檢索搜尋](sql-server-linux-setup-full-text-search.md#filters)。

#### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
您可以在 Linux 上執行 SSIS 封裝。 如需詳細資訊，請參閱下列文章：
-   [部落格文章宣佈適用於 SSIS 支援適用於 Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)。
-   [Linux 上安裝 SQL Server Integration Services (SSIS)](sql-server-linux-setup-ssis.md)
-   [擷取、 轉換和載入與 SSIS Linux 上的資料](sql-server-linux-migrate-ssis.md)

請注意在此版本的下列已知的問題。

- **Mssql 伺服器是**Ubuntu 和 Red Hat Enterprise Linux (RHEL) 在此版本中支援套件。

- 在重新整理 Linux CTP 2.1 和更新版本的 SSIS，SSIS 封裝可以使用 ODBC 連接 on Linux。 這項功能經過測試可與 SQL Server 及 MySQL ODBC 驅動程式，但也應該使用 ODBC 規格會觀察到的任何 Unicode ODBC 驅動程式。 在設計階段，您可以提供 DSN 或連接字串連接至 ODBC 資料;您也可以使用 Windows 驗證。 如需詳細資訊，請參閱[部落格文章發表的 ODBC 支援在 Linux 上](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)。

- 當您在 Linux 上執行 SSIS 封裝時，下列功能不支援此版本中：
  - SSIS 目錄資料庫
  - SQL Agent 排程的封裝執行
  - Windows 驗證
  - 第三方元件
  - 異動資料擷取 (CDC)
  - SSIS 向外延展
  - 適用於 SSIS 的 azure 功能套件
  - Hadoop 和 HDFS 的支援
  - Microsoft Connector for SAP BW

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 不支援管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 若要保留的記錄檔的數目不能修改。

### <a name="next-steps"></a>後續的步驟

若要開始，請參閱下列快速入門教學課程：

- [Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [執行 docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分隔列圖形](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="RC1"></a>RC1 (年 7 月 2017)
此版本的 SQL Server 引擎版本是 14.0.800.90。

### <a name="supported-platforms"></a>支援的平台 

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [安裝指南](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE]
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎已在此階段中測試 1 TB 的記憶體。

### <a name="package-details"></a>封裝詳細資料
下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 請注意，您不需要直接下載這些封裝，如果您使用下列的安裝指南中的步驟：

- [安裝 SQL Server 封裝](sql-server-linux-setup.md)
- [安裝全文檢索搜尋的套件](sql-server-linux-setup-full-text-search.md)
- [安裝 SQL Server 代理程式套件](sql-server-linux-setup-sql-agent.md)

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| Red Hat RPM 套件 | 14.0.800.90-2 | [引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| SLES RPM 套件 | 14.0.800.90-2 | [mssql 伺服器引擎 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.800.90-2.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.800.90-2.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.800.90-2.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.800.90-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 封裝 | 14.0.800.90-2 | [引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.800.90-2_amd64.deb)</br>[高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.800.90-2_amd64.deb)</br>[全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.800.90-2_amd64.deb)</br>[SQL Server Agent Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.800.90-2_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools for Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 |

### <a name="unsupported-features-and-services"></a>不支援的功能和服務
下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 異動複寫 |
| &nbsp; | 合併式複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | 機器學習服務 |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| **SQL Server Agent** |  子系統： CmdExec、 PowerShell、 佇列讀取器、 SSIS、 SSAS、 SSRS |
| &nbsp; | 警示 |
| &nbsp; | 記錄讀取器代理程式 |
| &nbsp; | 異動資料擷取 |
| &nbsp; | 受管理備份 |
| **高可用性** | 資料庫鏡像  |
| &nbsp; | 可用性群組的輪流升級 |
| **安全性** | 可延伸金鑰管理 |
| **服務** | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題
下列章節說明在 Linux 上的這一版的 SQL Server 2017 RC1 的已知的問題。

#### <a name="general"></a>一般
- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- 預設語言**sa**登入是英文。

    - **解析**： 變更語言**sa**登入，而且**ALTER LOGIN**陳述式。

#### <a name="databases"></a>資料庫

- 無法移動系統資料庫使用 mssql conf 公用程式。

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

#### <a name="remote-database-files"></a>遠端資料庫檔案

- 在此版本中不支援裝載於 NFS 伺服器上的資料庫檔案。 這包括使用 NFS 共用的磁碟容錯移轉叢集資料庫以及非叢集執行個體上。 我們正在研究如何啟用即將發行版本中的 NFS 伺服器支援。

#### <a name="cross-platform-availability-groups-and-distributed-availability-groups"></a>跨平台可用性群組和分散式的可用性群組

- 由於已知的問題，以裝載在 Windows 和 Linux 上的執行個體上的複本建立可用性群組並未在此版本中。 這包括分散式的可用性群組。 修正將可在即將發行候選版本組建。 

#### <a name="server-collation"></a>伺服器定序

- 當使用 MSSQL_COLLATION 覆寫，或當地語系化 （非英文） 安裝時，可能是 SQL Server 會叫用死結，嘗試設定伺服器定序，會產生傾印時。 安裝程式不會成功完成，不過，伺服器定序會有尚未設定。 因應措施是直接執行。 / mssql conf 組定序，並輸入出現提示時，所需的定序名稱 (列在錯誤記錄檔中找定序名稱: 「 嘗試變更預設定序...」)。 
 
#### <a name="localization"></a>當地語系化

- 如果您的地區設定不是英文 (en_us) 在安裝期間，您必須使用 utf-8 編碼您 bash 工作階段/終端機中。 如果您使用 ASCII 編碼方式，您可能會看到類似下面的錯誤：

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   如果您無法使用 utf-8 編碼方式，執行安裝程式使用 MSSQL_LCID 環境變數來指定您選擇的語言。

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

#### <a name = "fci"></a>共用磁碟叢集執行個體升級

RC1 中叢集資源代理程式會設定虛擬伺服器名稱，在 Windows 上的容錯移轉叢集執行個體中所顯示的一樣。 在 RC1 之前`@@servername`共用磁碟叢集傳回特定的節點名稱，在容錯移轉之後`@@servername`傳回不同的值。 在 RC1 共用的磁碟叢集執行個體的伺服器名稱已更新的資源名稱的資源新增至叢集時。 因為這個緣故，叢集將具有後到重新啟動 SQL Server 的手動容錯移轉期間升級-如下列步驟所示：

1. 先升級次要 （被動） 的叢集節點。
   - 升級**mssql 伺服器**封裝。
   - 升級**mssql-伺服器-ha**封裝。
1. 手動容錯移轉至升級的節點。
   `pcs resource move <resourceName>`
   - 資源一開始失敗，因為資源代理程式會檢查實際和預期的伺服器名稱。 預期的伺服器名稱將會不同。
   - 叢集會重新啟動 SQL Server 資源的相同節點上。 這會更新伺服器名稱。
1. 升級其他節點。 
   - 升級**mssql 伺服器**封裝。
   - 升級**mssql-伺服器-ha**封裝。
1. 移除條件約束加入手動資源移動。 請參閱[容錯移轉叢集的手動](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md#failManual)。
2. 如有需要，則會容錯回復到原始的主要節點。 

#### <a name="availability-group"></a>可用性群組

在 Linux 上不支援的輪流升級 SQL Server 2017 CTP 2.1 至 RC1。 升級次要複本之後，會中斷連線的主要複本之前升級主要複本。 Microsoft 計劃，以解決此問題在未來的版本。

#### <a name="full-text-search"></a>全文檢索搜尋
- 並非所有的篩選是適用於此版本中，包括 Office 文件的篩選。 如需支援的篩選器的清單，請參閱[Linux 上安裝 SQL Server 全文檢索搜尋](sql-server-linux-setup-full-text-search.md#filters)。

#### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- **Mssql 伺服器是**封裝 SUSE 上不支援此版本中。 目前支援在 Ubuntu 上及在 Red Hat Enterprise Linux (RHEL)。

- 當您在 Linux 上執行 SSIS 封裝時，下列功能不支援此版本中：
  - SSIS 目錄資料庫
  - SQL Agent 排程的封裝執行
  - Windows 驗證
  - 第三方元件
  - 異動資料擷取 (CDC)
  - SSIS 向外延展
  - 適用於 SSIS 的 azure 功能套件
  - Hadoop 和 HDFS 的支援
  - Microsoft Connector for SAP BW

如需在 Linux 上的 SSIS 的詳細資訊，請參閱下列文章：
-   [Linux 上安裝 SQL Server Integration Services (SSIS)](sql-server-linux-setup-ssis.md)
-   [擷取、 轉換和載入與 SSIS Linux 上的資料](sql-server-linux-migrate-ssis.md)

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 不支援管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 若要保留的記錄檔的數目不能修改。

### <a name="next-steps"></a>後續的步驟

若要開始，請參閱下列快速入門教學課程：

- [Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [執行 docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分隔列圖形](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp21"></a>CTP 2.1 (可能 2017)
此版本的 SQL Server 引擎版本是 14.0.600.250。

### <a name="supported-platforms"></a>支援的平台 

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [安裝指南](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE]
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎已在此階段中測試 1 TB 的記憶體。

### <a name="package-details"></a>封裝詳細資料
下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 您不需要直接下載這些封裝，如果您使用下列的安裝指南中的步驟：

- [安裝 SQL Server 封裝](sql-server-linux-setup.md)
- [安裝全文檢索搜尋的套件](sql-server-linux-setup-full-text-search.md)
- [安裝 SQL Server 代理程式套件](sql-server-linux-setup-sql-agent.md)

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| Red Hat RPM 套件 | 14.0.600.250-2 | [引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| SLES RPM 套件 | 14.0.600.250-2 | [mssql 伺服器引擎 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.600.250-2.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.600.250-2.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.600.250-2.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.600.250-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 封裝 | 14.0.600.250-2 | [引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.600.250-2_amd64.deb)</br>[高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.600.250-2_amd64.deb)</br>[全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.600.250-2_amd64.deb)</br>[SQL Server Agent Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.600.250-2_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) for Windows](https://go.microsoft.com/fwlink/?linkid=847722) | 17.0 |
| [SQL Server Data Tools for Visual Studio](https://go.microsoft.com/fwlink/?linkid=846626) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 (1.12) |

### <a name="unsupported-features-and-services"></a>不支援的功能和服務
下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| **高可用性** | 資料庫鏡像  |
| **安全性** | Active Directory 驗證 |
| &nbsp; | Windows 驗證 |
| &nbsp; | 可延伸金鑰管理 |
| &nbsp; | 使用使用者提供的憑證進行 SSL 或 TLS |
| **服務** | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題
下列章節說明在 Linux 上的這一版的 SQL Server 2017 CTP 2.1 的已知的問題。

#### <a name="general"></a>一般
- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- 預設語言**sa**登入是英文。

    - **解析**： 變更語言**sa**登入，而且**ALTER LOGIN**陳述式。

#### <a name="databases"></a>資料庫
- 無法移動系統資料庫使用 mssql conf 公用程式。

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

#### <a name="always-on-availability-group"></a>Always On 可用性群組
- `sys.fn_hadr_backup_is_preffered_replica`不適用於`CLUSTER_TYPE=NONE`或`CLUSTER_TYPE=EXTERNAL`因為其依賴 WSFC 複寫叢集登錄機碼無法使用它。 我們會努力提供類似的功能，透過不同的函式。 

#### <a name="full-text-search"></a>全文檢索搜尋
- 並非所有的篩選是適用於此版本中，包括 Office 文件的篩選。 如需支援的篩選器的清單，請參閱[Linux 上安裝 SQL Server 全文檢索搜尋](sql-server-linux-setup-full-text-search.md#filters)。

#### <a name="sql-agent"></a>SQL 代理程式
- 下列元件和子系統的 SQL 代理程式作業目前不支援在 Linux 上：

    - 子系統： CmdExec、 PowerShell、 複寫散發者、 快照集、 合併、 佇列讀取器、 SSIS、 SSAS、 SSRS
    - 警示
    - DB 郵件
    - 記錄讀取器代理程式 
    - 異動資料擷取

#### <a name="sqlpackage"></a>SqlPackage
- 透過 SqlPackage 必須指定檔案的絕對路徑。 使用相對路徑會對應 」 / tmp/sqlpackage 下檔案。\<程式碼 \> /系統/system32"資料夾。 

  - **解析**： 使用絕對檔案路徑。

- SqlPackage 顯示檔案的位置"c:\\"前置詞。

#### <a name="ssis"></a> SQL Server Integration Services (SSIS)
您可以在 Linux 上執行 SSIS 封裝。 如需詳細資訊，請參閱[部落格文章宣佈適用於 SSIS 支援適用於 Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)。 請注意在此版本的下列已知的問題。

- **Mssql 伺服器是**封裝在 Ubuntu 上才支援這一次。

- Linux 上執行 SSIS 封裝時，不支援下列功能：
  - SSIS 目錄資料庫
  - SQL 代理程式排程封裝執行
  - Windows 驗證
  - 第三方元件
  - 第三方 ODBC 驅動程式
  - ODBC 連接管理員、 來源和目的地 （使用重新整理 Linux CTP 2.1 上的 SSIS 支援）
  - 異動資料擷取 (CDC)
  - 相應放大
  - Azure 功能套件
  - Hadoop 和 HDFS 支援
  - Microsoft Connector for SAP BW

與 Linux CTP 2.1 重新整理 SSIS，SSIS 封裝可以在 Linux 上使用 ODBC 連接。 如需詳細資訊，請參閱[部落格文章發表的 ODBC 支援在 Linux 上](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)。

#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 不支援管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 若要保留的記錄檔的數目不能修改。

### <a name="next-steps"></a>後續的步驟

若要開始，請參閱下列快速入門教學課程：

- [Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [執行 docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分隔列圖形](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp20"></a>CTP 2.0 (第 2017 年 4 月)
此版本的 SQL Server 引擎版本是 14.0.500.272。

### <a name="supported-platforms"></a>支援的平台 

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [安裝指南](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS 和 16.10 | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎已在此階段中測試 1 TB 的記憶體。

### <a name="package-details"></a>封裝詳細資料
下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 請注意，您不需要直接下載這些封裝，如果您使用下列的安裝指南中的步驟：

- [安裝 SQL Server 封裝](sql-server-linux-setup.md)
- [安裝全文檢索搜尋的套件](sql-server-linux-setup-full-text-search.md)
- [安裝 SQL Server 代理程式套件](sql-server-linux-setup-sql-agent.md)

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| Red Hat RPM 套件 | 14.0.500.272-2 | [引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| SLES RPM 套件 | 14.0.500.272-2 | [mssql 伺服器引擎 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.500.272-2.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.500.272-2.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.500.272-2.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.500.272-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 封裝 | 14.0.500.272-2 | [引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[SQL Server Agent Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |
| Ubuntu 16.10 Debian 封裝 | 14.0.500.272-2 | [引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.500.272-2_amd64.deb)</br>[高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.500.272-2_amd64.deb)</br>[全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.500.272-2_amd64.deb)</br>[SQL Server Agent Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.500.272-2_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) 適用於 Windows 的候選版 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools for Visual Studio-候選版 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 (0.2.1) |

> [!NOTE] 
> 指定的 SQL Server Management Studio 和 SQL Server Data Tools 版本上方會發行候選項目，因此不建議在生產環境中使用。

### <a name="unsupported-features-and-services"></a>不支援的功能和服務
下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| **高可用性** | 資料庫鏡像  |
| **安全性** | Active Directory 驗證 |
| &nbsp; | Windows 驗證 |
| &nbsp; | 可延伸金鑰管理 |
| &nbsp; | 使用使用者提供的憑證進行 SSL 或 TLS |
| **服務** | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題
下列各節說明在 Linux 上的這一版的 SQL Server 2017 CTP 2.0 已知的問題。

#### <a name="general"></a>一般
- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- 預設語言**sa**登入是英文。

    - **解析**： 變更語言**sa**登入，而且**ALTER LOGIN**陳述式。

#### <a name="databases"></a>資料庫
- 無法移動系統資料庫使用 mssql conf 公用程式。

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

#### <a name="always-on-availability-group"></a>Always On 可用性群組
- 所有的 HA 組態-這表示做為資源建立前 CTP2.0 封裝 Pacemaker 叢集-新增可用性群組不相容於新的封裝。 刪除所有先前設定的叢集的資源，並建立新的可用性群組與`CLUSTER_TYPE=EXTERNAL`。 請參閱[設定 Alwayson 可用性群組的 SQL Server on Linux](sql-server-linux-availability-group-configure-ha.md)。
- 可用性群組，以建立`CLUSTER_TYPE=NONE`，不會加入叢集中的資源將會在升級之後繼續工作。 使用向外延展讀取案例。 請參閱[設定向外延展讀取可用性群組的 SQL Server on Linux](sql-server-linux-availability-group-configure-rs.md)。
- `sys.fn_hadr_backup_is_preffered_replica`不適用於`CLUSTER_TYPE=NONE`或`CLUSTER_TYPE=EXTERNAL`因為其依賴 WSFC 複寫叢集登錄機碼無法使用它。 我們會努力提供類似的功能，透過不同的函式。 

#### <a name="full-text-search"></a>全文檢索搜尋
- 並非所有的篩選是適用於此版本中，包括 Office 文件的篩選。 如需支援的篩選器的清單，請參閱[Linux 上安裝 SQL Server 全文檢索搜尋](sql-server-linux-setup-full-text-search.md#filters)。

- 韓文的斷詞工具會採用幾秒鐘的時間載入，並產生錯誤第一次使用。 之後此初始錯誤，它應該會運作正常。

#### <a name="sql-agent"></a>SQL 代理程式
- 下列元件和子系統的 SQL 代理程式作業目前不支援在 Linux 上：

    - 子系統： CmdExec、 PowerShell、 複寫散發者、 快照集、 合併、 佇列讀取器、 SSIS、 SSAS、 SSRS
    - 警示
    - DB 郵件
    - 記錄讀取器代理程式 
    - 異動資料擷取

#### <a name="sqlpackage"></a>SqlPackage
- 透過 SqlPackage 必須指定檔案的絕對路徑。 使用相對路徑會對應 」 / tmp/sqlpackage 下檔案。\<程式碼 \> /系統/system32"資料夾。 

    - **解析**： 使用絕對檔案路徑。

- SqlPackage 顯示檔案的位置"c:\\"前置詞。

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 不支援管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 若要保留的記錄檔的數目不能修改。

### <a name="next-steps"></a>後續的步驟

若要開始，請參閱下列快速入門教學課程：

- [Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [執行 docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分隔列圖形](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp14"></a>CTP 1.4 (第 2017 年 3 月)
此版本的 SQL Server 引擎版本是 14.0.405.198。

### <a name="supported-platforms"></a>支援的平台 

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [安裝指南](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS 和 16.10 | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎已在此階段中測試 1 TB 的記憶體。

### <a name="package-details"></a>封裝詳細資料
下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 請注意，您不需要直接下載這些封裝，如果您使用下方的安裝指南中的步驟
-   [安裝 SQL Server 封裝](sql-server-linux-setup.md)
-   [安裝全文檢索搜尋的套件](sql-server-linux-setup-full-text-search.md)
-   [安裝 SQL Server 代理程式套件](sql-server-linux-setup-sql-agent.md)

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| Red Hat RPM 套件 | 14.0.405.200-1 | [引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| SLES RPM 套件 | 14.0.405.200-1 | [mssql 伺服器引擎 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.405.200-1.x86_64.rpm)</br>[高可用性 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.405.200-1.x86_64.rpm)</br>[全文檢索搜尋 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.405.200-1.x86_64.rpm)</br>[SQL Server 代理程式 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-agent-14.0.405.200-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 封裝 | 14.0.405.200-1 | [引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[SQL Server Agent Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |
| Ubuntu 16.10 Debian 封裝 | 14.0.405.200-1 | [引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.405.200-1_amd64.deb)</br>[高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.405.200-1_amd64.deb)</br>[全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.405.200-1_amd64.deb)</br>[SQL Server Agent Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.405.200-1_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) 適用於 Windows 的候選版 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools for Visual Studio-候選版 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 (0.2.1) |

> [!NOTE] 
> 指定的 SQL Server Management Studio 和 SQL Server Data Tools 版本上方會發行候選項目，因此不建議在生產環境中使用。

### <a name="unsupported-features-and-services"></a>不支援的功能和服務
下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| **高可用性** | 資料庫鏡像  |
| **安全性** | Active Directory 驗證 |
| &nbsp; | Windows 驗證 |
| &nbsp; | 可延伸金鑰管理 |
| &nbsp; | 使用使用者提供的憑證進行 SSL 或 TLS |
| **服務** | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題
下列章節說明在 Linux 上的這一版的 SQL Server 2017 CTP 1.4 的已知的問題。

#### <a name="general"></a>一般
- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 無法執行命令`ALTER SERVICE MASTER KEY REGENERATE`。 沒有已知的錯誤會造成 SQL Server 變得不穩定。 如果您需要重新產生服務主要金鑰，您應該備份資料庫檔案，解除安裝和重新安裝 SQL Server，然後還原資料庫檔案一次。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 在 Linux 中的有些時區名稱不對應於 Windows 時區名稱。

    - **解析**： 使用從 TZID 資料行中的時區名稱 ' 的對應： Windows' 區段資料表上的[Unicode.org 文件頁面](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)。

- SQL Server 引擎預期終止 CR lf （Windows 樣式線條格式） 的文字檔案中的行。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- 所有記錄檔，以及錯誤記錄檔中會以 utf-16 編碼。

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- **CREATE ASSEMBLY**時嘗試使用的檔案將無法運作。 使用**FROM\<位元\>**方法而現在。 

#### <a name="databases"></a>資料庫
- 無法移動系統資料庫使用 mssql conf 公用程式。

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

#### <a name="always-on-availability-group"></a>Always On 可用性群組
- Alwayson 可用性群組之後升級 HA 封裝 (mssql-伺服器-ha)，在 Linux 上使用 CTP 1.3 所建立的叢集的資源將會失敗。 

   - **解析**： 升級 HA 封裝之前，請設定叢集資源參數`notify=true`。 
   
      - 下列範例會設定名為的資源上的叢集資源參數**ag1** RHEL 或 Ubuntu 上： 

      ```bash
      sudo pcs resource update ag1-master notify=true
      ```

      - Sles，更新可用性群組資源設定，以新增`notify=true`。  

      ```bash
      crm configure edit ms-ag_cluster 
      ```

      新增`notify=true`並儲存資源設定。

- 如果複本皆處於同步認可模式，alwayson 可用性群組在 Linux 中可能會受限於資料遺失。 視您的 Linux 散發套件，請參閱詳細資料。 

   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

#### <a name="full-text-search"></a>全文檢索搜尋
- 並非所有的篩選是適用於此版本中，包括 Office 文件的篩選。 如需支援的篩選器的清單，請參閱[Linux 上安裝 SQL Server 全文檢索搜尋](sql-server-linux-setup-full-text-search.md#filters)。

- 韓文的斷詞工具會採用幾秒鐘的時間載入，並產生錯誤第一次使用。 之後此初始錯誤，它應該會運作正常。

#### <a name="sql-agent"></a>SQL 代理程式
- 下列元件和子系統的 SQL 代理程式作業目前不支援在 Linux 上：
    - 子系統： CmdExec、 PowerShell、 複寫散發者、 快照集、 合併、 佇列讀取器、 SSIS、 SSAS、 SSRS
    - 警示
    - DB 郵件
    - 記錄傳送
    - 記錄讀取器代理程式 
    - 異動資料擷取

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- 記憶體內部 OLTP 資料庫只能建立 /var/opt/mssql 目錄中。 如需詳細資訊，請瀏覽[記憶體中 OLTP 主題](sql-server-linux-performance-get-started.md#use-in-memory-oltp)。

#### <a name="sqlpackage"></a>SqlPackage
- 透過 SqlPackage 必須指定檔案的絕對路徑。 使用相對路徑會對應 」 / tmp/sqlpackage 下檔案。\<程式碼 \> /系統/system32"資料夾。 

    - **解析**： 使用絕對檔案路徑。

- SqlPackage 顯示檔案的位置"c:\\"前置詞。

    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中的不支援。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 檔案瀏覽器受限於"c:\\"範圍內，可解析成/var/選擇/mssql/Linux 上。 若要使用其他路徑，產生 UI 作業的指令碼，取代 c:\\ Linux 路徑的路徑。 然後以手動方式在 SSMS 中執行指令碼。

- 若要保留的記錄檔的數目不能修改。

### <a name="next-steps"></a>後續的步驟

若要開始，請參閱下列快速入門教學課程：

- [Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [執行 docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分隔列圖形](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a id="ctp13"></a>CTP 1.3 (第 2017 年 2 月)
此版本的 SQL Server 引擎版本是 14.0.304.138。

### <a name="supported-platforms"></a>支援的平台 

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [安裝指南](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS 和 16.10 | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎已在此階段中測試 1 TB 的記憶體。

### <a name="package-details"></a>封裝詳細資料
下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 如果您使用中的步驟，請注意，您不需要下載這些封裝直接[安裝指南](sql-server-linux-setup.md)。

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| Red Hat RPM 套件 | 14.0.304.138-1 | [mssql 伺服器引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[mssql-伺服器-ha 高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[mssql-伺服器-fts 全文檢索搜尋 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| SLES RPM 套件 | 14.0.304.138-1 | [mssql 伺服器引擎 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-14.0.304.138-1.x86_64.rpm)</br>[mssql-伺服器-ha 高可用性 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-ha-14.0.304.138-1.x86_64.rpm)</br>[mssql-伺服器-fts 全文檢索搜尋 RPM 套件](https://packages.microsoft.com/sles/12/mssql-server/mssql-server-fts-14.0.304.138-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 封裝 | 14.0.304.138-1 | [mssql 伺服器引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[mssql-伺服器-ha 高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[mssql-伺服器-fts 全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |
| Ubuntu 16.10 Debian 封裝 | 14.0.304.138-1 | [mssql 伺服器引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.304.138-1_amd64.deb)</br>[mssql-伺服器-ha 高可用性 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.304.138-1_amd64.deb)</br>[mssql-伺服器-fts 全文檢索搜尋 Debian 封裝](https://packages.microsoft.com/ubuntu/16.10/mssql-server/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.304.138-1_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) 適用於 Windows 的候選版 2](https://go.microsoft.com/fwlink/?linkid=840957) | 17.0 |
| [SQL Server Data Tools for Visual Studio-候選版 2](https://go.microsoft.com/fwlink/?linkid=837939) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 (0.2.1) |

> [!NOTE] 
> 指定的 SQL Server Management Studio 和 SQL Server Data Tools 版本上方會發行候選項目，因此不建議在生產環境中使用。

### <a name="unsupported-features-and-services"></a>不支援的功能和服務
下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| **高可用性** | 資料庫鏡像  |
| **安全性** | Active Directory 驗證 |
| &nbsp; | Windows 驗證 |
| &nbsp; | 可延伸金鑰管理 |
| &nbsp; | 使用使用者提供的憑證進行 SSL 或 TLS |
| **服務** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題
下列章節說明在 Linux 上的這一版的 SQL Server 2017 CTP 1.3 的已知的問題。

#### <a name="general"></a>一般
- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 無法執行命令`ALTER SERVICE MASTER KEY REGENERATE`。 沒有已知的錯誤會造成 SQL Server 變得不穩定。 如果您需要重新產生服務主要金鑰，您應該備份資料庫檔案，解除安裝和重新安裝 SQL Server，然後還原資料庫檔案一次。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 在 Linux 中的有些時區名稱不對應於 Windows 時區名稱。

    - **解析**： 使用從 TZID 資料行中的時區名稱 ' 的對應： Windows' 區段資料表上的[Unicode.org 文件頁面](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)。

- SQL Server 引擎預期終止 CR lf （Windows 樣式線條格式） 的文字檔案中的行。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- 所有記錄檔，以及錯誤記錄檔中會以 utf-16 編碼。

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- **CREATE ASSEMBLY**時嘗試使用的檔案將無法運作。 使用**FROM\<位元\>**方法而現在。 

#### <a name="databases"></a>資料庫
- 不支援變更 TempDB 資料和記錄檔的位置。

- 無法移動系統資料庫使用 mssql conf 公用程式。

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

- 如果複本皆處於同步認可模式，alwayson 可用性群組在 Linux 中可能會受限於資料遺失。 請參閱 
 
   - [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   - [SLES](sql-server-linux-availability-group-cluster-sles.md)
   - [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   
#### <a name="full-text-search"></a>全文檢索搜尋
- 並非所有的篩選是適用於此版本中，包括 Office 文件的篩選。 如需支援的篩選器的清單，請參閱[Linux 上安裝 SQL Server 全文檢索搜尋](sql-server-linux-setup-full-text-search.md#filters)。

- 韓文的斷詞工具會採用幾秒鐘的時間載入，並產生錯誤第一次使用。 之後此初始錯誤，它應該會運作正常。

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- 記憶體內部 OLTP 資料庫只能建立 /var/opt/mssql 目錄中。 如需詳細資訊，請瀏覽[記憶體中 OLTP 主題](sql-server-linux-performance-get-started.md#use-in-memory-oltp)。  

#### <a name="sqlpackage"></a>SqlPackage
- 透過 SqlPackage 必須指定檔案的絕對路徑。 使用相對路徑會對應下的檔案 」 /tmp/sqlpackage./ <code/> /系統/system32"資料夾。 

    - **解析**： 使用絕對檔案路徑。

- SqlPackage 顯示檔案的位置"c:\\"前置詞。

#### <a name="sqlcmdbcp--odbc"></a>Sqlcmd/BCP 和 ODBC 
- SQL Server 命令列工具 （mssql 工具） 和 ODBC 驅動程式 (msodbcsql) 相依於自訂 unixODBC 驅動程式管理員。 這會導致衝突，如果您先前安裝的 unixODBC 驅動程式管理員。 

    - **解析**： 上 Ubuntu，將會自動解決衝突。 當系統提示您想要解除安裝現有的 unixODBC 驅動程式管理員，請輸入 'y'，然後繼續進行安裝。 在 RedHat，您必須手動移除現有的 unixODBC 驅動程式管理員使用`yum remove unixODBC`。 我們努力修正這項限制的 RHEL 和 SUSE，應該已更新為您很快。  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中的不支援。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 尚不支援 SQL Server 代理程式。 因此，在 SSMS 中的 SQL Server 代理程式功能不適用於 Linux 目前。

- 檔案瀏覽器受限於"c:\\"範圍內，可解析成/var/選擇/mssql/Linux 上。 若要使用其他路徑，產生 UI 作業的指令碼，取代 c:\\ Linux 路徑的路徑。 然後以手動方式在 SSMS 中執行指令碼。

- 若要保留的記錄檔的數目不能修改。

### <a name="next-steps"></a>後續的步驟

若要開始，請參閱下列快速入門教學課程：

- [Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [執行 docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分隔列圖形](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp12-ctp-12-january-2017"></a><a id="ctp12">CTP 1.2 (第 2017 年 1 月)
此版本的 SQL Server 引擎版本是 14.0.200.24。

### <a name="supported-platforms"></a>支援的平台 

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | EXT4 | [安裝指南](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS 和 16.10 | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎只被測試這一次最多為 256 GB 的記憶體。

### <a name="package-details"></a>封裝詳細資料
下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 如果您使用中的步驟，請注意，您不需要下載這些封裝直接[安裝指南](sql-server-linux-setup.md)。

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| RPM 套件 | 14.0.200.24-2 | [mssql 伺服器 14.0.200.24-2 引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.200.24-2.x86_64.rpm)</br>[mssql 伺服器 14.0.200.24-2 高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.200.24-2.x86_64.rpm) | 
| Debian 封裝 | 14.0.200.24-2 | [mssql server 14.0.200.24-2 引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.200.24-2_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) 適用於 Windows 的候選版 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools for Visual Studio-候選版 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 (0.2) |

> [!NOTE] 
> 指定的 SQL Server Management Studio 和 SQL Server Data Tools 版本上方會發行候選項目，因此不建議在生產環境中使用。

### <a name="unsupported-features-and-services"></a>不支援的功能和服務
下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 全文檢索搜尋 |
| &nbsp; | 複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| **高可用性** | AlwaysOn 可用性群組 |
| &nbsp; | 資料庫鏡像  |
| **安全性** | Active Directory 驗證 |
| &nbsp; | Windows 驗證 |
| &nbsp; | 可延伸金鑰管理 |
| &nbsp; | 使用使用者提供的憑證進行 SSL 或 TLS |
| **服務** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題
下列章節說明在 Linux 上的這一版的 SQL Server 2017 CTP 1.2 的已知的問題。

#### <a name="general"></a>一般
- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 無法執行命令`ALTER SERVICE MASTER KEY REGENERATE`。 沒有已知的錯誤會造成 SQL Server 變得不穩定。 如果您需要重新產生服務主要金鑰，您應該備份資料庫檔案，解除安裝和重新安裝 SQL Server，然後還原資料庫檔案一次。

- 從 ocf:sql:fci 變成 ocf:mssql:fci SQL 資源的資源名稱。 設定共用的磁碟容錯移轉叢集，您可以找到更多詳細[這裡](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure)。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 在 Linux 中的有些時區名稱不對應於 Windows 時區名稱。

    - **解析**： 使用從 TZID 資料行中的時區名稱 ' 的對應： Windows' 區段資料表上的[Unicode.org 文件頁面](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)。

- SQL Server 引擎預期終止 CR lf （Windows 樣式線條格式） 的文字檔案中的行。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- 所有記錄檔，以及錯誤記錄檔中會以 utf-16 編碼。

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- **CREATE ASSEMBLY**時嘗試使用的檔案將無法運作。 使用**FROM\<位元\>**方法而現在。 

#### <a name="databases"></a>資料庫
- 不支援變更 TempDB 資料和記錄檔的位置。

- 無法移動系統資料庫使用 mssql conf 公用程式。

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- 記憶體內部 OLTP 資料庫只能建立 /var/opt/mssql 目錄中。 這些資料庫也必須以"c:\\"標記法時參考。 如需詳細資訊，請瀏覽[記憶體中 OLTP 主題](sql-server-linux-performance-get-started.md#use-in-memory-oltp)。  

#### <a name="sqlpackage"></a>SqlPackage
- 透過 SqlPackage 必須指定檔案的絕對路徑。 使用相對路徑會對應 」 / tmp/sqlpackage 下檔案。\<程式碼 \> /系統/system32"資料夾。 

    - **解析**： 使用絕對檔案路徑。

- SqlPackage 顯示檔案的位置"c:\\"前置詞。

#### <a name="sqlcmdbcp--odbc"></a>Sqlcmd/BCP 和 ODBC 
- 如果您有較舊版本的 SQL Server 命令列工具 （mssql 工具） 和 ODBC 驅動程式 (msodbcsql)，您可能已安裝自訂的 unixODBC 驅動程式管理員 (unixODBC utf16)。 這可能會造成潛在的衝突，因為我們無法再使用自訂的驅動程式管理員。 

    - **解析**： 在 Ubuntu 和 SLES，將會自動解決衝突。 當系統提示您想要解除安裝現有的 unixODBC 驅動程式管理員，請輸入 'y'，然後繼續進行安裝。 在 RedHat，您必須手動移除現有的 unixODBC 驅動程式管理員使用`yum remove unixODBC-utf16 unixODBC-utf16-devel`，然後重試安裝。
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中的不支援。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 尚不支援 SQL Server 代理程式。 因此，在 SSMS 中的 SQL Server 代理程式功能不適用於 Linux 目前。

- 檔案瀏覽器受限於"c:\\"範圍內，可解析成/var/選擇/mssql/Linux 上。 若要使用其他路徑，產生 UI 作業的指令碼，取代 c:\\ Linux 路徑的路徑。 然後以手動方式在 SSMS 中執行指令碼。

### <a name="next-steps"></a>後續的步驟

若要開始，請參閱下列快速入門教學課程：

- [Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [執行 docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

![分隔列圖形](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp11-ctp-11-december-2016"></a><a id="ctp11">CTP 1.1 (年 12 月 2016)
此版本的 SQL Server 引擎版本是 14.0.100.187。

### <a name="supported-platforms"></a>支援的平台 

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS 和 16.10 | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎只被測試這一次最多為 256 GB 的記憶體。

### <a name="package-details"></a>封裝詳細資料
下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 如果您使用中的步驟，請注意，您不需要下載這些封裝直接[安裝指南](sql-server-linux-setup.md)。

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| RPM 套件 | 14.0.100.187-1 | [mssql 伺服器 14.0.100.187-1 引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.100.187-1.x86_64.rpm)</br>[mssql 伺服器 14.0.100.187-1 高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.100.187-1.x86_64.rpm) | 
| Debian 封裝 | 14.0.100.187-1 | [mssql server 14.0.100.187-1 引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.100.187-1_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) 適用於 Windows 的候選版 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools for Visual Studio-候選版 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 (0.2) |

> [!NOTE] 
> 指定的 SQL Server Management Studio 和 SQL Server Data Tools 版本上方會發行候選項目，因此不建議在生產環境中使用。

### <a name="unsupported-features-and-services"></a>不支援的功能和服務
下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 全文檢索搜尋 |
| &nbsp; | 複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| **高可用性** | AlwaysOn 可用性群組 |
| &nbsp; | 資料庫鏡像  |
| **安全性** | Active Directory 驗證 |
| &nbsp; | Windows 驗證 |
| &nbsp; | 可延伸金鑰管理 |
| &nbsp; | 使用使用者提供的憑證進行 SSL 或 TLS |
| **服務** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題
下列章節說明在 Linux 上的這一版的 SQL Server 2017 CTP 1.1 的已知的問題。

#### <a name="general"></a>一般
- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 無法執行命令`ALTER SERVICE MASTER KEY REGENERATE`。 沒有已知的錯誤會造成 SQL Server 變得不穩定。 如果您需要重新產生服務主要金鑰，您應該備份資料庫檔案，解除安裝和重新安裝 SQL Server，然後還原資料庫檔案一次。

- 從 ocf:sql:fci 變成 ocf:mssql:fci SQL 資源的資源名稱。 設定共用的磁碟容錯移轉叢集，您可以找到更多詳細[這裡](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-shared-disk-cluster-red-hat-7-configure)。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 在 Linux 中的有些時區名稱不對應於 Windows 時區名稱。

    - **解析**： 使用從 TZID 資料行中的時區名稱 ' 的對應： Windows' 區段資料表上的[Unicode.org 文件頁面](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)。

- SQL Server 引擎預期終止 CR lf （Windows 樣式線條格式） 的文字檔案中的行。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- 所有記錄檔，以及錯誤記錄檔中會以 utf-16 編碼。

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- **CREATE ASSEMBLY**時嘗試使用的檔案將無法運作。 使用**FROM\<位元\>**方法而現在。 

#### <a name="databases"></a>資料庫
- 不支援變更 TempDB 資料和記錄檔的位置。

- 無法移動系統資料庫使用 mssql conf 公用程式。

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- 記憶體內部 OLTP 資料庫只能建立 /var/opt/mssql 目錄中。 這些資料庫也必須以"c:\"所參考的標記法。 如需詳細資訊，請瀏覽[記憶體中 OLTP 主題](sql-server-linux-performance-get-started.md#use-in-memory-oltp)。  

#### <a name="sqlpackage"></a>SqlPackage
- 透過 SqlPackage 必須指定檔案的絕對路徑。 使用相對路徑會對應 」 / tmp/sqlpackage 下檔案。\<程式碼 \> /系統/system32"資料夾。 

    - **解析**： 使用絕對檔案路徑。

- SqlPackage 顯示檔案的位置"c:\\"前置詞。

#### <a name="sqlcmdbcp--odbc"></a>Sqlcmd/BCP 和 ODBC 
- SQL Server 命令列工具 （mssql 工具） 和 ODBC 驅動程式 (msodbcsql) 相依於自訂 unixODBC 驅動程式管理員。 這會導致衝突，如果您先前安裝的 unixODBC 驅動程式管理員。 

    - **解析**： 上 Ubuntu，將會自動解決衝突。 當系統提示您想要解除安裝現有的 unixODBC 驅動程式管理員，請輸入 'y'，然後繼續進行安裝。 在 RedHat，您必須手動移除現有的 unixODBC 驅動程式管理員使用`yum remove unixODBC`。 我們努力修正這項限制的 RHEL 和 SUSE，應該已更新為您很快。  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中的不支援。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 尚不支援 SQL Server 代理程式。 因此，在 SSMS 中的 SQL Server 代理程式功能不適用於 Linux 目前。

- 檔案瀏覽器受限於"c:\\"範圍內，可解析成/var/選擇/mssql/Linux 上。 若要使用其他路徑，產生 UI 作業的指令碼，取代 c:\\ Linux 路徑的路徑。 然後以手動方式在 SSMS 中執行指令碼。

v

![分隔列圖形](./media/sql-server-linux-release-notes/seperationbar3.png)

## <a name="a-idctp10-ctp-10-november-2016"></a><a id="ctp10">CTP 1.0 (11 月版 2016)
此版本的 SQL Server 引擎版本是 14.0.1.246。

### <a name="supported-platforms"></a>支援的平台 

| 平台 | 檔案系統 | 安裝指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.2 工作站、 伺服器和桌面 | XFS 或 EXT4 | [安裝指南](quickstart-install-connect-red-hat.md) | 
| Ubuntu 16.04LTS | EXT4 | [安裝指南](quickstart-install-connect-ubuntu.md) | 
| Docker 引擎 1.8 + Windows、 Mac 或 Linux 上 | 해당 사항 없음 | [安裝指南](quickstart-install-connect-docker.md) | 

> [!NOTE] 
> 您需要至少 3.25 GB 的記憶體來執行 SQL Server on Linux。
> SQL Server 引擎只被測試這一次最多為 256 GB 的記憶體。

### <a name="package-details"></a>封裝詳細資料
下表中會列出套件詳細資料及針對 RPM 和 Debian 封裝的下載位置。 如果您使用中的步驟，請注意，您不需要下載這些封裝直接[安裝指南](sql-server-linux-setup.md)。

| 封裝 | 封裝版本 | 下載 |
|-----|-----|-----|
| RPM 套件 | 14.0.1.246-6 | [mssql 伺服器 14.0.1.246-6 引擎 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-14.0.1.246-6.x86_64.rpm)</br>[mssql 伺服器 14.0.1.246-6 高可用性 RPM 套件](https://packages.microsoft.com/rhel/7/mssql-server/mssql-server-ha-14.0.1.246-6.x86_64.rpm) | 
| Debian 封裝 | 14.0.1.246-6 | [mssql server 14.0.1.246-6 引擎 Debian 封裝](https://packages.microsoft.com/ubuntu/16.04/mssql-server/pool/main/m/mssql-server/mssql-server_14.0.1.246-6_amd64.deb) |

### <a name="supported-client-tools"></a>支援的用戶端工具

| 工具 | 最小版本 |
|-----|-----|
| [SQL Server Management Studio (SSMS) 適用於 Windows 的候選版 1](https://go.microsoft.com/fwlink/?LinkID=835608) | 17.0 |
| [SQL Server Data Tools for Visual Studio-候選版 1](https://go.microsoft.com/fwlink/?LinkID=835150) | 17.0 |
| [Visual Studio Code](https://code.visualstudio.com)與[mssql 延伸模組](https://aka.ms/mssql-marketplace) | 最新 (0.1.5) |

> [!NOTE] 
> 指定的 SQL Server Management Studio 和 SQL Server Data Tools 版本上方會發行候選項目，因此不建議在生產環境中使用。

### <a name="unsupported-features-and-services"></a>不支援的功能和服務
下列功能和服務並不適用於 Linux 這一次。 這些功能的支援會逐漸啟用期間每月更新的頻率，預覽計畫。

| 區域 | 不支援的功能或服務 |
|-----|-----|
| **資料庫引擎** | 全文檢索搜尋 |
| &nbsp; | 複寫 |
| &nbsp; | Stretch DB |
| &nbsp; | Polybase |
| &nbsp; | Distributed Query |
| &nbsp; | 系統擴充預存程序 （XP_CMDSHELL 等等） |
| &nbsp; | Filetable |
| &nbsp; | CLR 組件與 EXTERNAL_ACCESS 或 UNSAFE 權限設定 |
| **高可用性** | AlwaysOn 可用性群組 |
| &nbsp; | 資料庫鏡像  |
| **安全性** | Active Directory 驗證 |
| &nbsp; | Windows 驗證 |
| &nbsp; | 可延伸金鑰管理 |
| &nbsp; | 使用使用者提供的憑證進行 SSL 或 TLS |
| **服務** | SQL Server Agent |
| &nbsp; | SQL Server Browser |
| &nbsp; | SQL Server R 服務 |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Integration Services | 
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |

### <a name="known-issues"></a>已知問題
下列章節說明在 Linux 上的這一版的 SQL Server 2017 CTP1 的已知的問題。

#### <a name="general"></a>一般
- SQL Server 安裝，需要 15 個字元或更少所在的主機名稱的長度。 

    - **解析**: /etc/hosts 主機名稱中的將名稱變更為項目 15 個字元長或較少。

- 回溯時間手動將系統時間會導致 SQL Server 停止更新 SQL Server 中的內部系統時間。

    - **解析**： 重新啟動 SQL Server。

- 在 Linux 中的有些時區名稱不對應於 Windows 時區名稱。

    - **解析**： 使用從 TZID 資料行中的時區名稱 ' 的對應： Windows' 區段資料表上的[Unicode.org 文件頁面](http://www.unicode.org/cldr/charts/latest/supplemental/zone_tzid.html)。

- SQL Server 引擎預期終止 CR lf （Windows 樣式線條格式） 的文字檔案中的行。

- 支援只有單一執行個體安裝。

    - **解析**： 如果您想要在指定的主機上有多個執行個體，請考慮使用 Vm 或 Docker 容器。 

- 所有記錄檔，以及錯誤記錄檔中會以 utf-16 編碼。

- SQL Server 組態管理員無法連線到 SQL Server on Linux。

- **CREATE ASSEMBLY**時嘗試使用的檔案將無法運作。 使用**FROM\<位元\>**方法而現在。

#### <a name="databases"></a>資料庫
- 不支援變更 TempDB 資料和記錄檔的位置。

- 無法移動系統資料庫使用 mssql conf 公用程式。

- 還原 Windows 上的 SQL Server 備份資料庫時，您必須使用**WITH MOVE**子句在 TRANSACT-SQL 陳述式中的。

- 在 Linux 上執行的 SQL Server 上不支援需要 Microsoft 分散式交易協調器服務的分散式交易。 SQL Server 到 SQL Server 支援分散式的交易。

#### <a name="in-memory-oltp"></a>In-Memory OLTP
- 記憶體內部 OLTP 資料庫只能建立 /var/opt/mssql 目錄中。 這些資料庫也必須以"c:\\"標記法時參考。 如需詳細資訊，請瀏覽[記憶體中 OLTP 主題](sql-server-linux-performance-get-started.md#use-in-memory-oltp)。  

#### <a name="sqlpackage"></a>SqlPackage
- 透過 SqlPackage 需要指定檔案的絕對路徑。 使用相對路徑會對應 」 / tmp/sqlpackage 下檔案。\<程式碼 \> /系統/system32"資料夾。 

    - **解析**： 使用絕對檔案路徑。

- SqlPackage 顯示檔案的位置"c:\\"前置詞。

#### <a name="sqlcmdbcp--odbc"></a>Sqlcmd/BCP 和 ODBC 
- SQL Server 命令列工具 （mssql 工具） 和 ODBC 驅動程式 (msodbcsql) 相依於自訂 unixODBC 驅動程式管理員。 這會導致衝突，如果您先前安裝的 unixODBC 驅動程式管理員。 

    - **解析**： 上 Ubuntu，將會自動解決衝突。 當系統提示您想要解除安裝現有的 unixODBC 驅動程式管理員，請輸入 'y'，然後繼續進行安裝。 在 RedHat，您必須手動移除現有的 unixODBC 驅動程式管理員使用`yum remove unixODBC`。 我們努力修正這項限制的 RHEL 和 SUSE，應該已更新為您很快。  
    
#### <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)
下列限制適用於 SSMS 連接到 SQL Server on Linux 的 Windows 上。

- 維護計畫不支援。

- 管理資料倉儲 (MDW) 和資料收集器，在 SSMS 中的不支援。 

- SSMS UI 元件的 Windows 驗證或 Windows 事件記錄檔選項與 Linux 無法運作。 您仍然可以使用這些功能與其他選項，例如 SQL 登入。 

- 尚不支援 SQL Server 代理程式。 因此，在 SSMS 中的 SQL Server 代理程式功能不適用於 Linux 目前。

- 檔案瀏覽器受限於"c:\\"範圍內，可解析成/var/選擇/mssql/Linux 上。 若要使用其他路徑，產生 UI 作業的指令碼，取代 c:\\ Linux 路徑的路徑。 然後以手動方式在 SSMS 中執行指令碼。

### <a name="next-steps"></a>後續的步驟

若要開始，請參閱下列快速入門教學課程：

- [Red Hat Enterprise Linux 上安裝](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server 上安裝](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安裝](quickstart-install-connect-ubuntu.md)
- [執行 docker](quickstart-install-connect-ubuntu.md)
<br/>
<br/>

