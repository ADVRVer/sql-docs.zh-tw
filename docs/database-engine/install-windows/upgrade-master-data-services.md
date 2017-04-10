---
title: "升級 Master Data Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
caps.latest.revision: 31
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 30
---
# 升級 Master Data Services
  升級至 Microsoft [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 的情況如下。  
  
-   [升級但不包含 Database Engine 升級](../../database-engine/install-windows/upgrade-master-data-services.md#noengine)  
  
-   [升級且包含 Database Engine 升級](../../database-engine/install-windows/upgrade-master-data-services.md#engine)  
  
-   [在兩部電腦的情況下升級](../../database-engine/install-windows/upgrade-master-data-services.md#twocomputer)  
  
-   [包含從備份中還原資料庫的升級](../../database-engine/install-windows/upgrade-master-data-services.md#restore)  
  
> [!IMPORTANT]  
>  -   不支援從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 版本升級到 CTP2 版本。  
> -   在執行任何升級之前備份您的資料庫。  
> -   升級程序會重新建立預存程序，並升級 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 使用的資料表。 您對這些元件所做的任何自訂可能會遺失。  
> -   模型部署封裝只能在之前建立這些封裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中使用。 您不能將在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中建立的模型部署封裝部署到 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]。  
> -   將 Data Quality Services 和 Master Data Services 升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之後，所有適用於 Excel 的舊版 Master Data Services 增益集將無法再繼續運作。 您可以從 [Microsoft 下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=47343)下載適用於 Excel 的 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Master Data Services 增益集。  
  
##  <a name="fileLocation"></a> 檔案位置  
  
-   根據預設，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\130\Master Data Services。  
  
-   根據預設，在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\120\Master Data Services。  
  
-   根據預設，在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\110\Master Data Services。  
  
-   根據預設，在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\Master Data Services。  
  
##  <a name="noengine"></a> 升級但不包含 Database Engine 升級  
 在此情況下，您會繼續使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 主控您的 MDS 資料庫。 但是，您必須升級 MDS 資料庫的結構描述，然後建立 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式以存取 MDS 資料庫。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web 應用程式無法再存取 MDS 資料庫。  
  
 您可以在相同電腦上安裝 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 和舊版 SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)])。 檔案會安裝在不同的位置 (如[檔案位置](#fileLocation)所示)。  
  
 **升級但不包含 Database Engine 升級**  
  
1.  安裝 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 及您想要的其他任何功能。  
  
    1.  開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式精靈。  
  
    2.  按一下左窗格中的 [安裝]。  
  
    3.  按一下右窗格中的 [新增 SQL Server 獨立安裝或將功能加入至現有安裝]。  
  
    4.  在 [功能選擇] 頁面上，選取 [[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]] 以及您想要安裝的其他任何功能。  
  
    5.  完成精靈。  
  
2.  升級 MDS 資料庫結構描述。  
  
    1.  開啟 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。  
  
        > [!IMPORTANT]  
        >  若要升級 MDS 資料庫結構描述，您必須以建立 MDS 資料庫時指定之系統管理員帳戶的身分登入。 在 MDS 資料庫的 mdm.tblUser 中，這位使用者的 [識別碼] 值為 **1**。  
  
    2.  按一下左窗格中的 [資料庫組態]。  
  
    3.  按一下右窗格中的 [選取資料庫]，然後指定 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 資料庫執行個體的資訊。  
  
    4.  按一下 [升級資料庫] 可啟動 [升級資料庫精靈]。 如需詳細資訊，請參閱[升級資料庫精靈 &#40;Master Data Services 組態管理員&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。  
  
3.  建立 Web 應用程式。  
  
    1.  開啟 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。  
  
    2.  按一下左窗格中的 **[Web 組態]**。  
  
    3.  從右窗格的 [網站] 清單中，選取下列其中一個選項：  
  
        -   [預設的網站]，然後按一下 [建立應用程式]。  
  
        -   [建立新的網站]。 建立網站時，便會自動建立新的 Web 應用程式。  
  
        > [!IMPORTANT]  
        >  在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 Master Data Services 組態管理員中，可讓您選取您在舊版 SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) 中的現有 MDS Web 應用程式。 您絕不能選取現有的 Web 應用程式，而是必須建立 MDS 的 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Web 應用程式。 否則，當您嘗試將 Web 應用程式與升級的 MDS 資料庫建立關聯時，將會收到錯誤，說明因為該頁面的相關組態資料無效，所以無法存取所要求的頁面。  
        >   
        >  如果您要為 MDS Web 應用程式使用相同的名稱 (別名) 作為現有 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) Web 應用程式，您必須先將 Web 應用程式和相關聯的應用程式集區從 IIS 刪除，然後使用 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 版的 Master Data Services 組態管理員，以相同的名稱建立 Web 應用程式。 如需從 IIS 移除 Web 應用程式和應用程式集區的資訊，請參閱[移除應用程式 (IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) 和[移除應用程式集區 (IIS)](http://go.microsoft.com/fwlink/?LinkId=323538)。  
  
4.  建立新 Web 應用程式與升級的 MDS 資料庫的關聯。  
  
    1.  在 [建立應用程式與資料庫間的關聯] 區段中，按一下 [選取]。  
  
    2.  選取 MDS 資料庫。  
  
    3.  按一下 **[套用]**。  
  
##  <a name="engine"></a> 升級且包含 Database Engine 升級  
 在此案例中，您要將資料庫引擎和 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 應用程式從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 升級到 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]。  
  
 **升級且包含 Database Engine 升級**  
  
1.  **僅適用於 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**：開啟 [控制台] > [程式和功能]，並解除安裝 Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]。  
  
2.  將資料庫引擎升級至 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]。 如需詳細資訊，請參閱[選擇 Database Engine 升級方法](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md)。  
  
3.  完成[升級但不包含 Database Engine 升級](#noengine)中的所有步驟。  
  
##  <a name="twocomputer"></a> 在兩部電腦的情況下升級  
 在此案例中，您會升級在兩部電腦上安裝 SQL Server 的系統：一部安裝 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]，另一部安裝 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]。  
  
 如果安裝 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]，則繼續分別使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]，在一部電腦上主控您的 MDS 資料庫。 但是，您必須升級 MDS 資料庫的結構描述，然後使用 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Web 應用程式來存取 MDS 資料庫。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web 應用程式無法再存取 MDS 資料庫。  
  
 **在兩部電腦的情況下升級**  
  
-   完成[升級但不包含 Database Engine 升級](#noengine)中的所有步驟。  
  
##  <a name="restore"></a> 包含從備份中還原資料庫的升級  
 在此案例中，[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 會隨著 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 安裝在同一部電腦或兩部不同的電腦上。 資料庫已在升級之前備份至 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 之前的版本上，而且必須還原資料庫。  
  
 **包含從備份中還原資料庫的升級**  
  
1.  安裝 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 及您想要的其他任何功能。  
  
    1.  開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式精靈。  
  
    2.  按一下左窗格中的 [安裝]。  
  
    3.  按一下右窗格中的 [新增 SQL Server 獨立安裝或將功能加入至現有安裝]。  
  
    4.  在 [功能選擇] 頁面上，選取 [[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]] 以及您想要安裝的其他任何功能。  
  
    5.  完成精靈。  
  
2.  還原備份的資料庫。  
  
3.  升級 MDS 資料庫結構描述，並建立 Web 應用程式，以及建立新 Web 應用程式與升級之 MDS 資料庫的關聯。 如需指示，請參閱[升級但不包含 Database Engine 升級](#noengine)中的步驟 2-4  
  
## 疑難排解  
 **問題**：當您開啟 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式時，出現「用戶端版本與資料庫版本不相容」錯誤訊息。  
  
 **解決方法**：當 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 主資料管理員 Web 應用程式嘗試存取已升級到 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Master Data Services 的資料庫時，就會發生此問題。 您必須改用 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Web 應用程式。  
  
 如果您升級 MDS 資料庫結構描述時，未在 IIS 中停止 [MDS 應用程式集區] 然後再重新啟動，也可能會發生此問題。 重新啟動 [MDS 應用程式集區] 即可更正此問題。  
  
## 另請參閱  
 [安裝 Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  