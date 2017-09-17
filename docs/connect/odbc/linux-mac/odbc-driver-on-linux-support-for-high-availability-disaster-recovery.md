---
title: "ODBC Driver on Linux 及 macOS-高可用性和災害復原 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa656c5b-a935-40bf-bc20-e517ca5cd0ba
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d7b6c72d350b718a7676bffd72c261b7cfa72667
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-driver-on-linux-and-macos-support-for-high-availability-and-disaster-recovery"></a>在 Linux 和 macOS 高可用性和災害復原的支援上的 ODBC 驅動程式
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Linux 及 macOS 支援的 ODBC 驅動程式[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]。 如需 [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)] 的相關資訊，請參閱：  
  
-   [可用性群組接聽程式、 用戶端連接性及應用程式容錯移轉 (SQL Server)](http://msdn.microsoft.com/library/hh213417.aspx)  
  
-   [建立及設定可用性群組 (SQL Server)](http://msdn.microsoft.com/library/ff878265.aspx)  
  
-   [容錯移轉叢集和 AlwaysOn 可用性群組 (SQL Server)](http://msdn.microsoft.com/library/ff929171.aspx)  
  
-   [使用中次要： 可讀取次要複本 （AlwaysOn 可用性群組）](http://msdn.microsoft.com/library/ff878253.aspx)  
  
您可以在連接字串中指定給定可用性群組的可用性群組接聽程式。 如果在 Linux 或 macOS ODBC 應用程式連接到容錯移轉可用性群組中的資料庫，則原始連接會中斷和應用程式必須開啟新連接，才能在容錯移轉之後繼續工作。

Linux 和 macOS 上的 ODBC 驅動程式循序逐一查看所有與 DNS 主機名稱相關聯，如果您未連接到可用性群組接聽程式，以及多個 IP 位址與主機名稱相關聯的 IP 位址。

如果 DNS 伺服器的第一個傳回的 IP 位址不是可連接，這些反覆運算可能會很耗時。 連接到可用性群組接聽程式時，驅動程式會嘗試平行建立的所有 IP 位址的連接。 如果連接嘗試成功，驅動程式就會捨棄任何暫止的連接嘗試。

> [!NOTE]  
> 因為連接可能會失敗，因為可用性群組容錯移轉，實作連接重試邏輯。重試失敗的連線，直到重新連接。 增加連接逾時並實作連接重試邏輯，可提高連接到可用性群組的機率。

## <a name="connecting-with-multisubnetfailover"></a>使用 MultiSubnetFailover 進行連接

請務必指定**MultiSubnetFailover = Yes** (或**= True**) 時，連線到[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]可用性群組接聽程式或[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]容錯移轉叢集執行個體。 **MultiSubnetFailover**啟用更快速的容錯移轉的所有可用性群組和容錯移轉叢集執行個體中的[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]。 **MultiSubnetFailover**也會大幅縮短單一和多重子網路 AlwaysOn 拓撲的容錯移轉時間。 在多重子網路容錯移轉期間，用戶端會嘗試平行連接。 子網路容錯移轉期間，此驅動程式會積極重試 TCP 連接。

**MultiSubnetFailover** 連接屬性表示應用程式正在可用性群組或容錯移轉叢集執行個體中部署。 驅動程式會嘗試連接到主要資料庫[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]執行個體來嘗試連接到所有 IP 位址。 使用連接時**MultiSubnetFailover = Yes**，用戶端重試 TCP 連接的速度比作業系統的預設 TCP 重新傳輸間隔快。 **MultiSubnetFailover=Yes** 可在容錯移轉 AlwaysOn 可用性群組或 AlwaysOn 容錯移轉叢集執行個體之後更快速地重新連接。 **MultiSubnetFailover = Yes**適用於單一-和多重子網路可用性群組和容錯移轉叢集執行個體。  

在連接到可用性群組接聽程式或容錯移轉叢集執行個體時，請使用 **MultiSubnetFailover=Yes** 。 否則，您的應用程式效能造成負面影響。

連接到可用性群組或容錯移轉叢集執行個體中的伺服器時請注意下列事項：
  
-   指定**MultiSubnetFailover = Yes**來連接到單一子網路或多重子網路可用性群組時改善效能。

-   指定可用性群組的可用性群組接聽程式為您的連接字串中的伺服器。
  
-   您無法連接到[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]超過 64 個 IP 位址設定的執行個體。

-   同時[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]驗證或 Kerberos 驗證可以搭配**MultiSubnetFailover = Yes**而不會影響應用程式的行為。

-   您可以增加 **loginTimeout** 的值，以容納容錯移轉時間並減少應用程式連接重試次數。

-   不支援分散式交易。  
  
如果唯讀路由不在作用中，在下列狀況下，連接到可用性群組中的次要複本位置將會失敗：  
  
1.  如果未設定次要複本位置接受連接。  
  
2.  如果應用程式使用 **ApplicationIntent=ReadWrite** ，而且已針對唯讀存取設定次要複本位置。  
  
如果設定主要複本拒絕唯讀工作負載，而且連接字串包含 **ApplicationIntent=ReadOnly**，則連接會失敗。  
  
## <a name="specifying-application-intent"></a>指定應用程式意圖  
當 **ApplicationIntent=ReadOnly**時，用戶端在連接到啟用 AlwaysOn 的資料庫時會要求讀取工作負載。 在連接時和在 USE 資料庫陳述式期間，只針對啟用 AlwaysOn 的資料庫，則伺服器會強制執行的意圖。

**ApplicationIntent** 關鍵字不適用於舊版唯讀資料庫。  

資料庫可以允許或不允許 AlwaysOn 目標資料庫上的讀取工作負載 (使用**ALLOW_CONNECTIONS**子句**PRIMARY_ROLE**和**SECONDARY_ROLE** [!INCLUDE[tsql](../../../includes/tsql_md.md)]陳述式。)  
  
**ApplicationIntent** 關鍵字用於啟用唯讀路由。  
  
## <a name="read-only-routing"></a>唯讀路由  
唯讀路由功能可確保資料庫之唯讀複本的可用性。 若要啟用唯讀路由：  
  
1.  連接到 AlwaysOn 可用性群組的可用性群組接聽程式。  
  
2.  **ApplicationIntent** 連接字串關鍵字必須設為 **ReadOnly**。  
  
3.  資料庫管理員必須設定可用性群組，以啟用唯讀路由。  
  
使用唯讀路由的多個連接可以連接到不同的唯讀複本。 資料庫同步處理的變更或伺服器路由組態的變更，可能會導致用戶端連接至不同的唯讀複本。 若要確保所有唯讀要求連接至相同的唯讀複本，請勿將可用性群組接聽程式傳遞至 **Server** 連接關鍵字。 請改為指定唯讀執行個體的名稱。  
  
使用唯讀路由時，連接的所需時間預期會比連接到主要複本長。 因此，請增加您的登入逾時。 唯讀路由會先連接到主要複本，然後尋找最佳可用的可讀次要複本。  
  
## <a name="odbc-syntax"></a>ODBC 語法

兩個 ODBC 連接字串關鍵字支援[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]:  
  
-   **ApplicationIntent**  
  
-   **MultiSubnetFailover**  
  
如需 ODBC 連接字串關鍵字的詳細資訊，請參閱 [搭配 SQL Server Native Client 使用連接字串關鍵字](http://msdn.microsoft.com/library/ms130822.aspx)。  
  
對等連接屬性如下：
  
-   **SQL_COPT_SS_APPLICATION_INTENT**  
  
-   **SQL_COPT_SS_MULTISUBNET_FAILOVER**  
  
如需 ODBC 連接屬性的詳細資訊，請參閱[SQLSetConnectAttr](http://msdn.microsoft.com/library/ms131709.aspx)。  
  
ODBC 應用程式使用[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]可以使用兩個函數之一進行連接：  
  
|函數|Description|  
|------------|---------------|  
|[SQLConnect 函式](../../../odbc/reference/syntax/sqlconnect-function.md)|**SQLConnect**同時支援**ApplicationIntent**和**MultiSubnetFailover**透過資料來源名稱 (DSN) 或連接屬性。|  
|[SQLDriverConnect 函式](../../../odbc/reference/syntax/sqldriverconnect-function.md)|**SQLDriverConnect**支援**ApplicationIntent**和**MultiSubnetFailover**透過 DSN、 連接字串關鍵字或連接屬性。|
  
## <a name="see-also"></a>另請參閱  

[連接字串關鍵字和資料來源名稱 (DSN)](../../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)

[程式設計指導方針](../../../connect/odbc/linux-mac/programming-guidelines.md)

[版本資訊](../../../connect/odbc/linux-mac/release-notes.md)  

