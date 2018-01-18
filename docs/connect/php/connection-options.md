---
title: "連線選項 |Microsoft 文件"
ms.custom: 
ms.date: 01/16/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d1ea295-8e34-438e-8468-4bbc0f76192c
caps.latest.revision: "37"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b90819fbed37aa41a23a257caf287fd563da6ffa
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="connection-options"></a>連線選項
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

本主題列出關聯陣列中允許的選項 (當使用[sqlsrv_connect](../../connect/php/sqlsrv-connect.md) SQLSRV 驅動程式) 或資料來源名稱 (dsn) 中允許的關鍵字 (使用時[pdo:: __construct](../../connect/php/pdo-construct.md) PDO_SQLSRV 驅動程式)。  

|索引鍵|Value|Description|預設值|  
|-------|---------|---------------|-----------|  
|APP|字串|指定在追蹤中使用的應用程式名稱。|未設定值。|  
|ApplicationIntent|字串|宣告連接到伺服器時的應用程式工作負載類型。 可能的值為 ReadOnly 和 ReadWrite。<br /><br />如需 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 對於 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]的支援，請參閱 [PHP Driver for SQL Server 對於高可用性、災害復原的支援](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|ReadWrite|  
|AttachDBFileName|字串|指定伺服器所應附加的資料庫檔案。|未設定值。|  
|驗證|其中一個下列字串：<br /><br />'SqlPassword'<br /><br />'ActiveDirectoryPassword'|指定驗證模式。|未設定。|  
|CEKeystoreProvider<br />CEKeystoreName<br />CEKeystoreEncryptKey|字串|指定的路徑、 名稱和 「 一律加密 」 功能給自訂金鑰存放區提供者的加密金鑰。 必須設定所有三個值，才能進行連接時，適當地設定自訂金鑰存放區提供者。 |未設定值。|
|CharacterSet<br /><br />(PDO_SQLSRV 驅動程式不支援)|字串|指定用來將資料傳送至伺服器的字元集。<br /><br />可能的值為 SQLSRV_ENC_CHAR 和 UTF-8。 如需詳細資訊，請參閱 [How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)。|SQLSRV_ENC_CHAR|  
|ColumnEncryption|**啟用**或**已停用**|指定是否啟用 「 永遠加密 」 功能。 |已停用|  
|ConnectionPooling|1 或 **true** 表示開啟連接共用。<br /><br />0 或 **false** 表示關閉連接共用。|指定是否從連接集區指派連接 (1 或**true**) 與否 (0 或**false**)。<sup>1</sup>|**true** (1)|  
|資料庫|字串|要建立的連接使用指定的資料庫名稱<sup>2</sup>。|使用登入的預設資料庫。|  
|驅動程式|字串|指定用來與 SQL Server 通訊的 Microsoft ODBC 驅動程式。<br /><br />可能的值為：<br />ODBC Driver for SQL Server 17<br />ODBC Driver 13 for SQL Server<br />ODBC Driver 11 for SQL Server (僅限 Windows)。|若未指定 Driver 關鍵字，Microsoft Drivers for PHP for SQL Server 嘗試尋找支援的 Microsoft ODBC 驅動程式存在在系統中，從 ODBC 的最新版本，依此類推。|  
|Encrypt|1 或 **true** 表示開啟加密。<br /><br />0 或 **false** 表示關閉加密。|指定是否要加密與 SQL Server 的通訊 (1 或**true**) 或未加密 (0 或**false**)<sup>3</sup>。|**false** (0)|  
|Failover_Partner|字串|指定在主要伺服器無法使用時所要使用的伺服器和資料庫鏡像執行個體 (如果已啟用和設定)。<br /><br />搭配使用 Failover_Partner 與 MultiSubnetFailover 時有一些限制。 如需詳細資訊，請參閱 [PHP Driver for SQL Server 對於高可用性、災害復原的支援](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|未設定值。|  
|LoginTimeout|整數 （SQLSRV 驅動程式）<br /><br />字串 （PDO_SQLSRV 驅動程式）|指定將連接嘗試認定為失敗之前所等候的秒數。|不會逾時。|  
|MultipleActiveResultSets|1 或 **true** 會使用 Multiple Active Result Sets。<br /><br />0 或 **false** 會停用 Multiple Active Result Sets。|停用或明確啟用 Multiple Active Result Sets (MARS) 的支援。<br /><br />如需詳細資訊，請參閱[如何： 停用 Multiple Active Resultsets &#40;MARS &#41;](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).|true (1)|  
|MultiSubnetFailover|字串|請務必指定**multiSubnetFailover = yes**連接到可用性群組接聽程式時[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]可用性群組或[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]容錯移轉叢集執行個體。 **multiSubnetFailover = yes**設定[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]來提供更快速偵測與 （目前） 使用中伺服器的連接。 可能的值為 [是] 和 [否]。<br /><br />如需 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 對於 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]的支援，請參閱 [PHP Driver for SQL Server 對於高可用性、災害復原的支援](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|否|  
|PWD<br /><br />(PDO_SQLSRV 驅動程式不支援)|字串|指定要使用 SQL Server 驗證進行連接時使用的使用者識別碼相關聯的密碼<sup>4</sup>。|未設定值。|  
|QuotedId|1 或**true**使用 sql-92 規則。<br /><br />0 或 **false** 會使用傳統規則。|指定是否要對引號識別項使用 sql-92 規則 (1 或**true**) 或使用傳統的 TRANSACT-SQL 規則 (0 或**false**)。|**true** (1)|  
|ReturnDatesAsStrings<br /><br />(PDO_SQLSRV 驅動程式不支援)|1 或 **true** 會以字串的形式傳回日期和時間類型。<br /><br />0 或 **false** 會以 PHP **DateTime** 類型的形式傳回日期和時間類型。|以字串或 PHP 類型的形式擷取日期和時間類型 (datetime、date、time、datetime2 和 datetimeoffset)。 使用 PDO_SQLSRV 驅動程式時，會以字串的形式傳回日期。 PDO_SQLSRV 驅動程式沒有**datetime**型別。<br /><br />如需詳細資訊，請參閱 [如何：使用 SQLSRV 驅動程式，以字串的形式擷取日期和時間類型](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)。|**false**|  
|可捲動|字串|「緩衝處理」表示您需要用戶端 (緩衝) 資料指標，它可讓您快取記憶體中的整個結果集。 如需詳細資訊，請參閱[資料指標類型 &#40;SQLSRV 驅動程式 &#41;](../../connect/php/cursor-types-sqlsrv-driver.md).|順向資料指標|  
|Server<br /><br />(SQLSRV 驅動程式不支援)|字串|要連接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 執行個體。<br /><br />您也可以指定虛擬網路名稱，以連接到 AlwaysOn 可用性群組。 如需 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 對於 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]的支援，請參閱 [PHP Driver for SQL Server 對於高可用性、災害復原的支援](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|伺服器是必要的關鍵字 (雖然它不一定是連接字串中的第一個關鍵字)。 如果伺服器名稱未傳遞至關鍵字，嘗試連接到本機執行個體。<br /><br />傳遞至伺服器的值可以是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 執行個體的名稱，或是執行個體的 IP 位址。 您可以選擇性地指定連接埠號碼 (例如， `sqlsrv:server=(local),1033`)。<br /><br />從 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 3.0 版開始，您也可以透過 `server=(localdb)\instancename`指定 LocalDB 執行個體。 如需詳細資訊，請參閱 [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)。|  
|TraceFile|字串|為用於追蹤資料的檔案指定路徑。|未設定值。|  
|TraceOn|1 或 **true** 會啟用追蹤。<br /><br />0 或 **false** 會停用追蹤。|指定是否要啟用 ODBC 追蹤 (1 或**true**) 或停用 (0 或**false**) 所建立的連接。|**false** (0)|  
|TransactionIsolation|SQLSRV 驅動程式會使用下列值：<br /><br />SQLSRV_TXN_READ_UNCOMMITTED<br /><br />SQLSRV_TXN_READ_COMMITTED<br /><br />SQLSRV_TXN_REPEATABLE_READ<br /><br />SQLSRV_TXN_SNAPSHOT<br /><br />SQLSRV_TXN_SERIALIZABLE<br /><br />PDO_SQLSRV 驅動程式會使用下列值：<br /><br />PDO::SQLSRV_TXN_READ_UNCOMMITTED<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED<br /><br />PDO::SQLSRV_TXN_REPEATABLE_READ<br /><br />PDO::SQLSRV_TXN_SNAPSHOT<br /><br />PDO::SQLSRV_TXN_SERIALIZABLE|指定交易隔離等級。<br /><br />如需關於交易隔離的詳細資訊，請參閱 SQL Server 文件中的 [設定交易隔離等級](http://go.microsoft.com/fwlink/?LinkID=191497) 。|SQLSRV_TXN_READ_COMMITTED<br /><br />或<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED|  
|TransparentNetworkIPResolution|**啟用**或**已停用**|會影響第一個解決主機名稱的 IP 沒有回應，並有多個 Ip 時的連接順序相關聯的主機名稱。<br /><br />它會提供不同的連接順序 MultiSubnetFailover 與互動。 如需詳細資訊，請參閱[使用透明網路 IP 解析](https://docs.microsoft.com/en-us/sql/connect/odbc/using-transparent-network-ip-resolution)。|已啟用|
|TrustServerCertificate|1 或 **true** 會信任憑證。<br /><br />0 或 **false** 會不信任憑證。|指定用戶端應信任 (1 或**true**) 或拒絕 (0 或**false**) 的自我簽署的伺服器憑證。|**false** (0)|  
|UID<br /><br />(PDO_SQLSRV 驅動程式不支援)|字串|指定要使用 SQL Server 驗證進行連接時使用的使用者識別碼<sup>4</sup>。|未設定值。|  
|WSID|字串|指定用於追蹤之電腦的名稱。|未設定值。|  

1. `ConnectionPooling`屬性不能啟用/停用連線集區在 Linux 和 mac。 請參閱[連接共用 (Microsoft Drivers for PHP for SQL Server)](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md)。

2. 已建立的連接上執行的所有查詢都對所指定的資料庫*資料庫*屬性。 不過，如果使用者有適當的權限，可以存取其他資料庫中的資料使用完整限定的名稱。 例如，如果*主要*資料庫已設定*資料庫*連接屬性，就仍然可以執行 TRANSACT-SQL 查詢來存取*AdventureWorks.HumanResources.Employee*資料表使用的完整限定的名稱。  

3. 啟用 [加密]  後可能會影響某些應用程式的效能，因為加密資料需要額外的計算負荷。  

4. 要連接的 *UID* 驗證進行連接時， *PWD* 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 屬性都必須設定。  

許多支援的索引鍵都是 ODBC 連接字串屬性。 如需 ODBC 連接字串的相關資訊，請參閱 [搭配 SQL Native Client 使用連接字串關鍵字](http://go.microsoft.com/fwlink/?LinkId=105504)。  

## <a name="see-also"></a>另請參閱  
[連接到伺服器](../../connect/php/connecting-to-the-server.md)  
