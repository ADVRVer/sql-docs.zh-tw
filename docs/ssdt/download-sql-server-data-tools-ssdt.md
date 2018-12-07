---
title: 下載 SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 09/28/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssdt
ms.topic: conceptual
keywords:
- 安裝 SSDT, 下載 SSDT, 最新的 SSDT
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 3067b05783d7a83118e87dc8db4cdc6a83d40a1c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52515997"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>下載並安裝 SQL Server Data Tools (SSDT) for Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

> [!div class="nextstepaction"]
> [請協助我們改善 SQL Server 文件！](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

**SQL Server Data Tools** 是一款新式開發工具，可用來建置 SQL Server 關聯式資料庫、Azure SQL 資料庫、Analysis Services (AS) 資料模型、Integration Services (IS) 套件和 Reporting Services (RS) 報表。 有了 SSDT，您便可設計和部署任何 SQL Server 內容類型，就像在 Visual Studio 中開發應用程式一樣容易。

*對於大多數使用者而言，SQL Server Data Tools (SSDT) 會在 Visual Studio 安裝期間安裝。使用 Visual Studio 安裝程式安裝 SSDT 會新增基本 SSDT 功能，因此您仍然需要執行 [SSDT 獨立安裝程式](#ssdt-for-vs-2017-standalone-installer)以取得 AS、IS 和 RS 工具。*

## <a name="install-ssdt-with-visual-studio-2017"></a>使用 Visual Studio 2017 安裝 SSDT

若要在 [Visual Studio 安裝](https://docs.microsoft.com/visualstudio/install/install-visual-studio)期間安裝 SSDT，請選取 [Data storage and processing] \(資料儲存和處理\) 工作負載，然後選取 [SQL Server Data Tools]。 如果已安裝 Visual Studio，您可以[編輯工作負載清單](https://docs.microsoft.com/visualstudio/install/modify-visual-studio)來包含 SSDT：![資料儲存和處理工作負載](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)



## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>安裝 Analysis Services、Integration Services 和 Reporting Services 工具
若要安裝 AS、IS 和 RS 專案支援，請執行 [SSDT 獨立安裝程式](#ssdt-for-vs-2017-standalone-installer)。 

此安裝程式會列出可新增 SSDT 工具的 Visual Studio 執行個體。 如果未安裝 Visual Studio，請選取 [Install a new SQL Server Data Tools instance] \(安裝新的 SQL Server Data Tools 執行個體\) 會以 Visual Studio 的最小版本安裝 SSDT，但若要獲得最佳體驗，建議搭配使用 SSDT 與 [Visual Studio 的最新版本](https://www.visualstudio.com/downloads)。 

![選取 AS、IS、RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT for VS 2017 (獨立安裝程式)

[![下載](../ssdt/media/download.png) 下載 SSDT for Visual Studio 2017 (15.8.2) ](https://go.microsoft.com/fwlink/?linkid=2038031) 

> [!IMPORTANT]
> - 如有安裝 *Analysis Services 專案*及 *Reporting Services 專案*延伸模組，請先予以解除安裝，並關閉所有 VS 執行個體，再安裝 SSDT for Visual Studio 2017 (15.8.2)。
> - 修正了將內有包含指令碼工作/一般檔案目的地之套件的 SSIS 專案部署到 Azure-SSIS 時，會導致該套件無法在 Azure-SSIS 中執行的問題。
> - 適用於 Visual Studio 2017 (15.8.2) 的 SSDT 不支援設計包含 Oracle/Teradata 來源或目的地的套件。 使用適用於 Visual Studio 2017 (15.8) 的 SSDT。



**版本資訊**  
  
版本編號：15.8.2  
組建編號：14.0.16182.0  
發行日期：2018 年 11 月 5 日  

如需變更的完整清單，請參閱[變更記錄](changelog-for-sql-server-data-tools-ssdt.md)。

SSDT for Visual Studio 2017 與 Visual Studio 具有相同的[系統需求](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs)。  

### <a name="available-languages---ssdt-for-vs-2017"></a>可用語言 - 適用於 VS 2017 的 SSDT

這版**適用於 VS 2017 的 SSDT** 提供下列語言版本：  

[簡體中文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x804) | 
[繁體中文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x404) | 
[英文 (美國)]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x409) | 
[法文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x40c)  
[德文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x407) | 
[義大利文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x410) | 
[日文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x411) | 
[韓文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x412) | 
[葡萄牙文 (巴西)]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x416) | 
[俄文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x419) | 
[西班牙文]( https://go.microsoft.com/fwlink/?linkid=2038031&clcid=0x40a)  


## <a name="offline-install"></a>離線安裝

若要在未連線到網際網路時安裝 SSDT，請遵循本節所述的步驟。 如需詳細資訊，請參閱[建立 Visual Studio 2017 的網路安裝](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio)。

首先，請在連線時完成下列步驟：

1. [下載 SSDT 的獨立安裝程式](#ssdt-for-vs-2017-standalone-installer)。
2. [下載 vs_sql.exe](https://aka.ms/vs/15/release/vs_sql.exe)。
3. 在連線時，執行下列命令下載離線安裝所需的全部檔案。 使用 `--layout`選項是關鍵，這會為離線安裝下載實際檔案。 以實際配置路徑取代 <filepath> 來儲存檔案。

   
   A.   若是使用特定語言，請傳遞地區設定：`vs_sql.exe --layout c:\<filepath> --lang en-us` (一種語言 ~1GB)  
   B. 若是使用所有語言，請省略 `--lang` 引數：`vs_sql.exe --layout c:\<filepath>` (所有語言 ~3.9GB)。

4. 執行 `SSDT-Setup-ENU.exe /layout c:\<filepath>` 以將 SSDT 承載擷取至與所下載 VS2017 檔案相同的 `<filepath>` 位置。 這能確保兩者的所有檔案都會合併到同一個配置資料夾。

完成前述步驟之後，就可以離線執行下列步驟：

1. 執行 `vs_setup.exe --NoWeb`，以安裝 VS2017 Shell 及 SQL Server 資料專案。
2. 從配置資料夾執行 `SSDT-Setup-ENU.exe /install`，並選取 SSIS/SSRS/SSAS。

   - 若要自動安裝，請執行或 `SSDT-Setup-ENU.exe /INSTALLALL[:vsinstances] /passive`  

若要查看可用的選項，請執行 `SSDT-Setup-ENU.exe /help`

## <a name="supported-sql-versions"></a>支援的 SQL 版本
  
|專案範本|支援的 SQL 平台|  
|-------------------|--------------------|  
關聯式資料庫|  SQL Server 2005* - SQL Server 2017<br> (使用 SSDT 17.x 或適用於 Visual Studio 2017 的 SSDT 來連線至 [Linux 上的 SQL Server](../linux/sql-server-linux-overview.md))<br /><br />Azure SQL Database<br /><br />Azure SQL 資料倉儲 (僅支援查詢；尚不支援資料庫專案)<br /><br />  * SQL Server 2005 支援已被取代，<br /><br /> 請改為官方支援的 SQL 版本|
  |Analysis Services 模型<br /><br />Reporting Services 報表 | SQL Server 2008 - SQL Server 2017|
  |Integration Services 封裝| SQL Server 2012 - SQL Server 2017    |
  
## <a name="dacfx"></a>DacFx
SSDT for Visual Studio 2015 和 SSDT for Visual Studio 2017 都會使用 DacFx 17.4.1：[下載資料層應用程式架構 (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508)。

## <a name="previous-versions"></a>舊版

若要下載及安裝 SSDT for Visual Studio 2015 或更舊版的 SSDT，請參閱[舊版 SQL Server Data Tools (SSDT 及 SSDT-BI)](previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md)。



## <a name="next-steps"></a>後續步驟  
安裝 SSDT 後，請逐步完成這些教學課程，了解如何使用 SSDT 建立資料庫、封裝、資料模型及報表：  

- [專案導向的離線資料庫開發](project-oriented-offline-database-development.md)  
- [SSIS 教學課程：建立簡易 ETL 封裝](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Analysis Services 教學課程](../analysis-services/analysis-services-tutorials-ssas.md)  
- [建立基本資料表報表 (SSRS 教學課程)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]


## <a name="see-also"></a>另請參閱  
[SSDT MSDN 論壇](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[SSDT 團隊部落格](https://blogs.msdn.com/b/ssdt/)  
[DACFx API 參考](https://msdn.microsoft.com/library/dn645454.aspx)  
[下載 SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
