---
title: 設定連線屬性 | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f1b62700-f046-488d-bd6b-a5cd8fc345b7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c96c61ad94bb93e2c2c370452021cfb5b95efdba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004460"
---
# <a name="setting-the-connection-properties"></a>設定連接屬性

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

您可以使用各種方法指定連接字串屬性：

- 當您使用 DriverManager 類別進行連線時，連線 URL 中的屬性為 name=value。
- 在 DriverManager 類別中 Connect 方法的*properties*參數中, As name = value 屬性。
- 作為驅動程式資料來源的適當 setter 方法中的值。 例如：  
  
    ```java
    datasource.setServerName(value)  
    datasource.setDatabaseName(value)  
    ```  
  
## <a name="remarks"></a>備註

屬性名稱需區分大小寫，而重複的屬性名稱將以下列順序解析：  
  
1. API 引數 (例如使用者及密碼)
2. 屬性集合。  
3. 連接字串內的最後一個執行個體。
  
此外，屬性名稱允許未知的值，且 JDBC 驅動程式並不會驗證屬性值的大小寫。

容許同義字並會依序解析，如同是重複的屬性名稱一般。

下表列出 JDBC 驅動程式目前所有可用的連接字串屬性。

| 屬性<br/>類型<br/>預設 | Description |
| :------------------------------ | :---------- |
| accessToken<br/><br/>String<br/><br/>null | 使用此屬性可使用存取權杖來連接到 SQL 資料庫。 無法使用連接 URL 來設定**accessToken** 。 |
| applicationIntent<br/><br/>String<br/><br/>ReadWrite | 宣告連接到伺服器時的應用程式工作負載類型。 <br/><br/>可能的值為 **ReadOnly** 和 **ReadWrite**。 <br/><br/>如需詳細資訊，請參閱 [JDBC Driver 對於高可用性、災害復原的支援](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)。 |
| applicationName<br/><br/>String<br/>[&lt;=128 char]<br/><br/>null | 應用程式名稱，如果未提供名稱，則為 "[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]"。<br/><br/>用以識別各種 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分析與記錄工具中的特定應用程式。 |
| 驗證 (authentication)<br/><br/>String<br/><br/>NotSpecified | 從 Microsoft JDBC Driver 6.0 for SQL Server 開始, 此選擇性屬性會指出要用於連接的 SQL 驗證方法。 可能的值為**ActiveDirectoryIntegrated**、 **ActiveDirectoryPassword**、 **ActiveDirectoryMSI**、 **SqlPassword**和預設**NotSpecified**。<br/><br/> 使用**ActiveDirectoryIntegrated**連接到使用整合式 Windows 驗證的 SQL Database。<br/><br/> 使用**ActiveDirectoryPassword**連接到使用 Azure AD 主體名稱和密碼的 SQL Database。<br/><br/> 使用**ActiveDirectoryMSI**從 azure 資源內部 (例如 Azure 虛擬機器、App Service 或使用受控服務識別 (MSI) 驗證的函數應用程式) 連線到 SQL Database。 <br><br>使用**ActiveDirectoryMSI**驗證模式時, 驅動程式所支援的兩種受控識別類型如下: <br> 1._系統指派的受控識別_: 預設會用來取得**accessToken** 。 <br> 2._使用者指派的受控識別_: 如果受控服務識別 (MSI) 的用戶端識別碼是以**msiClientId**連接屬性指定, 則用來取得**accessToken** 。<br/><br/> 使用**SqlPassword**連接到使用**使用者** **名稱**/和**密碼**屬性的 SQL Server。<br/><br/> 如果不需要這些驗證方法, 請使用**NotSpecified** 。<br/><br/> **重要事項:** 如果驗證設定為 ActiveDirectoryIntegrated, 則必須安裝下列兩個程式庫: **SQLJDBC_AUTH。DLL** (JDBC 驅動程式套件中提供) 和 SQL Server 的 Azure Active Directory Authentication 程式庫 (**adalsql.dll)。DLL**), 它是以不同的語言 (x86 和 amd64) 提供, 適用于[Microsoft Active Directory 驗證程式庫 Microsoft SQL Server](https://www.microsoft.com/download/details.aspx?id=48742)的下載中心。 JDBC 驅動程式只支援 ADALSQL.DLL 的 version **1.0.2028.318 和更高**版本。URLMON.DLL.<br/><br/> **注意:** 當 [驗證] 屬性設定為 [ **NotSpecified**] 以外的任何值時, 驅動程式預設會使用安全通訊端層 (SSL) 加密。<br/><br/> 如需如何設定 Azure Active Directory 驗證的相關資訊, 請造訪[使用 Azure Active Directory authentication 連線到 SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)。 |
| authenticationScheme<br/><br/>String<br/><br/>NativeAuthentication | 表示您希望應用程式使用的整合式安全性種類。 可能的值為**JAVAKerberos**和預設**NativeAuthentication**。<br/><br/> 使用**authenticationScheme = JAVAKerberos**時, 您必須在**serverName**或**serverSpn**屬性中指定完整功能變數名稱 (FQDN)。 否則，會發生錯誤 (Kerberos 資料庫中找不到伺服器)。<br/><br/> 如需有關使用 **authenticationScheme** 的詳細資訊，請參閱[使用 Kerberos 整合式驗證連線到 SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md) \(機器翻譯\)。 |
| cancelQueryTimeout<br/><br/>INT<br/><br/>-1 | 從 Microsoft JDBC Driver 6.4 for SQL Server 開始, 此屬性可用來取消在連接上設定的**queryTimeout** 。 如果 SQL Server 的 TCP 連線以無訊息方式卸載, 則查詢執行會停止回應, 且不會擲回例外狀況。 只有在連接上也設定了 ' queryTimeout ' 時, 此屬性才適用。 <br/><br/>驅動程式會等候總**cancelQueryTimeout**  +  **queryTimeout**秒數, 以捨棄連線並關閉通道。 <br/><br/>此屬性的預設值為-1, 而行為是無限期等候。 |
| columnEncryptionSetting<br/><br/>String<br/>["Enabled" &#124; "Disabled"]<br/><br/>已停用 | 自 Microsoft JDBC Driver 6.0 for SQL Server 起，設為 "Enabled" 會使用 Always Encrypted (AE) 功能。 如有啟用 AE，JDBC 驅動程式會透明加密及解密儲存在 SQL Server 中經過加密之資料庫資料行中的敏感性資料。<br/><br/> 如需**columnEncryptionSetting**的詳細資訊, 請參閱[使用 JDBC 驅動程式的 Always Encrypted](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md) , 以取得詳細資料。<br/><br/> **注意:** Always Encrypted 適用于 SQL Server 2016 或更新版本。 |
| databaseName,<br/>資料庫<br/><br/>String<br/>[&lt;=128 char]<br/><br/>null | 要連接的資料庫名稱。 <br/><br/>如果沒有指定，將連接到預設資料庫。 |
| disableStatementPooling<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>true | 表示是否應該使用語句共用的旗標。 |
| enablePrepareOnFirst...<br/>PreparedStatementCall<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>false | _enablePrepareOnFirstPreparedStatementCall_<br/><br/> 設定為 "true" 以啟用準備的語句控制碼建立, <code>sp_prepexec</code>方法是在第一次執行備妥的語句時呼叫。 <br/><br/>設定為 "false", 將第一次執行備妥的語句變更<code>sp_executesql</code>為呼叫, 而不准備語句, 一旦第二次執行之後<code>sp_prepexec</code> , 就會呼叫來設定備妥的語句控制碼。 |
| encrypt<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>false | 如果伺服器有安裝憑證，設定為 "true" 以指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將安全通訊端層 (SSL) 加密用於用戶端與伺服器之間傳送的所有資料。 預設值為 "false"。<br/><br/> 從 Microsoft JDBC Driver 6.0 for SQL Server 開始, 預設會使用 SSL 加密的新連線設定「驗證」。 <br/><br/>如需詳細資訊，請參閱 'authentication' 屬性。 |
| failoverPartner<br/><br/>String<br/><br/>null | 用於資料庫鏡像組態的容錯移轉伺服器名稱。 初始連接到主體伺服器若失敗，將使用此屬性；在建立初始連接之後，將忽略此屬性。 必須與 databaseName 屬性一起使用。<br/><br/> **注意：** 此驅動程式不支援在連接字串中指定容錯移轉夥伴執行個體的伺服器執行個體連接埠號碼作為 failoverPartner 屬性的一部分。 不過，它支援在相同的連接字串中指定主體伺服器執行個體的 serverName、instanceName 和 portNumber 屬性以及容錯移轉夥伴執行個體的 failoverPartner 屬性。<br/><br/> 如果您在 **Server** 連線屬性中指定虛擬網路名稱，則不能使用資料庫鏡像。 如需詳細資訊，請參閱 [JDBC Driver 對於高可用性、災害復原的支援](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md) |
| fips<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>"false" | 針對啟用 FIPS 的 JVM, 此屬性應為**true**。 |
| fipsProvider<br/><br/>String<br/><br/>null | 在 JVM 中設定的 FIPS 提供者。 例如, BCFIPS 或 SunPKCS11-NSS。 已在版本6.4.0 版中移除-請參閱[這裡](https://github.com/Microsoft/mssql-jdbc/pull/460)的詳細資料。 |
| gsscredential<br/><br/>org.ietf.jgss.GSSCredential<br/><br/>null | 從 Microsoft JDBC Driver 6.2 for SQL Server 開始, 可以在此屬性中傳遞用於 Kerberos 限制委派的使用者認證。 <br/><br/>這應該與**integratedSecurity**為**true**和**JAVAKerberos** **authenticationscheme**搭配使用。 |
| hostNameInCertificate<br/><br/>String<br/><br/>null | 用於驗證 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSL 憑證的主機名稱。<br/><br/> 如果未指定 hostNameInCertificate 屬性或設定為 null，[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 將會在連線 URL 上使用 **serverName** 屬性值，當作驗證 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSL 憑證的主機名稱。<br/><br/> **注意:** 這個屬性會與**加密**/**驗證**屬性和**trustServerCertificate**屬性搭配使用。 只有在連接使用安全通訊端層 (SSL) 加密, 而且**trustServerCertificate**設定為 "false" 時, 這個屬性才會影響憑證驗證。 確定傳遞給 **hostNameInCertificate** 的值符合伺服器憑證中主體替代名稱 (SAN) 內的一般名稱 (CN) 或 DNS 名稱，SSL 連線才會成功。 如需詳細資訊, 請參閱[瞭解 SSL 支援](../../connect/jdbc/understanding-ssl-support.md)。 |
| INSTANCENAME<br/><br/>String<br/>[&lt;=128 char]<br/><br/>null | 要連線的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。 如果未指定，將會連接到預設執行個體。 如果已指定 instanceName 與通訊埠，請參閱通訊埠的注意事項。<br/><br/> 如果您在 **Server** 連線屬性中指定虛擬網路名稱，則不能使用 **instanceName** 連線屬性。 請參閱 [JDBC Driver 對於高可用性、災害復原的支援](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)，以取得詳細資訊。 |
| integratedSecurity<br/><br/>boolean<br/>["true"&#124;"false"]<br/><br/>false | 設定為 "true", 表示 windows 作業系統[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上使用 windows 認證。 若為 "true"，JDBC 驅動程式會搜尋本機電腦認證快取，以取得電腦上已提供的認證或網路登入。<br/><br/> 設定為 "true" (使用**authenticationscheme = JAVAKerberos**), 表示使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Kerberos 認證。 如需有關 Kerberos 驗證的詳細資訊，請參閱[使用 Kerberos 整合式驗證來連線到 SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md) \(機器翻譯\)。 <br/><br/> 若為 "false"，必須提供使用者名稱及密碼。 |
| jaasConfigurationName<br/><br/>String<br/><br/>SQLJDBCDriver | 從 Microsoft JDBC Driver 6.2 for SQL Server 開始, SQL Server 的每個連接都可以有自己的 JAAS 登入設定檔來建立 Kerberos 連線。 可以透過這個屬性傳遞登入設定檔的名稱。 <br/> 根據預設, [IBM jvm `useDefaultCcache = true` ] 的 [驅動程式`useTicketCache = true` ] 屬性和 [其他 jvm]。 |
| keyStoreAuthentication<br/><br/>String<br/><br/>null | 從 Microsoft JDBC Driver 6.0 for SQL Server 開始, 此屬性會識別哪一個金鑰存放區可順暢設定以與 Always Encrypted 連接, 並決定用來驗證金鑰存放區的驗證機制。 適用于 SQL Server 的 Microsoft JDBC Driver 6.0 支援使用您需要設定 "**keyStoreAuthentication = JAVAKeyStorePassword**" 的這個屬性, 順暢地設定 JAVA 金鑰存放區。 請注意, 若要使用此屬性, 您也需要設定 JAVA 金鑰存放區的**keyStoreLocation**和**keyStoreSecret**屬性。 <br/><br/>如需詳細資訊，請瀏覽[搭配 JDBC 驅動程式使用 Always Encrypted](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)。 |
| keyStoreLocation<br/><br/>String<br/><br/>null | 當**keyStoreAuthentication = JAVAKeyStorePassword**時, **keyStoreLocation**屬性會識別 JAVA 金鑰儲存區檔案的路徑, 該檔案會存放要與 Always Encrypted 資料搭配使用的資料行主要金鑰。 請注意, 此路徑必須包含金鑰儲存區檔案名。<br/><br/>如需詳細資訊，請瀏覽[搭配 JDBC 驅動程式使用 Always Encrypted](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)。 |
| keyStoreSecret<br/><br/>String<br/><br/>null | 當**keyStoreAuthentication = JAVAKeyStorePassword**時, **keyStoreSecret**屬性會識別用於金鑰存放區以及金鑰的密碼。 請注意, 若要使用 JAVA 金鑰存放區, 則金鑰儲存區和金鑰密碼必須相同。<br/><br/>如需詳細資訊，請瀏覽[搭配 JDBC 驅動程式使用 Always Encrypted](https://msdn.microsoft.com/library/mt591987%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396)。 |
| lastUpdateCount<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>true | "true" 值只會從傳至伺服器的 SQL 陳述式傳回上次更新計數，而且它可以用在單一 SELECT、INSERT 或 DELETE 陳述式，以忽略伺服器觸發程序所導致的其他更新計數。 將此屬性設為 "false" 會導致傳回所有更新計數，包括伺服器觸發程序所傳回的更新計數。<br/><br/> **注意：** 此屬性僅適用於搭配 [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) 方法使用時。 所有其他 execute 方法都會傳回所有結果並更新計數。 這個屬性只會影響伺服器觸發程序所傳回的更新計數。 它不會影響結果集或觸發程序執行期間產生的錯誤。 |
| lockTimeout<br/><br/>INT<br/><br/>-1 | 等候資料庫報告鎖定逾時的毫秒數。預設的行為是無限期等待。 如果已指定，則此值為連接上所有陳述式的預設值。 請注意, **setQueryTimeout ()** 可以用來設定特定語句的超時時間。 此值可以為 0，表示不等待。 |
| loginTimeout<br/><br/>INT<br/>[0..65535]<br/><br/>15 | 驅動程式應等待失敗連接逾時的秒數。 值為零表示此逾時為預設系統逾時，預設指定為 15 秒。 非零值為驅動程式應等待失敗連接之逾時的秒數。<br/><br/> 如果您在 **Server** 連線屬性中指定虛擬網路名稱，您應該指定三分鐘或更長的逾時值，好讓容錯移轉連線有充足的時間可以順利完成。 請參閱 [JDBC Driver 對於高可用性、災害復原的支援](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)，以取得詳細資訊。 |
| msiClientId<br/><br/>String<br/><br/>null | 建立具有**ActiveDirectoryMSI**驗證模式的連接時, 用來取得**accessToken**之受控服務識別 (MSI) 的用戶端識別碼。|
| multiSubnetFailover<br/><br/>布林<br/><br/>false | 在連線到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可用性群組的可用性群組接聽程式或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 容錯移轉叢集執行個體時，一律指定 **multiSubnetFailover=true**。 **multiSubnetFailover=true** 會設定 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]，以提供對 (目前) 使用中伺服器更快速的偵測與連線。 可能的值為 true 和 false。 請參閱 [JDBC Driver 對於高可用性、災害復原的支援](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)，以取得詳細資訊。<br/><br/> 您可以透過程式設計方式，使用 [getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)、[getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md) 及 [setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md) 存取 **multiSubnetFailover** 連線屬性。<br/><br/> **注意:** 從 Microsoft JDBC Driver 6.0 for SQL Server 開始, 在連接到可用性群組接聽程式時, 不再需要將**multiSubnetFailover**設定為 "true"。 預設會啟用新的屬性**transparentNetworkIPResolution**, 它會提供對 (目前) 使用中伺服器的偵測和連接。 |
| packetSize<br/><br/>INT<br/>[-1 &#124; 0 &#124; 512..32767]<br/><br/>8000 | 用來與 SQL Server 通訊的網路封包大小 (以位元組指定)。 -1 這個值表示使用伺服器的預設封包大小。 0 這個值表示使用最大值，也就是 32767。 如果將此屬性設定為可接受範圍以外的值，則會發生例外狀況。<br/><br/> **重要事項：** 啟用加密 (encrypt=true) 時，不建議使用 packetSize 屬性。 否則，驅動程式可能會引發連接錯誤。 如需詳細資訊，請參閱 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) 類別的 [setPacketSize](../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md) 方法。 |
| 密碼<br/><br/>String<br/>[&lt;=128 char]<br/><br/>null | 資料庫密碼, 如果與 SQL 使用者和密碼連接, 則為。<br/>針對具有主體名稱和密碼的 Kerberos 連線, 此屬性會設定為 [Kerberos 主體密碼]。 |
| portNumber,<br/>port<br/><br/>INT<br/>[0..65535]<br/><br/>1433 | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在接聽的連接埠。 如果已在連接字串中指定連接埠號碼，就不需要對 SQLbrowser 進行要求。 同時指定 port 和 instanceName 時，會連接至指定的通訊埠。 然而，系統會驗證 **instanceName**，如果它不符合連接埠，則會發生錯誤。<br/><br/> **重要事項：** 建議您一定要指定連接埠號碼，因為這比使用 SQLbrowser 更安全。 |
| queryTimeout<br/><br/>INT<br/><br/>-1 | 查詢上發生超時前要等候的秒數。 預設值為-1, 表示無限的時間。 將此值設定為0也表示無限期等候。 |
| responseBuffering<br/><br/>String<br/>["full" &#124; "adaptive"]<br/><br/>adaptive | 如果此屬性設定為 "adaptive"，就會在必要時緩衝處理可能的資料下限。 預設模式為 "adaptive"。<br/><br/> 如果此屬性設定為 "full"，執行陳述式時，就會從伺服器讀取整個結果集。<br/><br/> **注意：** 在將 JDBC 驅動程式從 1.2 版升級之後，預設的緩衝行為將成為 "adaptive"。 若您的應用程式永遠不會需要設定 "responseBuffering" 屬性，所以您想要在應用程式中繼續保留 1.2 版的預設行為，您必須在連接字串中或使用 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) 物件的 [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) 方法將 responseBufferring 屬性設為 "full"。 |
| selectMethod<br/><br/>String<br/>["direct" &#124; "cursor"]<br/><br/>直接 | 如果將此屬性設定為 "cursor"，便會為在 **TYPE_FORWARD_ONLY** 及 **CONCUR_READ_ONLY** 資料指標之連線上建立的每個查詢，建立資料庫資料指標。 通常只有當應用程式所產生的結果集過於龐大而用戶端記憶體無法全數包含時，才需要此屬性。 此屬性設定為 "cursor" 時，用戶端記憶體中只會保留有限數量的結果集資料列。 <br/><br/>預設的行為是用戶端記憶體中保留了所有結果集資料列。 當應用程式處理所有資料列時，此行為提供最快的效能。 |
| sendStringParameters...<br/>AsUnicode<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>true | *sendStringParametersAsUnicode*<br/><br/>如果 **sendStringParametersAsUnicode** 屬性設定為 "true"，String 參數就會以 Unicode 格式傳送至伺服器。<br/><br/> 如果 **sendStringParametersAsUnicode** 屬性設定為 "false"，String 參數就會以非 Unicode 格式 (例如 ASCII/MBCS) 而非 Unicode 傳送至伺服器。<br/><br/> **sendStringParametersAsUnicode** 屬性的預設值為 "true"。<br/><br/> **請注意：** 只有在傳送具有 **CHAR**、**VARCHAR** 或 **LONGVARCHAR** JDBC 類型的參數值時，才會檢查 **sendStringParametersAsUnicode** 屬性。 新的 JDBC 4.0 國際字元方法 (例如 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 和 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) 類別的 setNString、setNCharacterStream 及 setNClob methods方法) 無論此屬性的設定為何，一律會以 Unicode 將其參數值傳送到伺服器。<br/><br/> 若要讓 **CHAR**、**VARCHAR** 和 **LONGVARCHAR** JDBC 資料類型達到最佳效能，應用程式應該將 **sendStringParametersAsUnicode** 屬性設定為 "false"，並且使用 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 和 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) 類別的 setString、setCharacterStream 及 setClob 非國家字元方法。<br/><br/> 當應用程式將 **sendStringParametersAsUnicode** 屬性設定為 "false" 並且使用非國家字元方法來存取伺服器端的 Unicode 資料類型 (例如 **nchar**、**nvarchar** 和 **ntext**) 時，如果資料庫定序不支援非國家字元方法所傳遞之 String 參數中的字元，某些資料可能會遺失。<br/><br/> 請注意, 應用程式應該使用[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)和[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)類別的 SetNString、setNCharacterStream 和 setNClob 國家字元方法, 來取得**NCHAR**、 **NVARCHAR**、和會**LONGNVARCHAR** JDBC 資料類型。 |
| sendTimeAsDatetime<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>true | 這個屬性是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC Driver 3.0 中所新增。<br/><br/> 設定為 "true", 將 sql. Time 值傳送至伺服器做為[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**值。 <br/>設定為 "false", 將時間值傳送至伺服器做為[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **時間**值。<br/><br/> 這個屬性的預設值目前為 "true", 未來的版本可能會變更。<br/><br/> 如需如何在將 java [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] .sql 值傳送至伺服器之前設定的詳細資訊, 請參閱設定[如何將 java. time 值傳送至伺服器](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)。 |
| serverName,<br/>伺服器<br/><br/>String<br/><br/>null | 執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦。<br/><br/> 您也可以指定 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] 可用性群組的虛擬網路名稱。 請參閱 [JDBC Driver 對於高可用性、災害復原的支援](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)，以取得詳細資訊。 |
| serverNameAsACE<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>false | 自 SQL Server 的 Microsoft JDBC 驅動程式 6.0 起，設為 "true" 表示驅動程式應將連接中的 Unicode 伺服器名稱轉譯成 ASCII 相容的 Unicode 編碼 (Punycode)。 若此設定為 false，驅動程式會使用使用者所提供的伺服器名稱進行連接。<br/><br/> 如需詳細資訊, 請參閱[JDBC Driver 的國際功能](../../connect/jdbc/international-features-of-the-jdbc-driver.md)。 |
| serverPreparedStatement...<br/>DiscardThreshold<br/><br/>Integer<br/><br/>10 | *serverPreparedStatementDiscardThreshold*<br/><br/>從適用于 SQL Server 的 JDBC Driver 6.2 開始, 這個屬性可用來控制在執行清除伺服器上未完成句<code>sp_unprepare</code>柄的呼叫之前, 每個連接的未完成準備語句捨棄動作 (). <br/><br/> 如果此屬性設定為&lt;= 1, 則會在備妥的語句關閉時立即執行 unprepare 動作。 如果設定為&gt;1, 則會將這些呼叫批次處理在一起, 以避免太常呼叫 sp_unprepare 的額外負荷。 |
| serverSpn<br/><br/>String<br/><br/>null | 從 Microsoft JDBC Driver 4.2 for SQL Server 開始，此選擇性屬性可以用來指定 Java Kerberos 連接的服務主體名稱 (SPN)。  它會與**authenticationScheme**搭配使用。<br/><br/> 若要指定 SPN，可以使用下列格式："MSSQLSvc/fqdn:port@REALM"，其中 fqdn 是完整網域名稱，port 是連接埠號碼，REALM 是以大寫字母表示的 SQL Server Kerberos 領域。<br/><br/> 注意：如果該用戶端的預設領域 (如 Kerberos 設定中所指定) 與 SQL Server 的 Kerberos 領域相同，則 @REALM 是選擇性項目。<br/><br/> 如需有關搭配使用**serverSpn**與 JAVA Kerberos 的詳細資訊, 請參閱[使用 Kerberos 整合式驗證連接到 SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)。 |
| statementPooling...<br/>CacheSize<br/><br/>INT<br/><br/>0 | *statementPoolingCacheSize*<br/><br/>從適用于 SQL Server 的 JDBC Driver 6.4 開始, 這個屬性可用來啟用驅動程式中已備妥的語句控制碼快取。 <br/><br/>這個屬性會定義語句集區的快取大小。 <br/><br/>這個屬性只能與應設定為 "false" 的**disableStatementPooling**連接屬性搭配使用。 將**disableStatementPooling**設定為 "true" 或**statementPoolingCacheSize**為0會停用備妥的語句控制碼快取。|
| socketTimeout<br/><br/>INT<br/><br/>0 | 在通訊端讀取或接受發生超時之前, 所要等待的毫秒數。 預設值為 0, 表示無限制的超時。 |
| sslProtocol<br/><br/>String<br/><br/>TLS | 從適用于 SQL Server 的 JDBC Driver 6.4 開始, 這個屬性可用來指定要在安全連線期間考慮的 TLS 通訊協定。 <br/>可能的值為：**TLS**、**TLSv1**、**TLSv1.1** 和 **TLSv1.2**。 <br/><br/>如需詳細資訊, 請參閱[SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol)。 |
| transparentNetwork...<br/>IPResolution<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>true | *transparentNetworkIPResolution*<br/><br/>從 Microsoft JDBC Driver 6.0 for SQL Server 開始, 此屬性可讓您更快速地偵測 (目前) 使用中的伺服器並連接到該服務。 可能的值為 "true" 和 "false", 其中 "true" 為預設值。<br/><br/> 在 Microsoft JDBC Driver 6.0 for SQL Server 之前, 應用程式必須將連接字串設定為包含 "multiSubnetFailover = true", 以指出它是連接到 AlwaysOn 可用性群組。 若未將**multiSubnetFailover** connection 關鍵字設定為 "true", 則應用程式在連接到 AlwaysOn 可用性群組時可能會遇到超時。 從 Microsoft JDBC Driver 6.0 for SQL Server 開始, 應用程式不需要再將 multiSubnetFailover 設定為 true。 <br/><br/>**注意:** 當 transparentNetworkIPResolution = true 時, 第一次連接嘗試會使用500毫秒做為超時。 任何後續的嘗試都會使用與 multiSubnetFailover 屬性所使用的相同超時邏輯。 |
| trustManagerClass<br/><br/>String<br/><br/>null | 自訂<code>javax.net.ssl.TrustManager</code>執行的完整類別名稱。 |
| trustManager ...<br/>ConstructorArg<br/><br/>String<br/><br/>null | *trustManagerConstructorArg*<br/><br/>要傳遞至 TrustManager 之函式的選擇性引數。 如果指定 trustManagerClass, 並要求加密的連線, 則會使用自訂 TrustManager, 而不是預設的系統 JVM 金鑰儲存區 TrustManager。 |
| trustServerCertificate<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>false | 設定為 "true" 以指定 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 將不會驗證 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSL 憑證。<br/><br/> 若為 "true"，當通訊層使用 SSL 加密時，會自動信任 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSL 憑證。<br/><br/> 如果為 "false", [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]則會驗證服務器 SSL 憑證。 如果伺服器憑證驗證失敗，驅動程式將引發錯誤，並中止連線。 預設值為 "false"。 確定傳遞給 **serverName** 的值完全符合伺服器憑證中主體替代名稱內的一般名稱 (CN) 或 DNS 名稱，SSL 連線才會成功。 如需詳細資訊, 請參閱[瞭解 SSL 支援](../../connect/jdbc/understanding-ssl-support.md)。<br/><br/> **注意:** 這個屬性會與**加密**/**驗證**屬性搭配使用。 只有在連接使用 SSL 加密時, 這個屬性才會影響伺服器 SSL 憑證驗證。 |
| trustStore<br/><br/>String<br/><br/>null | trustStore 憑證檔案的路徑 (包括檔案名稱)。 trustStore 檔案包含用戶端所信任之憑證的清單。<br/><br/> 未指定此屬性或將其設定為 null 時，驅動程式會依賴信任管理員 Factory 的查閱規則，決定要使用的憑證存放區。<br/><br/> **預設的 SunX509 TrustManagerFactory 會嘗試以下列的搜尋順序，找出信任的資料：**<br/><br/> 由 "javax.net.ssl.trustStore" Java Virtual Machine (JVM) 系統屬性所指定的檔案。<br/><br/> "&lt;java 主目錄&gt;/lib/security/jssecacerts" 檔案。<br/><br/> "&lt;java 主目錄&gt;/lib/security/cacerts" 檔案。<br/><br/> <br/><br/> 如需詳細資訊，請參閱 Sun Microsystems 網站上的 SUNX509 TrustManager 介面文件。<br/><br/> **注意:** 只有在連接使用 SSL 加密, 而且**trustServerCertificate**屬性設定為 "false" 時, 這個屬性才會影響憑證 trustStore 查閱。 |
| trustStorePassword<br/><br/>String<br/><br/>null | 用於檢查 trustStore 資料完整性的密碼。<br/><br/> 如果有設定 trustStore 屬性，但是未設定 trustStorePassword 屬性，就不會檢查 trustStore 的完整性。<br/><br/> 當 trustStore 和 trustStorePassword 屬性都未指定時，驅動程式會使用 JVM 系統屬性 "javax.net.ssl.trustStore" 和 "javax.net.ssl.trustStorePassword"。 如果未指定 "javax.net.ssl.trustStorePassword" 系統屬性，就不會檢查 trustStore 的完整性。<br/><br/> 如果未設定 trustStore 屬性，但是有設定 trustStorePassword 屬性，JDBC 驅動程式會使用 "javax.net.ssl.trustStore" 指定的檔案作為信任存放區，並使用指定的 trustStorePassword 來檢查信任存放區的完整性。 當用戶端應用程式不要在 JVM 系統屬性中儲存密碼時，可能需要這個動作。<br/><br/> **注意:** 只有在連接使用 SSL 連線, 而且**trustServerCertificate**屬性設定為 "false" 時, trustStorePassword 屬性才會影響憑證 trustStore 查閱。 |
| trustStoreType<br/><br/>String<br/><br/>JKS | 設定此屬性, 以指定要用於 FIPS 模式的信任存放區類型。 <br/><br/>可能的值為**PKCS12**或由 FIPS 提供者所定義的類型。 |
| useBulkCopyFor...<br/>BatchInsert<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>false | _useBulkCopyForBatchInsert_<br/><br/> 從適用于 SQL Server 的 Microsoft JDBC Driver 7.0 開始, 您可以在執行批次插入作業<code>java.sql.PreparedStatement</code>時, 啟用此連接屬性以使用大量複製 API 來改善效能。 <br/><br/>只有當目標伺服器的類型是**Azure 資料倉儲**時, 這項功能才會運作。 預設為停用, 若要啟用此功能, 請將此屬性設定為 "true"。 <br/></br> **重要注意事項:** 這項功能僅支援完全參數化的 INSERT 查詢。 如果插入查詢是由其他 SQL 查詢結合, 或包含值中的資料, 則執行會回到基本的批次插入作業。 <br/><br/> 如需如何使用此屬性的詳細資訊, 請參閱[使用大量複製 API 執行批次插入作業](use-bulk-copy-api-batch-insert-operation.md)|
| userName,<br/>user<br/><br/>String<br/>[&lt;=128 char]<br/><br/>null | 資料庫使用者 (如果與 SQL 使用者和密碼連接)。<br/><br/>針對具有主體名稱和密碼的 Kerberos 連線, 此屬性會設定為 Kerberos 主體名稱。 |
| workstationID<br/><br/>String<br/>[&lt;=128 char]<br/><br/>&lt;空字串&gt; | 工作站識別碼。 用以識別各種 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分析與記錄工具中的特定工作站。 <br/><br/>若未指定，將會使用 &lt;空字串&gt;。 |
| xopenStates<br/><br/>boolean<br/>["true" &#124; "false"]<br/><br/>false | 設定為 "true"，以指定驅動程式傳回例外狀況的 XOPEN 相容狀態碼。 <br/><br/>預設為傳回 SQL 99 狀態碼。 |
| &nbsp; | &nbsp; |

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 會針對連線屬性採用伺服器預設值，但是 ANSI_DEFAULTS 和 IMPLICIT_TRANSACTIONS 除外。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 會自動將 ANSI_DEFAULTS 設定為 ON，並將 IMPLICIT_TRANSACTIONS 設定為 OFF。

> [!Important]
> 如果驗證設定為 ActiveDirectoryPassword, 下列程式庫必須包含在 [類程式] 中: [azure-activedirectory-適用于 java 的程式庫](https://github.com/AzureAD/azure-activedirectory-library-for-java)。 它可以在 Maven 存放[庫](https://mvnrepository.com/artifact/com.microsoft.azure/adal4j)中找到。 若要下載程式庫及其相依性, 最簡單的方式是使用 Maven: 
> 1. 首先, 在您的系統上安裝 Maven 
> 2. 前往驅動程式的[GitHub 頁面](https://github.com/Microsoft/mssql-jdbc)
> 3. 下載 pom .xml 檔案
> 4. 執行下列 Maven 命令以下載程式庫和其相依性:`mvn dependency:copy-dependencies`

## <a name="see-also"></a>另請參閱

[使用 JDBC Driver 連接到 SQL Server](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
[FIPS 模式](../../connect/jdbc/fips-mode.md)
