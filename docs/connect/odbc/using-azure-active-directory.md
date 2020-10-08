---
title: 搭配 ODBC 驅動程式使用 Azure Active Directory
description: Microsoft ODBC Driver for SQL Server 可讓 ODBC 應用程式使用 Azure Active Directory，連線至 Azure SQL Database 的執行個體。
ms.custom: ''
ms.date: 09/01/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6925b2b79629fbcbe84f6577e2617e9b45ea82c
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727379"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>搭配 ODBC 驅動程式使用 Azure Active Directory
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>目的

Microsoft ODBC Driver for SQL Server 13.1 版或更新版本可讓 ODBC 應用程式在 Azure Active Directory 中，搭配使用者名稱/密碼、Azure Active Directory 存取權杖、Azure Active Directory 受控識別 (17.3+)，或是 Windows 整合式驗證 (在 Linux/macOS 上為 17.6+)，使用同盟識別身分來連線到 Azure SQL Database 的執行個體。 針對 ODBC Driver 13.1 版，Azure Active Directory 存取權杖驗證僅限 _Windows_。 ODBC Driver 17 版和更新版本支援跨所有平台 (Windows、Linux 及 macOS) 進行此驗證。 具有登入識別碼的新 Azure Active Directory 互動式驗證是在適用於 Windows 的 ODBC Driver 17.1 版中引進的。 在 ODBC 驅動程式 17.3.1.1 版中，已針對系統指派與使用者指派的身分識別，新增新的 Azure Active Directory 受控識別驗證方法。 所有這些驗證方法都是透過使用新的 DSN 和連接字串關鍵字，以及連線屬性來完成。

> [!NOTE]
> Linux 與 macOS 上早於 17.6 版的 ODBC 驅動程式只支援直接針對 Azure Active Directory 進行 Azure Active Directory 驗證。 如果在 Linux 或 macOS 用戶端使用 Azure Active Directory 使用者名稱/密碼，而您的 Active Directory 組態需要用戶端驗證 Active Directory 同盟服務端點，則驗證可能會失敗。 從 17.6 版的驅動程式起，已移除這個限制。

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>新的和/或已修改的 DSN 與連接字串關鍵字

使用 DSN 或連接字串連線以控制驗證模式時，可以使用 `Authentication` 關鍵字。 連接字串中設定的值會覆寫 DSN 中設定的值 (如已提供)。 `Authentication` 設定的「前置屬性值」  是從連接字串和 DSN 值計算而來的值。

|名稱|值|預設|描述|
|-|-|-|-|
|`Authentication`|(未設定)、(空字串)、`SqlPassword`、`ActiveDirectoryPassword`、`ActiveDirectoryIntegrated`、`ActiveDirectoryInteractive`、`ActiveDirectoryMsi` |(未設定)|控制驗證模式。<table><tr><th>值<th>描述<tr><td>(未設定)<td>由其他關鍵字決定的驗證模式 (現有的舊版連線選項)。<tr><td>(空字串)<td>(僅限連接字串)。覆寫和取消設定在 DSN 中設定的 `Authentication` 值。<tr><td>`SqlPassword`<td>利用使用者名稱與密碼直接向 SQL Server 執行個體進行驗證。<tr><td>`ActiveDirectoryPassword`<td>利用使用者名稱與密碼，以 Azure Active Directory 身分識別進行驗證。<tr><td>`ActiveDirectoryIntegrated`<td>僅限 Windows 與 Linux/Mac 17.6+ 驅動程式。 使用整合式驗證，以 Azure Active Directory 身分識別進行驗證。<tr><td>`ActiveDirectoryInteractive`<td>「僅限 Windows 驅動程式」  。 使用互動式驗證，以 Azure Active Directory 身分識別進行驗證。<tr><td>`ActiveDirectoryMsi`<td>使用受控識別驗證，以 Azure Active Directory 身分識別進行驗證。 針對使用者指派的識別，UID 設成使用者身分識別的物件識別碼。</table>|
|`Encrypt`|(未設定)、`Yes`、`No`|(請參閱描述)|控制連接的加密。 如果 `Authentication` 設定的前置屬性值在 DSN 或連接字串中不是 _none_，則預設值為 `Yes`。 否則預設為 `No`。 如果屬性 `SQL_COPT_SS_AUTHENTICATION` 會覆寫 `Authentication` 的前置屬性值，請在 DSN、連接字串或連線屬性中明確設定 Encryption 的值。 如果在 DSN 或連接字串中將值設定為 `Yes`，則 Encryption 的前置屬性值為 `Yes`。|

## <a name="new-andor-modified-connection-attributes"></a>新的和/或已修改的連線屬性

下列預先連線的連線屬性已引進或修改來支援 Azure Active Directory 驗證。 當連線屬性具有對應的連接字串或 DSN 關鍵字且已設定時，連線屬性就會取得高優先順序。

|屬性|類型|值|預設|描述|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_AD_MSI`, `SQL_AU_RESET`|(未設定)|請參閱上方的 `Authentication` 關鍵字描述。 提供 `SQL_AU_NONE` 以便明確覆寫 DSN 和/或連接字串中設定的 `Authentication` 值，而 `SQL_AU_RESET` 會取消設定該屬性 (如已設定)，讓 DSN 或連接字串值能夠取得高優先順序。|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|指向 `ACCESSTOKEN` 的指標或 NULL|NULL|如果不是 Null，請指定要使用的 AzureAD 存取權杖。 指定存取權杖，並同時指定 `UID`、`PWD`、`Trusted_Connection` 或 `Authentication` 連接字串關鍵字或其對等屬性，是錯誤的。 <br> **注意：** ODBC Driver 13.1 版僅在 _Windows_ 上支援此項。|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(請參閱描述)|控制連接的加密。 `SQL_EN_OFF` 和 `SQL_EN_ON` 會分別停用和啟用加密。 如果 `Authentication` 設定的前置屬性值不是 _none_ 或已設定 `SQL_COPT_SS_ACCESS_TOKEN`，而且未在 DSN 或連接字串中指定 `Encrypt`，則預設值為 `SQL_EN_ON`。 否則預設為 `SQL_EN_OFF`。 如果已將 `SQL_COPT_SS_AUTHENTICATION` 連線屬性設定為不是 _none_，若尚未在 DSN 或連接字串中指定 `Encrypt`，請明確地將 `SQL_COPT_SS_ENCRYPT` 設定為所需的值。 這個屬性的有效值會控制[是否將針對連線使用加密](../../relational-databases/native-client/features/using-encryption-without-validation.md) \(部分機器翻譯\)。|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Azure Active Directory 不支援，因為對 Azure AD 主體進行的密碼變更無法透過 ODBC 連線來完成。 <br><br>SQL Server 驗證的密碼逾期已在 SQL Server 2005 中推出。 已新增 `SQL_COPT_SS_OLDPWD` 屬性，讓用戶端能夠同時提供舊的和新的密碼進行連線。 設定這個屬性之後，提供者將不會針對第一次連線或後續連線使用連接集區，因為連接字串將會包含現已變更的「舊密碼」。|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|「已淘汰」  ；請改用設定為 `SQL_AU_AD_INTEGRATED` 的 `SQL_COPT_SS_AUTHENTICATION`。 <br><br>針對伺服器登入的存取驗證強制使用 Windows 驗證 (Linux 和 macOS 上的 Kerberos)。 使用 Windows 驗證時，驅動程式會忽略在 `SQLConnect`、`SQLDriverConnect` 或 `SQLBrowseConnect` 處理期間所提供的使用者識別碼和密碼值。|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Azure Active Directory 的 UI 新增項目 (僅限 Windows 驅動程式)

驅動程式的 DSN 設定和連線 UI 已利用搭配 Azure AD 使用驗證所需的其他選項來增強。

### <a name="creating-and-editing-dsns-in-the-ui"></a>在 UI 中建立和編輯 DSN

使用驅動程式的設定 UI 來建立或編輯現有的 DSN 時，可以使用新的 Azure AD 驗證選項：

`Authentication=ActiveDirectoryIntegrated`，適用於對 Azure SQL Database 進行 Azure Active Directory 整合式驗證

![DSN 建立及編輯畫面，其中已選取 Azure Active Directory 整合式驗證。](windows/create-dsn-ad-integrated.png)

`Authentication=ActiveDirectoryPassword`，適用於對 Azure SQL Database 進行 Azure Active Directory 使用者名稱/密碼驗證

![DSN 建立及編輯畫面，其中已選取 Azure Active Directory 密碼驗證。](windows/create-dsn-ad-password.png)

`Authentication=ActiveDirectoryInteractive`，適用於對 Azure SQL Database 進行 Azure Active Directory 互動式驗證

![DSN 建立及編輯畫面，其中已選取 Azure Active Directory 互動式驗證。](windows/create-dsn-ad-interactive.png)

`Authentication=SqlPassword` 表示對 SQL Server (Azure 或其他) 進行使用者名稱/密碼驗證

![DSN 建立及編輯畫面，其中已選取 SQL Server 驗證。](windows/create-dsn-ad-sql-server.png)

`Trusted_Connection=Yes` 表示 Windows 舊版 SSPI 整合式驗證

![DSN 建立及編輯畫面，其中已選取整合式 Windows 驗證。](windows/create-dsn-win-sspi.png)

`Authentication=ActiveDirectoryMsi`，適用於 Azure Active Directory 受控識別驗證

![DSN 建立及編輯畫面，其中已選取受控服務識別驗證。](windows/create-dsn-ad-msi.png)

這六個選項分別對應至 `Trusted_Connection=Yes` (現有僅限舊版 Windows SSPI 的整合式驗證) 與 `Authentication=` `ActiveDirectoryIntegrated`、`SqlPassword`、`ActiveDirectoryPassword`、`ActiveDirectoryInteractive` 與 `ActiveDirectoryMsi`。

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect 提示 (僅限 Windows 驅動程式)

當 SQLDriverConnect 要求完成連線所需之資訊時顯示的提示對話方塊，其中包含四個適用於 Azure AD 驗證的新選項：

![由 SQLDriverConnect 所顯示的 [SQL Server 登入] 對話方塊。](windows/server-login.png)

這些選項對應至上述 DSN 設定 UI 中相同的六個可用選項。

### <a name="example-connection-strings"></a>範例連接字串
1. SQL Server 驗證：舊版語法。 伺服器憑證不會經過驗證，而且只有在伺服器強制進行加密時，才會使用加密。 使用者名稱/密碼會在連接字串中傳遞。
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. SQL 驗證：新語法。 用戶端會要求加密 (`Encrypt` 的預設值是 `true`)，而且不論加密設定為何 (除非將 `TrustServerCertificate` 設定為 `true`)，都會驗證伺服器憑證。 使用者名稱/密碼會在連接字串中傳遞。
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. (向 SQL Server 或 SQL IaaS) 使用 SSPI 的整合式 Windows 驗證 (Linux 和 macOS 上的 Kerberos)：目前的語法。 除非使用加密，否則不會驗證伺服器憑證。 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (「僅限 Windows 驅動程式」  )。使用 SSPI 的整合式 Windows 驗證 (如果目標資料庫位於 SQL Server 或 SQL IaaS)：新語法。 用戶端會要求加密 (`Encrypt` 的預設值是 `true`)，而且不論加密設定為何 (除非將 `TrustServerCertificate` 設定為 `true`)，都會驗證伺服器憑證。 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Azure Active Directory 使用者名稱/密碼驗證 (如果目標資料庫位於 Azure SQL Database)。 無論加密設定為何，都會驗證伺服器憑證 (除非將 `TrustServerCertificate` 設定為 `true`)。 使用者名稱/密碼會在連接字串中傳遞。 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (「僅限 Windows 與 Linux/macOS 17.6+ 驅動程式」。)使用 ADAL 或 Kerberos 的整合式 Windows 驗證，其需要針對 Azure AD 發行的存取權杖兌換 Windows 帳戶認證 (假設目標資料庫位於 Azure SQL Database)。 無論加密設定為何，都會驗證伺服器憑證 (除非將 `TrustServerCertificate` 設定為 `true`)。 在 Linux/macOS 上，需要有適合的 Kerberos 票證可供使用；請參閱下面關於同盟帳戶的小節，以及[使用整合式驗證](linux-mac/using-integrated-authentication.md)以取得詳細資訊。
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (「僅限 Windows 驅動程式」)。Azure AD 互動式驗證會使用 Azure Multi-Factor Authentication 技術來設定連線。 在此模式中，藉由提供登入識別碼來觸發 Azure 驗證對話方塊，並允許使用者輸入密碼以完成連線。 使用者名稱會在連接字串中傳遞。
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![使用 Active Directory 互動式驗證時的 Windows Azure 驗證 UI。](windows/WindowsAzureAuth.png)

8. Azure Active Directory 受控識別驗證會使用系統指派或使用者指派的身分識別進行驗證以設定連線。 針對使用者指派的識別，UID 設成使用者身分識別的物件識別碼。<br>
針對系統指派的身分識別，<br>
`server=Server;database=Database;Authentication=ActiveDirectoryMsi;`<br>
對於物件識別碼等於 myObjectId 之使用者指派的身分識別，<br>
`server=Server;database=Database;UID=myObjectId;Authentication=ActiveDirectoryMsi;`

> [!NOTE]
>- 搭配 17.4.2 版***以前***的 Windows ODBC 驅動程式使用新的 Active Directory 選項時，確認已安裝 [SQL Server 的 Active Directory 驗證程式庫](https://go.microsoft.com/fwlink/?LinkID=513072)。 使用 Linux 和 macOS 驅動程式時，確認已安裝 `libcurl`。 對於驅動程式 17.2 版和更新版本，這不是明確的相依性，因其不是其他驗證方法或 ODBC 作業的必要項。
>- 當 Azure Active Directory 設定包含條件式存取原則，且用戶端為 Windows 10 或 Server 2016 或更新版本時，透過整合式或使用者名稱/密碼進行的驗證可能會失敗。 條件式存取原則要求使用 Windows 帳戶管理員 (WAM)，其由適用於 Windows 的驅動程式 17.6 版或更新版本所支援。 若要使用 WAM，請分別在 `HKLM\Software\ODBC\ODBCINST.INI\ODBC Driver 17 for SQL Server`、`HKCU\Software\ODBC\ODBC.INI\<your-user-DSN-name>` 或 `HKLM\Software\ODBC\ODBC.INI\<your-system-DSN-name>` 中針對全域、使用者 DSN 或系統 DSN 範圍的設定建立名為 `ADALuseWAM` 的新字串或 DWORD 值，並將其設定為 1 的值。 請注意，使用 WAM 進行驗證並不支援使用 `runas` 以不同的使用者身分執行應用程式。 Linux 或 macOS 並不支援需要條件式存取原則的案例。
>- 若要使用 SQL Server 帳戶使用者名稱與密碼進行連線，您現在可以使用新的 `SqlPassword` 選項，這是特別適用於 Azure SQL 的建議選項，因為此選項會啟用更安全的連線預設值。
>- 若要使用 Azure Active Directory 帳戶使用者名稱與密碼進行連線，請分別利用使用者名稱與密碼來指定連接字串中的 `Authentication=ActiveDirectoryPassword` 及 `UID` 和 `PWD` 關鍵字。
>- 若要使用 Windows 整合式或 Active Directory 整合式 (僅限 Windows 與 Linux/macOS 17.6+ 驅動程式) 驗證進行連線，請在連接字串中指定 `Authentication=ActiveDirectoryIntegrated`。 驅動程式將自動選擇正確的驗證模式。 不得指定 `UID` 和 `PWD`。
>- 若要使用 Active Directory 互動式 (僅限 Windows 驅動程式) 驗證進行連線，就必須指定 `UID`。

## <a name="authenticating-with-an-access-token"></a>使用存取權杖進行驗證

`SQL_COPT_SS_ACCESS_TOKEN` 預先連線屬性允許使用從 Azure AD 取得的存取權杖進行驗證 (而不是使用者名稱與密碼)，同時也會略過驅動程式對存取權杖的協商和取得。 若要使用存取權杖，請將 `SQL_COPT_SS_ACCESS_TOKEN` 連線屬性設定為指向 `ACCESSTOKEN` 結構的指標：

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

`ACCESSTOKEN` 是一個可變長度結構，由 4 個位元組的「長度」  且後面接著形成存取權杖之不透明資料的「長度」  位元組所組成。 由於 SQL Server 處理存取權杖的方式，因此，必須展開透過 [OAuth 2.0](/azure/active-directory/develop/active-directory-authentication-scenarios) \(部分機器翻譯\) JSON 回應取得的權杖，讓每個位元組後面都接著一個 0 填補位元組，類似於僅包含 ASCII 字元的 UCS-2 字串；不過，此權杖是一個不透明的值，而且指定的長度 (以位元組為單位) 不得包含任何 Null 結束字元。 由於其在長度和格式方面有大量限制，因此只能透過 `SQL_COPT_SS_ACCESS_TOKEN` 連線屬性以程式設計方式使用這個驗證方法；沒有對應的 DSN 或連接字串關鍵字。 連接字串不能包含 `UID`、`PWD`、`Authentication` 或 `Trusted_Connection` 關鍵字。

> [!NOTE]
> ODBC Driver 13.1 版僅在 _Windows_ 上支援此驗證。

## <a name="azure-active-directory-authentication-sample-code"></a>Azure Active Directory 驗證範例程式碼

下列範例示範如何使用 Azure Active Directory 搭配連線關鍵字來連線到 SQL Server 所需的程式碼。 請注意，不需要變更應用程式程式碼本身；使用 Azure AD 進行驗證唯一需要修改的是連接字串或 DSN (如已使用)：
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);    
    ...
~~~
下列範例示範如何使用 Azure Active Directory 搭配存取權杖驗證來連線到 SQL Server 所需的程式碼。 在此案例中，您必須修改應用程式程式碼來處理存取權杖，並設定相關聯的連線屬性。
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server}"
    SQLCHAR accessToken[] = "eyJ0eXAiOi..."; // In the format extracted from an OAuth JSON response
    ...
    DWORD dataSize = 2 * strlen(accessToken);
    ACCESSTOKEN *pAccToken = malloc(sizeof(ACCESSTOKEN) + dataSize);
    pAccToken->dataSize = dataSize;
    // Expand access token with padding bytes
    for(int i = 0, j = 0; i < dataSize; i += 2, j++) {
        pAccToken->data[i] = accessToken[j];
        pAccToken->data[i+1] = 0;
    }
    ...
    SQLSetConnectAttr(hDbc, SQL_COPT_SS_ACCESS_TOKEN, (SQLPOINTER)pAccToken, SQL_IS_POINTER);
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);        
    ...
    free(pAccToken);
~~~
以下是與 Azure Active Directory 互動式驗證搭配使用的範例連接字串。 請注意，其並未包含 PWD 欄位，因為密碼會使用 Azure 驗證畫面來輸入。
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~
以下是與 Azure Active Directory 受控識別驗證搭配使用的範例連接字串。 請注意，針對使用者指派的身分識別，UID 會設為使用者身分識別的物件識別碼。
~~~
// For system-assigned identity,
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};Authentication=ActiveDirectoryMsi"
...
// For user-assigned identity with object ID equals to myObjectId
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myObjectId;Authentication=ActiveDirectoryMsi"
~~~

## <a name="considerations-for-using-adfs-federated-accounts-on-linuxmacos"></a>在 Linux/macOS 上使用 ADFS 同盟帳戶的考量

從 17.6 版開始，適用於 Linux 與 macOS 的驅動程式支援搭配使用者名稱/密碼 (`ActiveDirectoryPassword`) 或 Kerberos (`ActiveDirectoryIntegrated`) 使用 Azure Active Directory ADFS 同盟帳戶進行驗證。 使用整合模式時，會有一些取決於平台的限制。

當 UPN 尾碼與 Kerberos 領域不同 (也就是使用替代的 UPN 尾碼) 的使用者進行驗證時，必須在取得 Kerberos 票證時使用企業主體選項 (搭配 `kinit` 使用 `-E` 選項，並以 `user@federated-domain` 的格式提供主體名稱)。 這可讓驅動程式正確判斷同盟網域與 Kerberos 領域。

您可以透過檢查 `klist` 命令的輸出，來確認有適當的 Kerberos 票證可供使用。 如果同盟網域與 Kerberos 領域及 UPN 尾碼相同，主體名稱的格式將會是 `user@realm`。 如果其為不同，主體名稱的格式應該會是 `user@federated-domain@realm`。

### <a name="linux"></a>Linux

在 SuSE 11 上，預設的 Kerberos 程式庫版本 (1.6.x) 並不支援使用替代 UPN 尾碼所需的企業主體選項。 若要搭配 Azure AD 整合式驗證使用替代 UPN 尾碼，請將 Kerberos 程式庫升級到 1.7 或更新版本。

在 Alpine Linux 上，預設的 `libcurl` 並不支援進行 Azure AD 整合式驗證所需的 SPNEGO/Kerberos 驗證。

### <a name="macos"></a>macOS

系統 Kerberos 程式庫 `kinit` 能透過 `--enterprise` 選項支援企業主體，但也會隱含地執行名稱標準化，其會防止使用替代 UPN 尾碼。 若要搭配 Azure AD 整合式驗證使用替代 UPN 尾碼，請透過 `brew install krb5` 安裝較新的 Kerberos 程式庫，並以上面所述的方式搭配 `-E` 選項使用其 `kinit`。

## <a name="see-also"></a>另請參閱

[適用於使用 Azure AD 驗證之 Azure SQL Database 的權杖型驗證支援](/archive/blogs/sqlsecurity/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

[使用整合式驗證](linux-mac/using-integrated-authentication.md)