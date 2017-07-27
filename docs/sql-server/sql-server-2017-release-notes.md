---
title: "SQL Server 2017 版本資訊 |Microsoft 文件"
ms.custom: 
ms.date: 05/16/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
caps.latest.revision: 41
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 6aa73e749d4f308265dfe27a160802c15a391a3e
ms.openlocfilehash: a2950b6aef0e12653efbb9eb26fd3f1ae6cb951e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/17/2017

---
# <a name="sql-server-2017-release-notes"></a>SQL Server 2017 版本資訊
本主題描述 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] 的限制及問題。 如需相關資訊，請參閱下列各項：

- [新功能 SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)。
- [SQL Server 上的 Linux 版本資訊](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes)。
- [SQL Server Reporting Services 版本資訊](../reporting-services/reporting-services-release-notes.md)。

 **現在就試試看：**    
   -   [![從 Evaluation Center 下載](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  從 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] Evaluation Center **[下載](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="sql-server-2017-release-candidate-rc1---july-2017"></a>SQL Server 2017 候選版 (RC1 - 2017 年 7 月)

### <a name="sql-server-integration-services-ssis-rc1---july-2017"></a>SQL Server Integration Services (SSIS) (RC1 - 2017 年 7 月)
- **問題和客戶的影響：**為了一致性和可讀性，預存程序 **[catalog].[create_execution]** 的參數 *runincluster* 已重新命名為 *runinscaleout*。
- **因應措施：**如果您有現成的指令碼可在 [相應放大] 中執行套件，您必須將參數名稱從 *runincluster* 變更為 *runinscaleout*，以確保這些指令碼在 RC1 中正常運作。

- **問題和客戶的影響：**SQL Server Management Studio (SSMS) 17.1 和舊版無法在 RC1 的 [相應放大] 中觸發套件執行。 錯誤訊息為：「*@runincluster* 不是程序 **create_execution** 的參數。」 SSMS 的下一個版本 17.2 版中將會修正此問題。 SSMS 17.2 版和更新版本支援 [相應放大] 中的新參數名稱和套件執行。 
- **因應措施：**在 SSMS 17.2 版可用之前，您可以使用現有的 SSMS 版本來產生套件執行指令碼，然後將指令碼中的 *runincluster* 參數名稱變更為 *runinscaleout*，再執行此指令碼。

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-21-may--2017"></a>SQL Server 2017 CTP 2.1 (可能 2017)
### <a name="documentation-ctp-21"></a>文件 (CTP 2.1)
- **問題和對客戶的影響︰**[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] 的文件有所限制，且內容會隨附於 [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] 文件集。  文中專門針對 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] 的內容會以「適用於」標示。 
- **問題和對客戶的影響︰**[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] 沒有離線內容。

### <a name="sql-server-reporting-services-ctp-21"></a>SQL Server Reporting Services (CTP 2.1)

- **問題和客戶的影響：**如果您有 SQL Server Reporting Services 和 Power BI 報表伺服器在相同電腦，並解除安裝其中一個，您將不再能夠連線到其餘的報表伺服器與報表伺服器組態管理員。
- **因應措施**若要解決此問題，您必須執行下列作業之後解除安裝其中一個伺服器。

    1. 啟動命令提示字元，以系統管理員模式。
    2. 前往剩餘的報表伺服器安裝所在目錄。

        *Power BI 報表伺服器的預設位置： C:\Program Files\Microsoft Power BI 報表伺服器*

        *SQL Server Reporting Services 的預設位置： C:\Program Files\Microsoft SQL Server 報告的服務*

    3. 接著移至下一個資料夾。 這會是*SSRS*或*PBIRS*根據剩餘的項目。
    4. 移至 WMI 資料夾。
    5. 執行下列命令：

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        您可以忽略下列錯誤，如果您看到它。

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

### <a name="tsqllanguageservicemsi-ctp-21"></a>TSqlLanguageService.msi (CTP 2.1)

- **問題和客戶的影響：** 2016年的版本的電腦上安裝之後*TSqlLanguageService.msi* （透過 SQL 安裝程式或安裝為獨立可轉散發套件） v13.* (SQL 2016) 的版本*Microsoft.SqlServer.Management.SqlParser.dll*和*Microsoft.SqlServer.Management.SystemMetadataProvider.dll*會移除。 任何有相依的這些組件的 2016年版本的應用程式將會再停止運作，提供類似的錯誤：*錯誤： 無法載入檔案或組件 ' Microsoft.SqlServer.Management.SqlParser，Version = 13.0.0.0，Culture = neutral，PublicKeyToken = 89845dcd8080cc91' 或其中一個相依性。系統找不到指定的檔案。*

   此外，嘗試重新安裝 TSqlLanguageService.msi 2016 版本將會失敗並出現訊息：*安裝的 Microsoft SQL Server 2016 T-SQL 語言服務失敗，因為較高的版本已經存在電腦上*。

- **因應措施**暫時解決此問題，並修正應用程式相依於 v13 版本的組件請遵循下列步驟：

   1. 移至**新增/移除程式**
   1. 尋找*Microsoft SQL Server vNext T-SQL 語言服務 CTP2.1*，以滑鼠右鍵按一下，然後選取**解除安裝**。
   1. 移除元件之後，修復就會中斷應用程式 (或重新安裝適當版本的*TSqlLanguageService.MSI*)

   這個因應措施會移除這些組件，v14 版本，以便任何相依於 v14 版本的應用程式將無法再運作。 如果需要這些組件，而任何由並行 2016年安裝不是個別安裝不需要的。

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-20-april--2017"></a>SQL Server 2017 CTP 2.0 (第 2017 年 4 月)
### <a name="documentation-ctp-20"></a>文件 (CTP 2.0)
- **問題和對客戶的影響︰**[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] 的文件有所限制，且內容會隨附於 [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] 文件集。  文中專門針對 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] 的內容會以「適用於」標示。 
- **問題和對客戶的影響︰**[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] 沒有離線內容。

### <a name="always-on-availability-groups"></a>AlwaysOn 可用性群組

- **問題和客戶的影響：**裝載可用性群組次要複本的 SQL Server 執行個體當機，如果 SQL Server 主要版本低於裝載主要複本的執行個體。 會影響所有受支援版本的 SQL Server 裝載 SQL server 的可用性群組升級[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]CTP 2.0。 發生這種情況下的下列步驟。 

> 1. 使用者可升級 SQL Server 執行個體裝載次要複本根據[最佳做法](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)。
> 2. 升級之後，容錯移轉，而且新升級的次要變成主要複本之前完成可用性群組中的所有次要複本的升級。 舊的主要現在是次要複本，這可能會比主要更舊版本。
> 3. 可用性群組處於不支援的組態和任何剩餘的次要複本可能會很容易損毀。 

- **因應措施**連接到裝載的新的主要複本並移除從組態錯誤的次要複本的 SQL Server 執行個體。

   `ALTER AVAILABILITY GROUP agName REMOVE REPLICA ON NODE instanceName`

   裝載次要複本的 SQL Server 執行個體復原。

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) 與 SQL Server 工程團隊交流 
- [堆疊溢位 (標記 sql-server) - 詢問技術性問題](http://stackoverflow.com/questions/tagged/sql-server)
- [MSDN 論壇 - 詢問技術性問題](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect - 報告錯誤及要求功能](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - 有關 R 的一般討論](https://www.reddit.com/r/SQLServer/)

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
