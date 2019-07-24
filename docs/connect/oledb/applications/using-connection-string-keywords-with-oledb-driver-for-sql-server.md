---
title: 利用 OLE DB Driver for SQL Server 使用連接字串關鍵字 | Microsoft Docs
description: 利用 OLE DB Driver for SQL Server 使用連接字串關鍵字
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: pelopes
ms.openlocfilehash: f7f64a2ffc1761dee49297777bc29ab45463252a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989226"
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>利用 OLE DB Driver for SQL Server 使用連接字串關鍵字
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server Api 的某些 OLE DB 驅動程式會使用連接字串來指定連接屬性。 連接字串是關鍵字和關聯值的清單，每一個關鍵字都會識別特定的連接屬性。  
  
> [!NOTE]
> OLE DB Driver for SQL Server 允許模稜兩可的連接字串，以維護回溯相容性 (例如，某些關鍵字可能會指定一次以上，而且可能會允許衝突的關鍵字，好讓解決方案以位置或優先順序為根據)。 SQL Server 的 OLE DB 驅動程式的未來版本, 在連接字串中可能不會造成混淆。 修改應用程式時，適合使用適用於 SQL Server 的 OLE DB 驅動程式來消除任何對於模稜兩可連接字串的相依性。  
  
 下列各節描述在使用 SQL Server 做為資料提供者的 OLE DB 驅動程式時, 可以與 OLE DB Driver for SQL Server 和 ActiveX Data Objects (ADO) 搭配使用的關鍵字。  

  
## <a name="ole-db-driver-connection-string-keywords"></a>OLE DB 驅動程式連接字串關鍵字  
 OLE DB 應用程式有兩種方法可初始化資料來源物件：  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 在第一個案例中，提供者字串可用來初始化連接屬性，其方式是在 DBPROPSET_DBINIT 屬性集中設定 DBPROP_INIT_PROVIDERSTRING 屬性。 在第二個案例中，初始化字串可以傳遞給 **IDataInitialize::GetDataSource** 方法來初始化連接屬性。 這兩個方法都會初始化相同的 OLE DB 連接屬性，但是會使用不同的關鍵字集合。 **IDataInitialize::GetDataSource** 所使用的關鍵字集合，至少是初始化屬性群組內的屬性描述。  
  
 如果任何提供者字串設定所包含的對應 OLE DB 屬性設定為預設值或明確設定為某個值，OLE DB 屬性值將在提供者字串中覆寫此設定。  
  
 在提供者字串中透過 DBPROP_INIT_PROVIDERSTRING 值所設定的布林屬性是使用 "yes" 和 "no" 的值所設定。 在初始化字串中使用 **IDataInitialize::GetDataSource** 所設定的布林值屬性，是使用 "True" 和 "False" 的值所設定。  
  
 使用 **IDataInitialize::GetDataSource** 的應用程式，也可以使用 **IDBInitialize::Initialize** 所用的關鍵字，但是只適用於沒有預設值的屬性。 如果應用程式在初始化字串中同時使用 **IDataInitialize::GetDataSource** 關鍵字和 **IDBInitialize::Initialize** 關鍵字，則會使用 **IDataInitialize::GetDataSource** 關鍵字設定。 強烈建議您不要讓應用程式在 **IDataInitialize:GetDataSource** 連接字串中使用 **IDBInitialize::Initialize** 關鍵字，因為將來的版本可能無法維護這個行為。  
  
> [!NOTE]  
>  透過 **IDataInitialize::GetDataSource** 傳遞的連接字串會經由 **IDBProperties::SetProperties** 轉換成屬性並加以套用。 如果元件服務在 **IDBProperties::GetPropertyInfo** 中找到屬性描述，此屬性將會作為獨立屬性來套用。 否則，它將會透過 DBPROP_PROVIDERSTRING 屬性來套用。 例如, 如果您指定連接字串**資料來源 = server1;Server = server2**,**資料來源**將會設定為屬性, 但是**伺服器**會進入提供者字串。  
  
 如果您指定相同提供者特有之屬性的多個執行個體，將會使用第一個屬性的值。  
  
 OLE DB 應用程式使用的連接字串如果搭配 **IDBInitialize::Initialize** 使用 DBPROP_INIT_PROVIDERSTRING，其語法如下：  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 可以選擇用大括號括住屬性值，這樣是很好的作法。 如此可在屬性值包含非英數字元時避免問題發生。 值中的第一個右大括號應該會結束該值，所以值不能包含右大括號字元。  
  
 連接字串關鍵字 = 符號後面的空格字元應該解譯為常值，即使該值括在引號內也是如此。  
  
 下表描述可搭配 DBPROP_INIT_PROVIDERSTRING 使用的關鍵字。  
  
|關鍵字|初始化屬性|Description|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|"Address" 的同義字。|  
|**位址**|SSPROP_INIT_NETWORKADDRESS|執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之伺服器的網路位址。 **Address** 通常是伺服器的網路名稱，不過也可能是其他名稱，例如管道、IP 位址，或 TCP/IP 通訊埠和通訊端位址。<br /><br /> 若您指定 IP 位址，請確定在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 組態管理員中已啟用 TCP/IP 或具名管道通訊協定。<br /><br /> 使用 SQL Server 的 OLE DB 驅動程式時,**位址**的值會優先于連接字串中傳遞給**伺服器**的值。 同時請注意，`Address=;` 將會連接到 **Server** 關鍵字中指定的伺服器，而 `Address= ;, Address=.;`、`Address=localhost;` 和 `Address=(local);` 都會造成與本機伺服器的連接。<br /><br /> **Address** 關鍵字的完整語法如下：<br /><br /> [_通訊協定_ **:** ]_位址_[ **,** _連接埠 &#124;\pipe\pipename_]<br /><br /> _protocol_ 可以是 **tcp** (TCP/IP)、 **lpc** (共用記憶體) 或 **np** (具名管道)。 如需通訊協定的詳細資訊, 請參閱[設定用戶端通訊協定](../../../database-engine/configure-windows/configure-client-protocols.md)。<br /><br /> 如果未指定_通訊協定_或**網路**關鍵字, SQL Server 的 OLE DB 驅動程式會使用 Configuration Manager 中[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]指定的通訊協定順序。<br /><br /> *port* 是在指定伺服器上所要連接的通訊埠。 根據預設，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會使用通訊埠 1433。|   
|**APP**|SSPROP_INIT_APPNAME|識別應用程式的字串。|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|宣告連接到伺服器時的應用程式工作負載類型。 可能的值為 **ReadOnly** 和 **ReadWrite**。<br /><br /> 預設值為**ReadWrite**。 如需 SQL Server 支援[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]之 OLE DB 驅動程式的詳細資訊, 請參閱[OLE DB 驅動程式以取得高可用性和嚴重損壞修復的 SQL Server 支援](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|可附加資料庫的主要檔案名稱，包括完整路徑名稱。 若要使用 **AttachDBFileName**，您還必須使用提供者字串 Database 關鍵字來指定資料庫名稱。 如果之前已附加資料庫，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會重新附加它 (它會使用附加的資料庫當做連接的預設值)。|  
|**驗證**<a href="#table1_1"> <sup id="table1_authmode"> **1**</sup></a>|SSPROP_AUTH_MODE|指定使用的 SQL 或 Active Directory 驗證。 有效值為：<br/><ul><li>`(not set)`: 由其他關鍵字決定的驗證模式。</li><li>`ActiveDirectoryPassword:`使用登入識別碼和密碼 Active Directory 驗證。</li><li>`ActiveDirectoryIntegrated:`使用目前登入之使用者的 Windows 帳號憑證, 來 Active Directory 的整合式驗證。</li><br/>**注意:** **建議**使用`Integrated Security` (或`Trusted_Connection`) 驗證關鍵字或其`Authentication`對應屬性的應用程式將關鍵字的值 (或其對應的屬性) 設定為`ActiveDirectoryIntegrated` , 以啟用新的加密和憑證驗證行為。<br/><br/><li>`SqlPassword:`使用登入識別碼和密碼進行驗證。</li><br/>**注意:** **建議**使用`SQL Server`驗證的應用程式將`Authentication`關鍵字的值 (或其對應的屬性) 設定為`SqlPassword` , 以啟用新的加密和憑證驗證行為。</ul>|
|**自動轉譯**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" 的同義字。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|設定 OEM/ANSI 字元轉譯。 可辨識的值為 "yes" 和 "no"。|  
|**[資料庫備份]**|DBPROP_INIT_CATALOG|資料庫名稱。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|指定要使用的資料類型處理模式。 認得的值為 "0" (代表提供者資料類型) 和 "80" (代表 SQL Server 2000 資料類型)。|  
|**加密t**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|指定當透過網路傳送資料以前，是否應該先加密資料。 可能的值為 "yes" 和 "no"。 預設值為 "no"。|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|用於資料庫鏡像的容錯移轉伺服器名稱。|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|容錯移轉夥伴的 SPN。 預設值為空字串。 空字串會導致 SQL Server 的 OLE DB 驅動程式使用預設的提供者產生的 SPN。|  
|**語言**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 語言。|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|當伺服器為 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更新版本時，啟用或停用連接上的 Multiple Active Result Sets (MARS)。 可能的值為 "yes" 和 "no"。 預設值為 "no"。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|在連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可用性群組的可用性群組接聽程式或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體時，一律指定 **MultiSubnetFailover=yes**。 **MultiSubnetFailover=yes** 會設定 OLE DB Driver for SQL Server ，以提供對 (目前) 使用中伺服器更快速的偵測與連接。 可能的值為 [是]  和 [否]  。 預設值為 **No**。 例如：<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> 如需 SQL Server 支援[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]之 OLE DB 驅動程式的詳細資訊, 請參閱[OLE DB 驅動程式以取得高可用性和嚴重損壞修復的 SQL Server 支援](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|"Network" 的同義字。|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|用來建立組織中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之連接的網路程式庫。|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|"Network" 的同義字。|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|網路封包大小。 預設值是 4096。|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|接受的值為 "yes" 和 "no" 字串。 當為 "no" 時，不允許使用資料來源物件來保存敏感性驗證資訊。|  
|**PWD**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入密碼。|  
|**Server**|DBPROP_INIT_DATASOURCE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。 此值必須是網路上的伺服器名稱、IP 位址，或是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 組態管理員別名的名稱。<br /><br /> 如果沒有指定，就會連接至本機電腦上的預設執行個體。<br /><br /> **Address**關鍵字會覆寫**Server**關鍵字。<br /><br /> 您可藉由指定下列其中一個項目，連接到本機伺服器上的預設執行個體：<br /><br /> **伺服器=;**<br /><br /> **伺服器=.;**<br /><br /> **伺服器=(local);**<br /><br /> **伺服器=(local);**<br /><br /> **伺服器=(localhost);**<br /><br /> **伺服器=(localdb)\\** *執行個體名稱* **;**<br /><br /> 如需 LocalDB 支援的詳細資訊, 請參閱[OLE DB 驅動程式以取得 localdb 的 SQL Server 支援](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)。<br /><br /> 若要指定的具名執行個體[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，附加 **\\** _InstanceName_。<br /><br /> 如果未指定伺服器，就會連接到本機電腦上的預設執行個體。<br /><br /> 若您指定 IP 位址，請確定在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 組態管理員中已啟用 TCP/IP 或具名管道通訊協定。<br /><br /> **Server** 關鍵字的完整語法如下：<br /><br /> **伺服器=** [_通訊協定_ **:** ]*伺服器*[ **,** _連接埠_]<br /><br /> _protocol_ 可以是 **tcp** (TCP/IP)、 **lpc** (共用記憶體) 或 **np** (具名管道)。<br /><br /> 下列是指定具名管道的範例：<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> 此程式碼行指定具名管道通訊協定、本機電腦上的具名管道 (`\\.\pipe`)、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱 (`MSSQL$MYINST01`) 以及具名管道的預設名稱 (`sql/query`)。<br /><br /> 如果未指定*通訊協定*或**網路**關鍵字, SQL Server 的 OLE DB 驅動程式會使用 Configuration Manager 中[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]指定的通訊協定順序。<br /><br /> *port* 是在指定伺服器上所要連接的通訊埠。 根據預設，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會使用通訊埠 1433。<br /><br /> 使用 SQL Server 的 OLE DB 驅動程式時, 在連接字串中傳遞至**伺服器**的值開頭會忽略空格。|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|伺服器的 SPN。 預設值為空字串。 空字串會導致 SQL Server 的 OLE DB 驅動程式使用預設的提供者產生的 SPN。|  
|**逾時**|DBPROP_INIT_TIMEOUT|等候資料來源初始化完成的時間量 (以秒為單位)。|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|當為 "yes" 時, 會指示 SQL Server 的 OLE DB 驅動程式使用 Windows 驗證模式進行登入驗證。 否則會指示 OLE DB Driver for SQL Server 使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用者名稱和密碼進行登入驗證，而且必須指定 UID 和 PWD 密碼。|  
|**TrustServerCertificate**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|接受的值為 "yes" 和 "no" 字串。 預設值為 "no"，這表示將會驗證伺服器憑證。|  
|**UID**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入名稱。|  
|**UseFMTONLY**|SSPROP_INIT_USEFMTONLY|控制連線到 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 及更新版本時，如何擷取中繼資料。 可能的值為 "yes" 和 "no"。 預設值為 "no"。<br /><br />根據預設, SQL Server 的 OLE DB 驅動程式會使用[sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)和[sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)預存程式來取得中繼資料。 這些預存程式有一些限制 (例如, 在臨時表上操作時, 它們會失敗)。 將**UseFMTONLY**設定為 [是], 會指示驅動程式改為使用[SET set fmtonly](../../../t-sql/statements/set-fmtonly-transact-sql.md)來進行中繼資料抓取。|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|這個關鍵字已被取代, 而 SQL Server 的 OLE DB 驅動程式會忽略它的設定。|  
|**WSID**|SSPROP_INIT_WSID|工作站識別碼。|  
  
<b id="table1_1">[1]:</b>若要改善安全性, 使用驗證/存取權杖初始化屬性或其對應的連接字串關鍵字時, 會修改加密和憑證驗證行為。 如需詳細資訊, 請參閱[加密和憑證驗證](../features/using-azure-active-directory.md#encryption-and-certificate-validation)。

 OLE DB 應用程式使用的連接字串如果使用 **IDataInitialize::GetDataSource**，其語法如下：  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 屬性的使用必須符合其範圍內所允許的語法。  例如，**WSID** 會使用大括號 ( **{}** ) 字元，而 **Application Name** 會使用單引號 ( **'** ) 或雙引號 ( **"** ) 字元。 只有字串屬性可以加上引號。 嘗試將整數或列舉屬性加上引號將會產生「連接字串沒有符合 OLE DB 規格」錯誤。  
  
 您可以選擇用單引號或雙引號括住屬性值，這樣是很好的作法。 如此可在值包含非英數字元時避免問題發生。 使用的引號字元也可出現在值當中，但前提必須是雙引號字元。  
  
 連接字串關鍵字 = 符號後面的空格字元應該解譯為常值，即使該值括在引號內也是如此。  
  
 如果連接字串具有下表所列的多個屬性，將會使用最後一個屬性的值。  
  
 下表說明可搭配 **IDataInitialize::GetDataSource** 使用的關鍵字：  
  
|關鍵字|初始化屬性|Description|  
|-------------|-----------------------------|-----------------|  
|**存取權杖**<a href="#table2_1"><sup id="table2_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|用來驗證 Azure Active Directory 的存取權杖。 <br/><br/>**注意:** 指定此關鍵字`UID`, 以及`Trusted_Connection`、、或`Authentication`連接字串關鍵字`PWD`或其對應的屬性/關鍵字, 是錯誤的。|
|**Application Name**|SSPROP_INIT_APPNAME|識別應用程式的字串。|  
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|宣告連接到伺服器時的應用程式工作負載類型。 可能的值為 **ReadOnly** 和 **ReadWrite**。<br /><br /> 預設值為**ReadWrite**。 如需 SQL Server 支援[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]之 OLE DB 驅動程式的詳細資訊, 請參閱[OLE DB 驅動程式以取得高可用性和嚴重損壞修復的 SQL Server 支援](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|  
|**驗證**<a href="#table2_1"> <sup> **1**</sup></a>|SSPROP_AUTH_MODE|指定使用的 SQL 或 Active Directory 驗證。 有效值為：<br/><ul><li>`(not set)`: 由其他關鍵字決定的驗證模式。</li><li>`ActiveDirectoryPassword:`使用登入識別碼和密碼 Active Directory 驗證。</li><li>`ActiveDirectoryIntegrated:`使用目前登入之使用者的 Windows 帳號憑證, 來 Active Directory 的整合式驗證。</li><br/>**注意:** **建議**使用`Integrated Security` (或`Trusted_Connection`) 驗證關鍵字或其`Authentication`對應屬性的應用程式將關鍵字的值 (或其對應的屬性) 設定為`ActiveDirectoryIntegrated` , 以啟用新的加密和憑證驗證行為。<br/><br/><li>`SqlPassword:`使用登入識別碼和密碼進行驗證。</li><br/>**注意:** **建議**使用`SQL Server`驗證的應用程式將`Authentication`關鍵字的值 (或其對應的屬性) 設定為`SqlPassword` , 以啟用新的加密和憑證驗證行為。</ul>|
|**自動轉譯**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" 的同義字。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|設定 OEM/ANSI 字元轉譯。 認得的值為 "true" 和 "false"。|  
|**連接逾時**|DBPROP_INIT_TIMEOUT|等候資料來源初始化完成的時間量 (以秒為單位)。|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 語言名稱。|  
|**資料來源**|DBPROP_INIT_DATASOURCE|組織中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。<br /><br /> 如果沒有指定，就會連接至本機電腦上的預設執行個體。<br /><br /> 如需有關有效位址語法的詳細資訊，請參閱本主題中對於 **Server** 關鍵字的說明。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|指定要使用的資料類型處理模式。 認得的值為 "0" (代表提供者資料類型) 和 "80" (代表 [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] 資料類型)。|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|用於資料庫鏡像的容錯移轉伺服器名稱。|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|容錯移轉夥伴的 SPN。 預設值為空字串。 空字串會導致 SQL Server 的 OLE DB 驅動程式使用預設的提供者產生的 SPN。|  
|**初始目錄**|DBPROP_INIT_CATALOG|資料庫名稱。|  
|**初始檔案名**|SSPROP_INIT_FILENAME|可附加資料庫的主要檔案名稱，包括完整路徑名稱。 若要使用 **AttachDBFileName**，您還必須使用提供者字串 DATABASE 關鍵字來指定資料庫名稱。 如果之前已附加資料庫，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會重新附加它 (它會使用附加的資料庫當做連接的預設值)。|  
|**整合式安全性**|DBPROP_AUTH_INTEGRATED|接受 "SSPI" 值進行 Windows 驗證。|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|啟用或停用連接上的 Multiple Active Result Sets (MARS)。 認得的值為 "true" 和 "false"。 預設值為 "false"。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|在連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可用性群組的可用性群組接聽程式或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體時，一律指定 **MultiSubnetFailover=True**。 **MultiSubnetFailover=True** 會設定 OLE DB Driver for SQL Server ，以提供對 (目前) 使用中伺服器更快速的偵測與連線。 可能的值為 **True** 和 **False**。 預設值為 **False**。 例如：<br /><br /> `MultiSubnetFailover=True`<br /><br /> 如需 SQL Server 支援[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]之 OLE DB 驅動程式的詳細資訊, 請參閱[OLE DB 驅動程式以取得高可用性和嚴重損壞修復的 SQL Server 支援](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|組織中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的網路位址。<br /><br /> 如需有關有效位址語法的詳細資訊，請參閱本主題中對於 **Address** 關鍵字的說明。|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|用來建立組織中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之連接的網路程式庫。|  
|**封包大小**|SSPROP_INIT_PACKETSIZE|網路封包大小。 預設值是 4096。|  
|**密碼**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入密碼。|  
|**保存安全性資訊**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|接受的值為 "true" 和 "false" 字串。 當為 "false" 時，不允許使用資料來源物件來保存敏感性驗證資訊。|  
|**提供者**||針對 SQL Server 的 OLE DB 驅動程式, 這應該是 "內含 MSOLEDBSQL.H"。|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|伺服器的 SPN。 預設值為空字串。 空字串會導致 SQL Server 的 OLE DB 驅動程式使用預設的提供者產生的 SPN。|  
|**信任伺服器憑證**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|接受的值為 "true" 和 "false" 字串。 預設值為 "false"，這表示將會驗證伺服器憑證。|  
|**為資料使用加密**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|指定當透過網路傳送資料以前，是否應該先加密資料。 可能的值為 "true" 和 "false"。 預設值為 "false"。|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|控制連線到 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 及更新版本時，如何擷取中繼資料。 可能的值為 "true" 和 "false"。 預設值為 "false"。<br /><br />根據預設, SQL Server 的 OLE DB 驅動程式會使用[sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)和[sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)預存程式來取得中繼資料。 這些預存程式有一些限制 (例如, 在臨時表上操作時, 它們會失敗)。 將 [**使用 set fmtonly** ] 設定為 "true", 會指示驅動程式改為使用[SET set fmtonly](../../../t-sql/statements/set-fmtonly-transact-sql.md)來進行中繼資料抓取。|  
|**使用者識別碼**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入名稱。|  
|**Workstation ID**|SSPROP_INIT_WSID|工作站識別碼。|  
  
<b id="table2_1">[1]:</b>若要改善安全性, 使用驗證/存取權杖初始化屬性或其對應的連接字串關鍵字時, 會修改加密和憑證驗證行為。 如需詳細資訊, 請參閱[加密和憑證驗證](../features/using-azure-active-directory.md#encryption-and-certificate-validation)。

 **請注意**：在此連接字串中，"Old Password" 屬性會設定 SSPROP_AUTH_OLD_PASSWORD，這是無法透過提供者字串屬性取得的目前密碼 (可能已過期)。  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>ActiveX Data Objects (ADO) 連接字串關鍵字  
 ADO 應用程式會設定 **ADODBConnection** 物件的 **ConnectionString** 屬性，或是提供連接字串當做 **ADODBConnection** 物件之 **Open** 方法的參數。  
  
 ADO 應用程式也可以使用 OLE DB **IDBInitialize::Initialize** 方法所使用的關鍵字，但是只適用於沒有預設值的屬性。 如果應用程式在初始化字串中同時使用 ADO 關鍵字和 **IDBInitialize::Initialize** 關鍵字，將會使用 ADO 關鍵字設定。 強烈建議您只讓應用程式使用 ADO 連接字串關鍵字。  
  
 ADO 使用的連接字串具有以下語法：  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 可以選擇用雙引號括住屬性值，這樣是很好的作法。 如此可在值包含非英數字元時避免問題發生。 屬性值不能包含雙引號。  
  
 下表描述可搭配 ADO 連接字串使用的關鍵字：  
  
|關鍵字|初始化屬性|Description|  
|-------------|-----------------------------|-----------------|  
|**存取權杖**<a href="#table3_1"><sup id="table3_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|用來驗證 Azure Active Directory 的存取權杖。<br/><br/>**注意:** 指定此關鍵字`UID`, 以及`Trusted_Connection`、、或`Authentication`連接字串關鍵字`PWD`或其對應的屬性/關鍵字, 是錯誤的。|
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|宣告連接到伺服器時的應用程式工作負載類型。 可能的值為 **ReadOnly** 和 **ReadWrite**。<br /><br /> 預設值為**ReadWrite**。 如需 SQL Server 支援[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]之 OLE DB 驅動程式的詳細資訊, 請參閱[OLE DB 驅動程式以取得高可用性和嚴重損壞修復的 SQL Server 支援](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|  
|**Application Name**|SSPROP_INIT_APPNAME|識別應用程式的字串。|  
|**驗證**<a href="#table3_1"> <sup> **1**</sup></a>|SSPROP_AUTH_MODE|指定使用的 SQL 或 Active Directory 驗證。 有效值為：<br/><ul><li>`(not set)`: 由其他關鍵字決定的驗證模式。</li><li>`ActiveDirectoryPassword:`使用登入識別碼和密碼 Active Directory 驗證。</li><li>`ActiveDirectoryIntegrated:`使用目前登入之使用者的 Windows 帳號憑證, 來 Active Directory 的整合式驗證。</li><br/>**注意:** **建議**使用`Integrated Security` (或`Trusted_Connection`) 驗證關鍵字或其`Authentication`對應屬性的應用程式將關鍵字的值 (或其對應的屬性) 設定為`ActiveDirectoryIntegrated` , 以啟用新的加密和憑證驗證行為。<br/><br/><li>`SqlPassword:`使用登入識別碼和密碼進行驗證。</li><br/>**注意:** **建議**使用`SQL Server`驗證的應用程式將`Authentication`關鍵字的值 (或其對應的屬性) 設定為`SqlPassword` , 以啟用新的加密和憑證驗證行為。</ul>|
|**自動轉譯**|SSPROP_INIT_AUTOTRANSLATE|"AutoTranslate" 的同義字。|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|設定 OEM/ANSI 字元轉譯。 認得的值為 "true" 和 "false"。|  
|**連接逾時**|DBPROP_INIT_TIMEOUT|等候資料來源初始化完成的時間量 (以秒為單位)。|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 語言名稱。|  
|**資料來源**|DBPROP_INIT_DATASOURCE|組織中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。<br /><br /> 如果沒有指定，就會連接至本機電腦上的預設執行個體。<br /><br /> 如需有關有效位址語法的詳細資訊，請參閱本主題中對於 **Server** 關鍵字的說明。|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|指定即將使用之資料類型處理的模式。 認得的值為 "0" (代表提供者資料類型) 和 "80" (代表 SQL Server 2000 資料類型)。|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|用於資料庫鏡像的容錯移轉伺服器名稱。|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|容錯移轉夥伴的 SPN。 預設值為空字串。 空字串會導致 SQL Server 的 OLE DB 驅動程式使用預設的提供者產生的 SPN。|  
|**初始目錄**|DBPROP_INIT_CATALOG|資料庫名稱。|  
|**初始檔案名**|SSPROP_INIT_FILENAME|可附加資料庫的主要檔案名稱，包括完整路徑名稱。 若要使用 **AttachDBFileName**，您還必須使用提供者字串 DATABASE 關鍵字來指定資料庫名稱。 如果之前已附加資料庫，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會重新附加它 (它會使用附加的資料庫當做連接的預設值)。|  
|**整合式安全性**|DBPROP_AUTH_INTEGRATED|接受 "SSPI" 值進行 Windows 驗證。|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|當伺服器為 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更新版本時，啟用或停用連接上的 Multiple Active Result Sets (MARS)。 認得的值為 "true" 和 "false"。預設值是 "false"。|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|在連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可用性群組的可用性群組接聽程式或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體時，一律指定 **MultiSubnetFailover=True**。 **MultiSubnetFailover=True** 會設定 OLE DB Driver for SQL Server ，以提供對 (目前) 使用中伺服器更快速的偵測與連線。 可能的值為 **True** 和 **False**。 預設值為 **False**。 例如：<br /><br /> `MultiSubnetFailover=True`<br /><br /> 如需 SQL Server 支援[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]之 OLE DB 驅動程式的詳細資訊, 請參閱[OLE DB 驅動程式以取得高可用性和嚴重損壞修復的 SQL Server 支援](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|組織中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的網路位址。<br /><br /> 如需有關有效位址語法的詳細資訊，請參閱本主題中對於 **Address** 關鍵字的說明。|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|用來建立組織中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之連接的網路程式庫。|  
|**封包大小**|SSPROP_INIT_PACKETSIZE|網路封包大小。 預設值是 4096。|  
|**密碼**|DBPROP_AUTH_PASSWORD|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入密碼。|  
|**保存安全性資訊**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|接受的值為 "true" 和 "false" 字串。 如果為 "false"，表示不允許資料來源物件保存機密的驗證資訊。|  
|**提供者**||針對 SQL Server 的 OLE DB 驅動程式, 這應該是 "內含 MSOLEDBSQL.H"。|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|伺服器的 SPN。 預設值為空字串。 空字串會導致 SQL Server 的 OLE DB 驅動程式使用預設的提供者產生的 SPN。|  
|**信任伺服器憑證**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|接受的值為 "true" 和 "false" 字串。 預設值為 "false"，這表示將會驗證伺服器憑證。|  
|**為資料使用加密**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|指定當透過網路傳送資料以前，是否應該先加密資料。 可能的值為 "true" 和 "false"。 預設值為 "false"。|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|控制連線到 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 及更新版本時，如何擷取中繼資料。 可能的值為 "true" 和 "false"。 預設值為 "false"。<br /><br />根據預設, SQL Server 的 OLE DB 驅動程式會使用[sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)和[sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)預存程式來取得中繼資料。 這些預存程式有一些限制 (例如, 在臨時表上操作時, 它們會失敗)。 將 [**使用 set fmtonly** ] 設定為 "true", 會指示驅動程式改為使用[SET set fmtonly](../../../t-sql/statements/set-fmtonly-transact-sql.md)來進行中繼資料抓取。|  
|**使用者識別碼**|DBPROP_AUTH_USERID|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入名稱。|  
|**Workstation ID**|SSPROP_INIT_WSID|工作站識別碼。|  
  
<b id="table3_1">[1]:</b>若要改善安全性, 使用驗證/存取權杖初始化屬性或其對應的連接字串關鍵字時, 會修改加密和憑證驗證行為。 如需詳細資訊, 請參閱[加密和憑證驗證](../features/using-azure-active-directory.md#encryption-and-certificate-validation)。

 **請注意**：在此連接字串中，"Old Password" 屬性會設定 SSPROP_AUTH_OLD_PASSWORD，這是無法透過提供者字串屬性取得的目前密碼 (可能已過期)。  
  
## <a name="see-also"></a>另請參閱  
 [利用 OLE DB Driver for SQL Server 建置](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
