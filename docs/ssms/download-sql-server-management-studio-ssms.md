---
title: 下載 SQL Server Management Studio (SSMS) | Microsoft Docs
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
ms.technology: ssms
ms.topic: conceptual
keywords:
- 安裝 ssms, 下載 ssms, 最新的 ssms
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- sql management studio install
- download sql management studio
- ms sql management studio
- install sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
author: dnethi
ms.author: dinethi
ms.custom: ''
ms.date: 07/26/2019
ms.openlocfilehash: 46174db6dc0008dbeb9490cc96cf41cdef1bc3ed
ms.sourcegitcommit: a1ddeabe94cd9555f3afdc210aec5728f0315b14
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70123099"
---
# <a name="download-sql-server-management-studio-ssms"></a>下載 SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) 是整合式環境，可用於管理任何 SQL 基礎結構，從 SQL Sever 到 Azure SQL Database 皆適用。 SSMS 提供工具來設定、監視以及管理 SQL Server 執行個體和資料庫。 使用 SSMS，即可部署、監視和升級應用程式所使用的資料層元件，以及建置查詢和指令碼。

使用 SSMS，即可查詢、設計與管理資料庫和資料倉儲，而不論它們位在何處：本機電腦上或雲端中。

SSMS 是免費的！

## <a name="download-ssms-182"></a>下載 SSMS 18.2

**SSMS 18.2 現已開放使用，且是 *SQL Server Management Studio* 的正式運作 (GA) 版本，其提供 [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] 的支援！**

**[![下載](../ssdt/media/download.png) 下載 SQL Server Management Studio 18.2](https://go.microsoft.com/fwlink/?linkid=2099720)**

SSMS 18.2 是 SSMS 最新的正式運作 (GA) 版本。 若先前已安裝 SSMS 18 的 GA 版本，則安裝 SSMS 18.2 會將其升級至 18.2。 若您已安裝舊的 SSMS 18.x「預覽」  版本，則您必須在安裝 SSMS 18.2 前先將它解除安裝。

**版本資訊**

- 版本號碼：18.2  
- 組建編號：15.0.18142.0  
- 發行日期：2019 年 7 月25 日  

若您有意見或建議，或是要回報問題，則連絡 SSMS 小組的最佳方式是透過 [UserVoice](https://aka.ms/sqlfeedback)。

SSMS 18.x 安裝不會升級或取代 SSMS 17.x 版或更早版本。 SSMS 18.x 會與舊版本並存安裝，讓兩個版本同時可供使用。

如果電腦中包含並存安裝的 SSMS，請確認已針對您的特定需求啟動正確的版本。 最新版本會標記為 **Microsoft SQL Server Management Studio 18**

## <a name="available-languages-ssms-182"></a>可用語言 (SSMS 18.2)

此版 SSMS 提供下列語言版本：

SQL Server Management Studio 18.2：  
[簡體中文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x804) | [繁體中文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x404) | [英文 (美國)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x409) | [法文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x40c) | [德文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x407) | [義大利文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x410) | [日文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x411) | [韓文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x412) | [葡萄牙文 (巴西)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x416) | [俄文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x419) | [西班牙文](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x40a)

> [!NOTE]
> SQL Server PowerShell 模組為透過 PowerShell 資源庫個別安裝的模組。 如需詳細資訊，請參閱[下載 SQL Server PowerShell 模組](download-sql-server-ps-module.md)。

## <a name="new-in-this-release-ssms-182"></a>此版本 (SSMS 18.2) 中的新功能

|  新項目  |  詳細資料  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Always Encrypted | 更新記憶體保護區提供者以支援 Azure 證明。 |
| IntelliSense/編輯器 | 新增資料分類的支援  |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | SSMS 索引對話方塊 - 新增了新的索引選項。OPTIMIZE_FOR_SEQUENTIAL_KEY |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | 新增 Intellisense 支援 |
| 查詢執行或結果 | 在訊息中新增了「完成時間」，用來追蹤指定的查詢何時完成其執行。 |
| 查詢執行或結果  | 允許顯示更多的資料 (結果為文字) 並將其儲存在資料格 (結果為方格) 中。 SSMS 現在允許這兩者最多有 2M 個字元 (最高分別從 256 和 64K)。 這也解決了使用者無法從方格資料格抓取超過 43680 個字元的問題。 |
| 執行程序表 | 啟用內嵌純量 UDF 功能時(ContainsInlineScalarTsqlUdfs)，在 QueryPlan 中新增了新屬性。 |
| Integration Services (SSIS) | Azure 中 SSIS 套件排程器的效能最佳化 |
|  |  |

如需此版本中最新功能的詳細資料，請參閱 [SSMS 版本資訊](release-notes-ssms.md)。

## <a name="supported-sql-offerings-ssms-182"></a>支援的 SQL 供應項目 (SSMS 18.2)

* 此版本的 SSMS 適用於所有[支援的 SQL Server 2008 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044)，並提供最高層級的支援以使用 Azure SQL Database 和 Azure SQL 資料倉儲中最新雲端功能。
* 此外，SSMS 18.x 可以與 SSMS 17.x、SSMS 16.x 或 SQL Server 2014 SSMS 及更早的版本並存安裝。
* SQL Server Integration Services (SSIS) - SSMS 17.x 或更新版本不支援連線至舊版 SQL Server Integration Services 服務。 若要連線至舊版 Integration Services 的舊版本，請使用與 SQL Server 版本一致的 SSMS 版本。 例如，使用 SSMS 16.x 連線至舊版 SQL Server 2016 Integration Services 服務。 SSMS 17.x 和 SSMS 16.x 可以並存安裝在相同電腦上。 自 SQL Server 2012 發行之後，建議使用 SSIS Catalog 資料庫 SSISDB 來儲存、管理、執行和監視 Integration Services 套件。 如需詳細資訊，請參閱 [SSIS 目錄](../integration-services/catalog/ssis-catalog.md)。

## <a name="supported-operating-systems-ssms-182"></a>支援的作業系統 (SSMS 18.2)

搭配最新推出的服務套件使用時，這一版 SSMS 支援下列 64 位元平台：

- Windows 10 (64 位元) <sup>*</sup>
- Windows 8.1 (64 位元)
- Windows Server 2019 (64 位元)
- Windows Server 2016 (64 位元) <sup>*</sup>
- Windows Server 2012 R2 (64 位元)
- Windows Server 2012 (64 位元)
- Windows Server 2008 R2 (64 位元)

<sup>*</sup> 需要版本 1607 (10.0.14393) 或更新版本

> [!NOTE]
> SSMS 僅能在 Windows 上執行。 若您需要能在 Windows 以外平台上執行的工具，請查看 Azure Data Studio。 Azure Data Studio 是一個新的跨平台工具，可在 macOS、Linux 以及 Windows 上執行。 如需詳細資料，請參閱 [Azure Data Studio](../azure-data-studio/what-is.md)。

## <a name="release-notes-ssms-182"></a>版本資訊 (SSMS 18.2)

此版本有一些[已知問題](release-notes-ssms.md#known-issues-181)。

如需此版本的詳細資料，請參閱 [SSMS 版本資訊](release-notes-ssms.md)。

## <a name="previous-ssms-releases"></a>舊版 SSMS

[先前 SQL Server Management Studio 版本](../ssms/release-notes-ssms.md#previous-ssms-releases)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

## <a name="see-also"></a>另請參閱

- [教學課程：SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [SQL Server Management Studio 文件](sql-server-management-studio-ssms.md)
- [其他的更新與 Service Pack](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [下載 SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
