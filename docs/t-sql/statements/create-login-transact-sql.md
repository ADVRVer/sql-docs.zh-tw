---
title: CREATE LOGIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE_LOGIN_TSQL
- CREATE LOGIN
- LOGIN_TSQL
- LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], logins
- mapping logins [SQL Server]
- logins [SQL Server], creating
- CREATE LOGIN statement
- permissions [SQL Server], logins
- Windows domain accounts [SQL Server]
- re-hashing passwords
- certificates [SQL Server], logins
ms.assetid: eb737149-7c92-4552-946b-91085d8b1b01
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5e7b598d4fe860c0d0eb1cb95730bb483be5470a
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48252105"
---
# <a name="create-login-transact-sql"></a>CREATE LOGIN (Transact-SQL)

建立 SQL Server、SQL Database、SQL 資料倉儲或平行資料倉儲資料庫的登入。 按一下下列其中一個索引標籤，以查看特定版本的語法、引數、備註、權限和範例。

如需語法慣例的詳細資訊，請參閱 [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。 

## <a name="click-a-product"></a>按一下產品！

在下一行中，按一下您感興趣的產品名稱。 視您所按下的產品而定，此點選會在本網頁的這裡顯示不同的內容。

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> ||||||
> |-|-|-|-|-|
> |**_\* SQL Server \*_**|[SQL Database<br />邏輯伺服器](create-login-transact-sql.md?view=azuresqldb-current)|[SQL Database<br />受控執行個體](create-login-transact-sql.md?view=azuresqldb-mi-current)|[SQL 資料<br />倉儲](create-login-transact-sql.md?view=azure-sqldw-latest)|[平行處理<br />資料倉儲](create-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="sql-server"></a>[SQL Server]

## <a name="syntax"></a>語法 
  
```  
-- Syntax for SQL Server  
CREATE LOGIN login_name { WITH <option_list1> | FROM <sources> }  
  
<option_list1> ::=   
    PASSWORD = { 'password' | hashed_password HASHED } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
    SID = sid  
    | DEFAULT_DATABASE = database      
    | DEFAULT_LANGUAGE = language  
    | CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
    | CREDENTIAL = credential_name   
  
<sources> ::=  
    WINDOWS [ WITH <windows_options>[ ,... ] ]  
    | CERTIFICATE certname  
    | ASYMMETRIC KEY asym_key_name  
  
<windows_options> ::=        
    DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
```  
  
## <a name="arguments"></a>引數  
*login_name*  
指定建立的登入名稱。 有四種類型的登入：SQL Server 登入、Windows 登入、憑證對應登入和非對稱金鑰對應登入。 當您建立從 Windows 網域帳戶對應的登入時，對於 Windows 2000 之前版本的使用者登入名稱，您必須使用 [\<domainName>\\<login_name>] 格式。 您無法使用 login_name@DomainName 格式的 UPN。 如需範例，請參閱本文稍後的範例 D。 驗證登入屬於 **sysname** 類型、必須符合[識別碼](../../relational-databases/databases/database-identifiers.md)的規則，而且不得包含 '**\\**'。 Windows 登入可以包含 '**\\**'。 根據 Active Directory 使用者的登入，僅限小於 21 個字元的名稱。 

PASSWORD **='**_password_**'* 僅適用於 SQL Server 登入。 指定要建立的登入密碼。 您應該使用增強式密碼。 如需詳細資訊，請參閱[強式密碼](../../relational-databases/security/strong-passwords.md)和[密碼原則](../../relational-databases/security/password-policy.md)。 從  SQL Server 2012 (11.x) 開始，預存密碼資訊會使用加料式 (Salted) 密碼的 SHA-512 加以計算。 
  
密碼會區分大小寫。 密碼長度應該一律至少為 8 個字元，且不能超過 128 個字元。 密碼可以包含 a-z、A-Z、0-9 及大多數非英數字元。 密碼不能包含單引號或 *login_name*。 
  
PASSWORD **=**_hashed\_password_  
僅適用於 HASHED 關鍵字。 指定要建立之登入的密碼雜湊值。 
  
HASHED 僅適用於 SQL Server 登入。 指定在 PASSWORD 引數之後輸入的密碼已雜湊處理。 如果未選取這個選項，則輸入的密碼字串在儲存至資料庫之前會先雜湊處理。 只有要在兩部伺服器之間移轉資料庫時，才應使用這個選項。 請勿使用 HASHED 選項來建立新登入。 HASHED 選項無法與 SQL 7 或更早版本所建立的雜湊搭配使用。

MUST_CHANGE 只適用於 SQL Server 登入。 如果有包含這個選項，第一次使用新登入時，SQL Server 會提示使用者輸入新密碼。 
  
CREDENTIAL **=**_credential\_name_  
對應到新 SQL Server 登入的認證名稱。 認證必須已存在於伺服器中。 目前這個選項只會將認證連結到登入。 認證無法對應至系統管理員 (sa) 登入。 
  
SID = *sid*  
用來重新建立登入。 僅適用於 SQL Server 驗證登入，不適用於 Windows 驗證登入。 指定新 SQL Server 驗證登入的 SID。 如果未使用這個選項，SQL Server 將自動指派 SID。 SID 結構取決於 SQL Server 版本。 SQL Server 登入 SID：以 GUID 為基礎的 16 位元組 (**binary(16)**) 常值。 例如， `SID = 0x14585E90117152449347750164BA00A7`。 
  
DEFAULT_DATABASE **=**_database_  
指定要指派給登入的預設資料庫。 如果不包括這個選項，預設資料庫將設為 master。 
  
DEFAULT_LANGUAGE **=**_language_  
指定要指派給登入的預設語言。 如果不包括這個選項，預設語言將設為伺服器的目前預設語言。 如果伺服器的預設語言在未來有所變更，登入的預設語言會保持不變。 
  
CHECK_EXPIRATION **=** { ON | **OFF** }  
僅適用於 SQL Server 登入。 指定是否應該對這個登入強制執行密碼逾期原則。 預設值是 OFF。 
  
CHECK_POLICY **=** { **ON** | OFF }  
僅適用於 SQL Server 登入。 指定應該在這項登入上強制使用執行 SQL Server 之電腦的 Windows 密碼原則。 預設值是 ON。 
  
如果 Windows 原則要求增強式密碼，則密碼必須至少包含下列四個特性的其中三個：  
  
- 大寫字元 (A-Z)。 
- 小寫字元 (a-z)。 
- 數字 (0-9)。 
- 其中一個非英數字元，例如空格、_、@、*、^、%、!、$、# 或 &。 
  
WINDOWS  
指定登入對應到 Windows 登入。 
  
CERTIFICATE *certname*  
指定與這項登入相關聯的憑證名稱。 這個憑證必須已存在於 master 資料庫中。 
  
ASYMMETRIC KEY *asym_key_name*  
指定與這項登入相關聯的非對稱金鑰名稱。 這個金鑰必須已存在於 master 資料庫中。 
  
## <a name="remarks"></a>Remarks  
- 密碼會區分大小寫。
- 只有當您建立 SQL Server 登入時，才支援預先雜湊處理密碼。
- 如果指定 MUST_CHANGE，則 CHECK_EXPIRATION 和 CHECK_POLICY 必須設為 ON。 否則，陳述式便會失敗。
- 不支援 CHECK_POLICY = OFF 和 CHECK_EXPIRATION = ON 的結合。
- 當 CHECK_POLICY 設為 OFF 時，*lockout_time* 會重設，且 CHECK_EXPIRATION 會設為 OFF。 
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION 和 CHECK_POLICY 只會在 Windows Server 2003 和更新版本中強制執行。 如需詳細資訊，請參閱＜ [Password Policy](../../relational-databases/security/password-policy.md)＞。 
  
- 從憑證或非對稱金鑰建立的登入只能用於程式碼簽章。 它們不能用來連線至 SQL Server。 僅當憑證或非對稱金鑰已存在於 master 時，您才能從憑證或非對稱金鑰中建立登入。 
- 如需傳送登入的指令碼，請參閱 [如何在 SQL Server 2005 和 SQL Server 2008 的執行個體之間傳送登入和密碼](http://support.microsoft.com/kb/918992)。
- 建立登入會自動啟用新登入，並授與登入伺服器層級的 **CONNECT SQL** 權限。 
- 伺服器的[驗證模式](../../relational-databases/security/choose-an-authentication-mode.md)必須符合登入類型，以允許存取。
- 如需設計權限系統的資訊，請參閱 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)。

## <a name="permissions"></a>[權限]  
- 只有具備伺服器的 **ALTER ANY LOGIN** 權限或 **securityadmin** 固定伺服器角色之成員資格的使用者才能建立登入。 如需詳細資訊，請參閱[伺服器層級角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles)和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles。
- 如果使用 **CREDENTIAL** 選項，則也需要伺服器的 **ALTER ANY CREDENTIAL** 權限。 
  
## <a name="after-creating-a-login"></a>建立登入之後  
建立登入之後，登入就可以連線至 SQL Server，但是只會取得 **public** 角色的權限。 請考慮執行下列其中一些活動。 
  
 - 若要連接至資料庫，請建立用於登入的資料庫使用者。 如需詳細資訊，請參閱 [CREATE USER](../../t-sql/statements/create-user-transact-sql.md)。 
  
 - 使用 [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md) 建立使用者定義的伺服器角色。 使用 **ALTER SERVER ROLE** … 使用 **ADD MEMBER** 將新登入加入至使用者定義的伺服器角色中。 如需詳細資訊，請參閱 [CREATE SERVER ROL](../../t-sql/statements/create-server-role-transact-sql.md) 和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md)。 
  
 - 使用 **sp_addsrvrolemember** 將登入加入至固定伺服器角色中。 如需詳細資訊，請參閱[伺服器層級角色](../../relational-databases/security/authentication-access/server-level-roles.md)和 [sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)。 
  
 - 使用 **GRANT** 陳述式將伺服器層級權限授與新登入或包含登入的角色。 如需詳細資訊，請參閱 [GRANT](../../t-sql/statements/grant-transact-sql.md)。 
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-login-with-a-password"></a>A. 建立具有密碼的登入  
 下列範例會針對特定的使用者建立登入，並指派密碼。 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-with-a-password-that-must-be-changed"></a>B. 建立具有密碼的登入，且密碼必須變更
 下列範例會針對特定的使用者建立登入，並指派密碼。 `MUST_CHANGE` 選項需要使用者在第一次連接到伺服器時變更這個密碼。 
  
**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>' 
    MUST_CHANGE,  CHECK_EXPIRATION = ON;
GO  
``` 

> [!NOTE]
> 當 CHECK_EXPIRATION 為 OFF 時，不可使用 MUST_CHANGE 選項。
  
### <a name="c-creating-a-login-mapped-to-a-credential"></a>C. 建立對應到認證的登入  
 下列範例會針對特定使用者建立登入 (透過使用者)。 此登入會對應到認證。 
  
**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>',   
    CREDENTIAL = <credentialName>;  
GO  
```  
  
### <a name="d-creating-a-login-from-a-certificate"></a>D. 從憑證建立登入  
 下列範例會從 master 的憑證建立特定使用者的登入。 
  
**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 
  
```sql
USE MASTER;  
CREATE CERTIFICATE <certificateName>  
    WITH SUBJECT = '<login_name> certificate in master database',  
    EXPIRY_DATE = '12/05/2025';  
GO  
CREATE LOGIN <login_name> FROM CERTIFICATE <certificateName>;  
GO  
```  
  
### <a name="e-creating-a-login-from-a-windows-domain-account"></a>E. 從 Windows 網域帳戶中建立登入  
 下列範例會從 Windows 網域帳戶建立登入。 
  
**適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。 
  
```sql  
CREATE LOGIN [<domainName>\<login_name>] FROM WINDOWS;  
GO  
```  
  
### <a name="f-creating-a-login-from-a-sid"></a>F. 從 SID 建立登入  
 下列範例會先建立 SQL Server 驗證登入，並判斷登入的 SID。 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 我的查詢會傳回 0x241C11948AEEB749B0D22646DB1A19F2 作為 SID。 您的查詢將傳回不同的值。 下列陳述式會刪除登入，並重新建立登入。 使用來自前一個查詢的 SID。 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
- [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
- [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
- [密碼原則](../../relational-databases/security/password-policy.md)   
- [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
- [建立登入](../../relational-databases/security/authentication-access/create-a-login.md)  
  
::: moniker-end
::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> ||||||
> |-|-|-|-|-|
> |[SQL Server](create-login-transact-sql.md?view=sql-server-2016)|**_\* SQL Database<br />邏輯伺服器 \*_**|[SQL Database<br />受控執行個體](create-login-transact-sql.md?view=azuresqldb-mi-current)|[SQL 資料<br />倉儲](create-login-transact-sql.md?view=azure-sqldw-latest)|[平行處理<br />資料倉儲](create-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-database-logical-server"></a>Azure SQL Database 邏輯伺服器
  
## <a name="syntax"></a>語法 
  
```
-- Syntax for Azure SQL Database  
CREATE LOGIN login_name  
 { WITH <option_list> }  
  
<option_list> ::=   
    PASSWORD = { 'password' }  
    [ , SID = sid ]  
```  

## <a name="arguments"></a>引數  
*login_name*  
指定建立的登入名稱。 Azure SQL Database 邏輯伺服器僅支援 SQL 登入。 

PASSWORD **='** password**'*  
指定要建立的 SQL 登入密碼。 您應該使用增強式密碼。 如需詳細資訊，請參閱[強式密碼](../../relational-databases/security/strong-passwords.md)和[密碼原則](../../relational-databases/security/password-policy.md)。 從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，預存密碼資訊會使用加料式 (Salted) 密碼的 SHA-512 加以計算。 
  
密碼會區分大小寫。 密碼長度應該一律至少為 8 個字元，且不能超過 128 個字元。 密碼可以包含 a-z、A-Z、0-9 及大多數非英數字元。 密碼不能包含單引號或 *login_name*。 

SID = *sid*  
用來重新建立登入。 僅適用於 SQL Server 驗證登入，不適用於 Windows 驗證登入。 指定新 SQL Server 驗證登入的 SID。 如果未使用這個選項，SQL Server 將自動指派 SID。 SID 結構取決於 SQL Server 版本。 對於 SQL Database，這通常是由 `0x01060000000000640000000000000000` 再加上代表 GUID 的 16 位元組組成的 32 位元組 (**binary(32)**) 常值。 例如， `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`。 
  
## <a name="remarks"></a>Remarks  
- 密碼會區分大小寫。
- 如需傳送登入的指令碼，請參閱 [如何在 SQL Server 2005 和 SQL Server 2008 的執行個體之間傳送登入和密碼](http://support.microsoft.com/kb/918992)。
- 建立登入會自動啟用新登入，並授與登入伺服器層級的 **CONNECT SQL** 權限。 
- 伺服器的[驗證模式](../../relational-databases/security/choose-an-authentication-mode.md)必須符合登入類型，以允許存取。
    - 如需設計權限系統的資訊，請參閱 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)。
  
## <a name="login"></a>登入

### <a name="sql-database-logins"></a>SQL 資料庫登入
**CREATE LOGIN** 陳述式必須是批次中唯一的陳述式。 
  
在連線至 SQL Database 的一些方法中 (例如 **sqlcmd**)，您必須使用 *\<login>*@*\<server>* 標記法，將 SQL Database 伺服器名稱附加至連接字串中的登入名稱。 例如，如果您的登入為 `login1`，且 SQL Database 伺服器的完整名稱為 `servername.database.windows.net`，則連接字串的 *username* 參數應該是 `login1@servername`。 由於 *username* 參數的總長度為 128 個字元，因此 *login_name* 的限制為 127 個字元減去伺服器名稱的長度。 在此範例中，`login_name` 的長度只能是 117 個字元，因為 `servername` 為 10 個字元。 
  
在 SQL Database 中，您必須連線至 master 資料庫以建立登入。 
  
 SQL Server 規則可讓您建立 \<loginname>@\<servername> 格式的 SQL Server 驗證登入。 如果您的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 伺服器是 **myazureserver**，而您的登入是 **myemail@live.com**，則必須以 **myemail@live.com@myazureserver** 提供登入。 
  
在 SQL Database 中，驗證連線需要登入資料，且伺服器層級防火牆規則會暫時快取在每個資料庫中。 此快取會定期重新整理。 若要重新整理驗證快取，並確定資料庫擁有登入資料表的最新版本，請執行 [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md)。 
  
 如需 SQL Database 登入的詳細資訊，請參閱[管理 Windows Azure SQL Database 中的資料庫和登入](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins)。 
 
## <a name="permissions"></a>[權限]

只有 master 資料庫中的伺服器層級主體登入 (由佈建程序所建立) 或 `loginmanager` 資料庫角色成員，才能建立新登入。 如需詳細資訊，請參閱[伺服器層級角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles)和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles。

## <a name="logins"></a>登入
- 必須具有伺服器的 **ALTER ANY LOGIN** 權限或 **securityadmin** 固定伺服器角色的成員資格。 只有具備伺服器的 **ALTER ANY LOGIN** 權限或 securityadmin 權限之成員資格的 Azure Active Directory (Azure AD) 帳戶才能執行這個命令
- 必須是用於 Azure SQL 邏輯伺服器之相同目錄中的 Azure AD 成員
  
## <a name="after-creating-a-login"></a>建立登入之後  
建立登入之後，登入就可以連線至 SQL Database，但是只會取得 **public** 角色的權限。 請考慮執行下列其中一些活動。 
  
- 若要連線至資料庫，請建立用於登入該資料庫的資料庫使用者。 如需詳細資訊，請參閱 [CREATE USER](../../t-sql/statements/create-user-transact-sql.md)。 
- 若要將權限授與資料庫中的使用者，請使用**ALTER SERVER ROLE** … **ADD MEMBER** 陳述式可將用法新增至其中一個內建的資料庫角色或自訂角色，或直接使用 [GRANT](../../t-sql/statements/grant-transact-sql.md) 陳述式將權限授與使用者。 如需詳細資訊，請參閱[非系統管理員角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users)、[ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles 和 [GRANT](grant-transact-sql.md) 陳述式。
- 若要授與伺服器範圍權限，請在 master 資料庫中建立資料庫使用者，並使用 **ALTER SERVER ROLE** … **ADD MEMBER** 陳述式可將用法新增至其中一個管理伺服器角色。 如需詳細資訊，請參閱[伺服器層級角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles)和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md)，以及[伺服器角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles)。
- 使用 **GRANT** 陳述式將伺服器層級權限授與新登入或包含登入的角色。 如需詳細資訊，請參閱 [GRANT](../../t-sql/statements/grant-transact-sql.md)。
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-login-with-a-password"></a>A. 建立具有密碼的登入  
 下列範例會針對特定的使用者建立登入，並指派密碼。 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-from-a-sid"></a>B. 從 SID 建立登入  
 下列範例會先建立 SQL Server 驗證登入，並判斷登入的 SID。 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 我的查詢會傳回 0x241C11948AEEB749B0D22646DB1A19F2 作為 SID。 您的查詢將傳回不同的值。 下列陳述式會刪除登入，並重新建立登入。 使用來自前一個查詢的 SID。 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [密碼原則](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [建立登入](../../relational-databases/security/authentication-access/create-a-login.md)  

::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> ||||||
> |-|-|-|-|-|
> |[SQL Server](create-login-transact-sql.md?view=sql-server-2016)|[SQL Database<br />邏輯伺服器](create-login-transact-sql.md?view=azuresqldb-current)|**_\* SQL Database<br />受控執行個體 \*_**|[SQL 資料<br />倉儲](create-login-transact-sql.md?view=azure-sqldw-latest)|[平行處理<br />資料倉儲](create-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-database-managed-instance"></a>Azure SQL Database 受控執行個體

## <a name="overview"></a>概觀

## <a name="syntax"></a>語法 
  
```sql
-- Syntax for Azure SQL Database  
CREATE LOGIN login_name  
 { WITH <option_list> }  
  
<option_list> ::=   
    PASSWORD = { 'password' }  
    [ , SID = sid ]  
```  

## <a name="arguments"></a>引數  
*login_name*  
指定建立的登入名稱。 Azure SQL Database 受控執行個體僅支援 SQL 登入。 

PASSWORD **='** password**'*  
指定要建立的 SQL 登入密碼。 您應該使用增強式密碼。 如需詳細資訊，請參閱[強式密碼](../../relational-databases/security/strong-passwords.md)和[密碼原則](../../relational-databases/security/password-policy.md)。 從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，預存密碼資訊會使用加料式 (Salted) 密碼的 SHA-512 加以計算。 
  
密碼會區分大小寫。 密碼長度應該一律至少為 8 個字元，且不能超過 128 個字元。 密碼可以包含 a-z、A-Z、0-9 及大多數非英數字元。 密碼不能包含單引號或 *login_name*。 

SID = *sid*  
用來重新建立登入。 僅適用於 SQL Server 驗證登入，不適用於 Windows 驗證登入。 指定新 SQL Server 驗證登入的 SID。 如果未使用這個選項，SQL Server 將自動指派 SID。 SID 結構取決於 SQL Server 版本。 對於 SQL Database，這通常是由 `0x01060000000000640000000000000000` 再加上代表 GUID 的 16 位元組組成的 32 位元組 (**binary(32)**) 常值。 例如， `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`。 
  
## <a name="remarks"></a>Remarks  
- 密碼會區分大小寫。
- 如需傳送登入的指令碼，請參閱 [如何在 SQL Server 2005 和 SQL Server 2008 的執行個體之間傳送登入和密碼](http://support.microsoft.com/kb/918992)。
- 建立登入會自動啟用新登入，並授與登入伺服器層級的 **CONNECT SQL** 權限。 
- 伺服器的[驗證模式](../../relational-databases/security/choose-an-authentication-mode.md)必須符合登入類型，以允許存取。
    - 如需設計權限系統的資訊，請參閱 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)。
  
## <a name="login"></a>登入

### <a name="sql-database-logins"></a>SQL 資料庫登入
**CREATE LOGIN** 陳述式必須是批次中唯一的陳述式。 
  
在連線至 SQL Database 的一些方法中 (例如 **sqlcmd**)，您必須使用 *\<login>*@*\<server>* 標記法，將 SQL Database 伺服器名稱附加至連接字串中的登入名稱。 例如，如果您的登入為 `login1`，且 SQL Database 伺服器的完整名稱為 `servername.database.windows.net`，則連接字串的 *username* 參數應該是 `login1@servername`。 由於 *username* 參數的總長度為 128 個字元，因此 *login_name* 的限制為 127 個字元減去伺服器名稱的長度。 在此範例中，`login_name` 的長度只能是 117 個字元，因為 `servername` 為 10 個字元。 
  
在 SQL Database 中，您必須連線至 master 資料庫以建立登入。 
  
 SQL Server 規則可讓您建立 \<loginname>@\<servername> 格式的 SQL Server 驗證登入。 如果您的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 伺服器是 **myazureserver**，而您的登入是 **myemail@live.com**，則必須以 **myemail@live.com@myazureserver** 提供登入。 
  
在 SQL Database 中，驗證連線需要登入資料，且伺服器層級防火牆規則會暫時快取在每個資料庫中。 此快取會定期重新整理。 若要重新整理驗證快取，並確定資料庫擁有登入資料表的最新版本，請執行 [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md)。 
  
 如需 SQL Database 登入的詳細資訊，請參閱[管理 Windows Azure SQL Database 中的資料庫和登入](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins)。 
 
## <a name="permissions"></a>[權限]

只有 master 資料庫中的伺服器層級主體登入 (由佈建程序所建立) 或 `loginmanager` 資料庫角色成員，才能建立新登入。 如需詳細資訊，請參閱[伺服器層級角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles)和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles。

## <a name="logins"></a>登入
- 必須具有伺服器的 **ALTER ANY LOGIN** 權限或 **securityadmin** 固定伺服器角色的成員資格。 只有具備伺服器的 **ALTER ANY LOGIN** 權限或 securityadmin 權限之成員資格的 Azure Active Directory (Azure AD) 帳戶才能執行這個命令
- 必須是用於 Azure SQL 邏輯伺服器之相同目錄中的 Azure AD 成員
  
## <a name="after-creating-a-login"></a>建立登入之後  
建立登入之後，登入就可以連線至 SQL Database，但是只會取得 **public** 角色的權限。 請考慮執行下列其中一些活動。 
  
- 若要連線至資料庫，請建立用於登入該資料庫的資料庫使用者。 如需詳細資訊，請參閱 [CREATE USER](../../t-sql/statements/create-user-transact-sql.md)。 
- 若要將權限授與資料庫中的使用者，請使用**ALTER SERVER ROLE** … **ADD MEMBER** 陳述式可將用法新增至其中一個內建的資料庫角色或自訂角色，或直接使用 [GRANT](../../t-sql/statements/grant-transact-sql.md) 陳述式將權限授與使用者。 如需詳細資訊，請參閱[非系統管理員角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users)、[ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles 和 [GRANT](grant-transact-sql.md) 陳述式。
- 若要授與伺服器範圍權限，請在 master 資料庫中建立資料庫使用者，並使用 **ALTER SERVER ROLE** … **ADD MEMBER** 陳述式可將用法新增至其中一個管理伺服器角色。 如需詳細資訊，請參閱[伺服器層級角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles)和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md)，以及[伺服器角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles)。
- 使用 **GRANT** 陳述式將伺服器層級權限授與新登入或包含登入的角色。 如需詳細資訊，請參閱 [GRANT](../../t-sql/statements/grant-transact-sql.md)。
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-login-with-a-password"></a>A. 建立具有密碼的登入  
 下列範例會針對特定的使用者建立登入，並指派密碼。 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-from-a-sid"></a>B. 從 SID 建立登入  
 下列範例會先建立 SQL Server 驗證登入，並判斷登入的 SID。 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 我的查詢會傳回 0x241C11948AEEB749B0D22646DB1A19F2 作為 SID。 您的查詢將傳回不同的值。 下列陳述式會刪除登入，並重新建立登入。 使用來自前一個查詢的 SID。 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [密碼原則](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [建立登入](../../relational-databases/security/authentication-access/create-a-login.md)  


  
::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> ||||||
> |-|-|-|-|-|
> |[SQL Server](create-login-transact-sql.md?view=sql-server-2016)|[SQL Database<br />邏輯伺服器](create-login-transact-sql.md?view=azuresqldb-current)|[SQL Database<br />受控執行個體]()|**_\* SQL 資料<br />倉儲 \*_**|[平行處理<br />資料倉儲](create-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-data-warehouse"></a>Azure SQL 資料倉儲
  
## <a name="syntax"></a>語法 
  
```
-- Syntax for Azure SQL Data Warehouse  
CREATE LOGIN login_name  
 { WITH <option_list> }  
  
<option_list> ::=   
    PASSWORD = { 'password' }  
    [ , SID = sid ]  
```  
  
## <a name="arguments"></a>引數  
*login_name*  
指定建立的登入名稱。 Azure SQL Database 僅支援 SQL 登入。 

PASSWORD **='** password**'*  
指定要建立的 SQL 登入密碼。 您應該使用增強式密碼。 如需詳細資訊，請參閱[強式密碼](../../relational-databases/security/strong-passwords.md)和[密碼原則](../../relational-databases/security/password-policy.md)。 從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，預存密碼資訊會使用加料式 (Salted) 密碼的 SHA-512 加以計算。 
  
密碼會區分大小寫。 密碼長度應該一律至少為 8 個字元，且不能超過 128 個字元。 密碼可以包含 a-z、A-Z、0-9 及大多數非英數字元。 密碼不能包含單引號或 *login_name*。 

 SID = *sid*  
 用來重新建立登入。 僅適用於 SQL Server 驗證登入，不適用於 Windows 驗證登入。 指定新 SQL Server 驗證登入的 SID。 如果未使用這個選項，SQL Server 將自動指派 SID。 SID 結構取決於 SQL Server 版本。 對於 SQL 資料倉儲，這通常是由 `0x01060000000000640000000000000000` 再加上代表 GUID 的 16 位元組組成的 32 位元組 (**binary(32)**) 常值。 例如， `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`。 
  
## <a name="remarks"></a>Remarks  
- 密碼會區分大小寫。
- 如需傳送登入的指令碼，請參閱 [如何在 SQL Server 2005 和 SQL Server 2008 的執行個體之間傳送登入和密碼](http://support.microsoft.com/kb/918992)。
- 建立登入會自動啟用新登入，並授與登入伺服器層級的 **CONNECT SQL** 權限。 
- 伺服器的[驗證模式](../../relational-databases/security/choose-an-authentication-mode.md)必須符合登入類型，以允許存取。
    - 如需設計權限系統的資訊，請參閱 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)。
  
## <a name="logins"></a>登入

**CREATE LOGIN** 陳述式必須是批次中唯一的陳述式。 
  
在連線至 SQL 資料倉儲的一些方法中 (例如 **sqlcmd**)，您必須使用 *\<login>*@*\<server>* 標記法，將 SQL 資料倉儲伺服器名稱附加至連接字串中的登入名稱。 例如，如果您的登入為 `login1`，且 SQL 資料倉儲伺服器的完整名稱為 `servername.database.windows.net`，則連接字串的 *username* 參數應該是 `login1@servername`。 由於 *username* 參數的總長度為 128 個字元，因此 *login_name* 的限制為 127 個字元減去伺服器名稱的長度。 在此範例中，`login_name` 的長度只能是 117 個字元，因為 `servername` 為 10 個字元。 
  
在 SQL 資料倉儲中，您必須連線至 master 資料庫以建立登入。 
  
 SQL Server 規則可讓您建立 \<loginname>@\<servername> 格式的 SQL Server 驗證登入。 如果您的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 伺服器是 **myazureserver**，而您的登入是 **myemail@live.com**，則必須以 **myemail@live.com@myazureserver** 提供登入。 
  
在 SQL 資料倉儲中，驗證連線需要登入資料，且伺服器層級防火牆規則會暫時快取在每個資料庫中。 此快取會定期重新整理。 若要重新整理驗證快取，並確定資料庫擁有登入資料表的最新版本，請執行 [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md)。 
  
 如需 SQL 資料倉儲登入的詳細資訊，請參閱[管理 Windows Azure SQL Database 中的資料庫和登入](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins)。 
 
## <a name="permissions"></a>[權限]

只有 master 資料庫中的伺服器層級主體登入 (由佈建程序所建立) 或 `loginmanager` 資料庫角色成員，才能建立新登入。 如需詳細資訊，請參閱[伺服器層級角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles)和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles。

## <a name="after-creating-a-login"></a>建立登入之後  
建立登入之後，登入就可以連線至 SQL 資料倉儲，但是只會取得 **public** 角色的權限。 請考慮執行下列其中一些活動。 
  
- 若要連接至資料庫，請建立用於登入的資料庫使用者。 如需詳細資訊，請參閱 [CREATE USER](../../t-sql/statements/create-user-transact-sql.md)。
- 若要將權限授與資料庫中的使用者，請使用**ALTER SERVER ROLE** … **ADD MEMBER** 陳述式可將用法新增至其中一個內建的資料庫角色或自訂角色，或直接使用 [GRANT](grant-transact-sql.md) 陳述式將權限授與使用者。 如需詳細資訊，請參閱[非系統管理員角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users)、[ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles 和 [GRANT](grant-transact-sql.md) 陳述式。
- 若要授與伺服器範圍權限，請在 master 資料庫中建立資料庫使用者，並使用 **ALTER SERVER ROLE** … **ADD MEMBER** 陳述式可將用法新增至其中一個管理伺服器角色。 如需詳細資訊，請參閱[伺服器層級角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles)和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md)，以及[伺服器角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles)。

- 使用 **GRANT** 陳述式將伺服器層級權限授與新登入或包含登入的角色。 如需詳細資訊，請參閱 [GRANT](../../t-sql/statements/grant-transact-sql.md)。 
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-login-with-a-password"></a>A. 建立具有密碼的登入  
下列範例會針對特定的使用者建立登入，並指派密碼。 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  

### <a name="b-creating-a-login-from-a-sid"></a>B. 從 SID 建立登入  
 下列範例會先建立 SQL Server 驗證登入，並判斷登入的 SID。 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 我的查詢會傳回 0x241C11948AEEB749B0D22646DB1A19F2 作為 SID。 您的查詢將傳回不同的值。 下列陳述式會刪除登入，並重新建立登入。 使用來自前一個查詢的 SID。 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [密碼原則](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [建立登入](../../relational-databases/security/authentication-access/create-a-login.md)  
  
::: moniker-end
::: moniker range=">=aps-pdw-2016||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> ||||||
> |-|-|-|-|-|
> |[SQL Server](create-login-transact-sql.md?view=sql-server-2016)|[SQL Database<br />邏輯伺服器](create-login-transact-sql.md?view=azuresqldb-current)|[SQL Database<br />受控執行個體]()|[SQL 資料<br />倉儲](create-login-transact-sql.md?view=azure-sqldw-latest)|**_\* 平行處理<br />資料倉儲\*_**

&nbsp;

## <a name="parallel-data-warehouse"></a>平行處理資料倉儲

  
## <a name="syntax"></a>語法 
  
```
-- Syntax for Parallel Data Warehouse  
CREATE LOGIN loginName { WITH <option_list1> | FROM WINDOWS }  
  
<option_list1> ::=   
    PASSWORD = { 'password' } [ MUST_CHANGE ]  
    [ , <option_list> [ ,... ] ]  
  
<option_list> ::=    
      CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
```  

## <a name="arguments"></a>引數  
*login_name*  
指定建立的登入名稱。 有四種類型的登入：SQL Server 登入、Windows 登入、憑證對應登入和非對稱金鑰對應登入。 當您建立從 Windows 網域帳戶對應的登入時，對於 Windows 2000 之前版本的使用者登入名稱，您必須使用 [\<domainName>\\<login_name>] 格式。 您無法使用 login_name@DomainName 格式的 UPN。 如需範例，請參閱本文稍後的範例 D。 驗證登入屬於 **sysname** 類型、必須符合[識別碼](../../relational-databases/databases/database-identifiers.md)的規則，而且不得包含 '**\\**'。 Windows 登入可以包含 '**\\**'。 根據 Active Directory 使用者的登入，僅限小於 21 個字元的名稱。 

PASSWORD **='**_password_**'* 僅適用於 SQL Server 登入。 指定要建立的登入密碼。 您應該使用增強式密碼。 如需詳細資訊，請參閱[強式密碼](../../relational-databases/security/strong-passwords.md)和[密碼原則](../../relational-databases/security/password-policy.md)。 從  SQL Server 2012 (11.x) 開始，預存密碼資訊會使用加料式 (Salted) 密碼的 SHA-512 加以計算。 
  
密碼會區分大小寫。 密碼長度應該一律至少為 8 個字元，且不能超過 128 個字元。 密碼可以包含 a-z、A-Z、0-9 及大多數非英數字元。 密碼不能包含單引號或 *login_name*。 
  
MUST_CHANGE 只適用於 SQL Server 登入。 如果有包含這個選項，第一次使用新登入時，SQL Server 會提示使用者輸入新密碼。 
  
CHECK_EXPIRATION **=** { ON | **OFF** }  
僅適用於 SQL Server 登入。 指定是否應該對這個登入強制執行密碼逾期原則。 預設值是 OFF。 
  
CHECK_POLICY **=** { **ON** | OFF }  
僅適用於 SQL Server 登入。 指定應該在這項登入上強制使用執行 SQL Server 之電腦的 Windows 密碼原則。 預設值是 ON。 
  
如果 Windows 原則要求增強式密碼，則密碼必須至少包含下列四個特性的其中三個：  
  
- 大寫字元 (A-Z)。 
- 小寫字元 (a-z)。 
- 數字 (0-9)。 
- 其中一個非英數字元，例如空格、_、@、*、^、%、!、$、# 或 &。 
  
WINDOWS  
指定登入對應到 Windows 登入。 
  
## <a name="remarks"></a>Remarks  
- 密碼會區分大小寫。
- 如果指定 MUST_CHANGE，則 CHECK_EXPIRATION 和 CHECK_POLICY 必須設為 ON。 否則，陳述式便會失敗。
- 不支援 CHECK_POLICY = OFF 和 CHECK_EXPIRATION = ON 的結合。
- 當 CHECK_POLICY 設為 OFF 時，*lockout_time* 會重設，且 CHECK_EXPIRATION 會設為 OFF。 
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION 和 CHECK_POLICY 只會在 Windows Server 2003 和更新版本中強制執行。 如需詳細資訊，請參閱＜ [Password Policy](../../relational-databases/security/password-policy.md)＞。 
  
- 如需傳送登入的指令碼，請參閱 [如何在 SQL Server 2005 和 SQL Server 2008 的執行個體之間傳送登入和密碼](http://support.microsoft.com/kb/918992)。
- 建立登入會自動啟用新登入，並授與登入伺服器層級的 **CONNECT SQL** 權限。 
- 如需設計權限系統的資訊，請參閱 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)。

## <a name="permissions"></a>[權限]  
只有具備伺服器的 **ALTER ANY LOGIN** 權限或 **securityadmin** 固定伺服器角色之成員資格的使用者才能建立登入。 如需詳細資訊，請參閱[伺服器層級角色](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles)和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles。
  
## <a name="after-creating-a-login"></a>建立登入之後  
建立登入之後，登入就可以連線至 SQL 資料倉儲，但是只會取得 **public** 角色的權限。 請考慮執行下列其中一些活動。 
  
 - 若要連接至資料庫，請建立用於登入的資料庫使用者。 如需詳細資訊，請參閱 [CREATE USER](../../t-sql/statements/create-user-transact-sql.md)。 
  
 - 使用 [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md) 建立使用者定義的伺服器角色。 使用 **ALTER SERVER ROLE** … 使用 **ADD MEMBER** 將新登入加入至使用者定義的伺服器角色中。 如需詳細資訊，請參閱 [CREATE SERVER ROL](../../t-sql/statements/create-server-role-transact-sql.md) 和 [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md)。 
  
 - 使用 **sp_addsrvrolemember** 將登入加入至固定伺服器角色中。 如需詳細資訊，請參閱[伺服器層級角色](../../relational-databases/security/authentication-access/server-level-roles.md)和 [sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)。 
  
 - 使用 **GRANT** 陳述式將伺服器層級權限授與新登入或包含登入的角色。 如需詳細資訊，請參閱 [GRANT](../../t-sql/statements/grant-transact-sql.md)。 
  
## <a name="examples"></a>範例  
  
### <a name="g-creating-a-sql-server-authentication-login-with-a-password"></a>G. 建立使用密碼的 SQL Server 驗證登入  
 下列範例會建立使用密碼 `A2c3456` 的登入 `Mary7`。 
  
```sql  
CREATE LOGIN Mary7 WITH PASSWORD = 'A2c3456$#' ;  
```  
  
### <a name="h-using-options"></a>H. 使用選項  
 下列範例會建立使用密碼與部分選用引數的登入 `Mary8`。 
  
```sql  
CREATE LOGIN Mary8 WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
```  
  
### <a name="i-creating-a-login-from-a-windows-domain-account"></a>I. 從 Windows 網域帳戶中建立登入  
 下列範例會從 `Contoso` 網域中名稱為 `Mary` 的 Windows 網域帳戶建立登入。 
  
```sql  
CREATE LOGIN [Contoso\Mary] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [密碼原則](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [建立登入](../../relational-databases/security/authentication-access/create-a-login.md)  
  
---  

::: moniker-end
