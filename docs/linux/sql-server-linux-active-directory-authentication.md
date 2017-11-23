---
title: "Active Directory 驗證 Linux 上的 SQL server |Microsoft 文件"
description: "本教學課程提供的 SQL Server on Linux 的 AAD 驗證的設定步驟。"
author: meet-bhagdev
ms.date: 10/09/2017
ms.author: meetb
manager: jhubbard
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
helpviewer_keywords: Linux, AAD authentication
ms.workload: On Demand
ms.openlocfilehash: ab9be968e11688a960e4306f82cf7ca47666f688
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="active-directory-authentication-with-sql-server-on-linux"></a>Active Directory 驗證與 SQL Server on Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

本教學課程說明如何設定[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]on Linux 支援 Active Directory (AD) 驗證，也稱為整合式驗證。 AD 驗證可讓已加入網域的用戶端的 Windows 或 Linux 向[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用其網域認證和 Kerberos 通訊協定。

AD 驗證透過具有下列優點[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]驗證：

* 使用者驗證透過單一登入，而不會提示輸入密碼。   
* 藉由建立的 AD 群組的登入，您可以管理存取權與權限[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用 AD 群組成員資格。  
* 每位使用者都有單一識別您的組織，因此您不需要追蹤其中的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]登入對應至哪些使用者。   
* AD 可讓您強制執行組織的集中式的密碼原則。   

本教學課程包含下列工作：

> [!div class="checklist"]
> * 加入[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD 網域的主機
> * 建立 AD 使用者輸入[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]和設定 SPN
> * 設定[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]服務 keytab
> * 在 TRANSACT-SQL 中建立 AD 為基礎的登入
> * 連接到[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用 AD 驗證

## <a name="prerequisites"></a>必要條件

設定 AD 驗證之前，您需要：

* 設定您的網路上的 AD 網域控制站 (Windows)  
* 安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
  * [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

> [!IMPORTANT]
> 限制：
> - 此時，資料庫鏡像端點支援的唯一的驗證方法是憑證。 在未來版本中，將會啟用 WINDOWS 驗證方法。
> - 第 3 個合作對象 AD 工具不支援 Centrify、 Powerbroker 和 Vintela 

## <a name="join-includessnoversionincludesssnoversion-mdmd-host-to-ad-domain"></a>加入[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD 網域的主機

使用下列步驟來加入[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Active Directory 網域的主機：

1. 使用 **[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)** 主機電腦加入 AD 網域。 如果您還沒有這麼做，realmd 和 Kerberos 用戶端套件上安裝[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]主機電腦使用您的 Linux 散發套件管理員：

   ```bash
   # RHEL
   sudo yum install realmd krb5-workstation

   # SUSE
   sudo zypper install realmd krb5-client

   # Ubuntu
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. 如果 Kerberos 用戶端封裝安裝會提示您輸入領域名稱，請輸入您的網域名稱以大寫表示。

   > [!NOTE]
   > 本逐步解說"contoso.com"和"CONTOSO.COM"做為範例網域和領域名稱，會分別使用。 您應該取代這些與您自己的值。 這些命令會區分大小寫，因此請確定您使用大寫只要它使用在本逐步解說。

1. 設定您[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]作為 DNS nameserver AD 網域控制站的 IP 位址的主機電腦。 

   - **Ubuntu**:

      編輯`/etc/network/interfaces`檔案，所以您的 AD 網域控制站的 IP 位址會列示為 dns nameserver。 例如： 

      ```/etc/network/interfaces
      <...>
      # The primary network interface
      auth eth0
      iface eth0 inet dhcp
      dns-nameservers **<AD domain controller IP address>**
      dns-search **<AD domain name>**
      ```

      > [!NOTE]
      > 網路介面 (eth0) 可能會與不同的其他機器。 若要找出您要使用哪一項，執行 ifconfig 並複製有 IP 位址，以及傳輸和接收位元組的介面。

      編輯這個檔案之後, 重新啟動網路服務：

      ```bash
      sudo ifdown eth0 && sudo ifup eth0
      ```

      現在請檢查您`/etc/resolv.conf`檔案包含類似下列一行：  

      ```Code
      nameserver **<AD domain controller IP address>**
      ```

   - **RHEL**:

     編輯`/etc/sysconfig/network-scripts/ifcfg-eth0`檔案 （或其他介面設定檔案依適當情況），讓您的 AD 網域控制站的 IP 位址會列示為 DNS 伺服器：

     ```/etc/sysconfig/network-scripts/ifcfg-eth0
     <...>
     PEERDNS=no
     DNS1=**<AD domain controller IP address>**
     ```

     編輯這個檔案之後, 重新啟動網路服務：

     ```bash
     sudo systemctl restart network
     ```

     現在請檢查您`/etc/resolv.conf`檔案包含類似下列一行：  

     ```Code
     nameserver **<AD domain controller IP address>**
     ```

1. 加入網域

   一旦您已確認您的 DNS 已正確設定，請執行下列命令來加入網域。 您必須使用具有足夠權限，將新電腦加入網域的 AD 中的 AD 帳戶進行驗證。

   具體而言，此命令會在 AD 中建立新的電腦帳戶，請建立`/etc/krb5.keytab`裝載 keytab 檔案和設定網域中的`/etc/sssd/sssd.conf`:

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   <...>
   * Successfully enrolled machine in realm
   ```

   > [!NOTE]
   > 如果您看到錯誤，「 未安裝必要的套件，」 然後您應該安裝使用您的 Linux 散發套件管理員，再執行這些封裝`realm join`命令一次。
   >
   > 如果您收到的錯誤 」 的權限不足，加入網域 」 將需要網域系統管理員檢查您有足夠的權限加入您的網域中的 Linux 機器。
   
   > SQL Server 會使用 SSSD 和 NSS 對應使用者帳戶和群組安全性識別碼 (SID)。 SSSD 必須設定並執行 SQL Server 已成功建立 AD 登入的順序。 Realmd 通常會這樣會自動加入網域的一部分，但在某些情況下您必須分別執行這項操作。
   >
   > 簽出設定下列[SSSD 手動](https://access.redhat.com/articles/3023951)，和[設定才能使用 SSSD NSS](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options)

  
5. 請確認您現在可以收集使用者資訊從網域中，您可以取得 Kerberos 票證來當做該使用者。

   We will use **id**, **[kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)** and **[klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)** commands for this.

   ```bash
   id user@contoso.com
   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM
   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   <...>
   ```

   > [!NOTE]
   > 如果`id user@contoso.com`傳回 「 沒有這類使用者，」 確定 SSSD 服務成功啟動執行命令`sudo systemctl status sssd`。 如果服務正在執行，而且您仍然看到 「 沒有這類使用者 」 錯誤，請嘗試啟用 SSSD 的詳細資訊記錄。 如需詳細資訊，請參閱 Red Hat 文件[疑難排解 SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting)。
   >
   > 如果`kinit user@CONTOSO.COM`傳回時，"KDC 的回覆不符合預期時取得初始認證，"請確定您指定之領域以大寫表示。

如需詳細資訊，請參閱 Red Hat 文件[發掘和聯結的身分識別網域](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html)。 

## <a name="create-ad-user-for-includessnoversionincludesssnoversion-mdmd-and-set-spn"></a>建立 AD 使用者輸入[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]和設定 SPN

  > [!NOTE]
  > 在下一個步驟中，我們將使用您[完整的網域名稱](https://en.wikipedia.org/wiki/Fully_qualified_domain_name)。 如果您在**Azure**，您就必須**[建立一個](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/portal-create-fqdn)**在繼續之前。

1. 在您的網域控制站上執行[New-aduser](https://technet.microsoft.com/library/ee617253.aspx) PowerShell 命令，建立新的 AD 使用者的密碼永久有效。 這個範例會命名帳戶 」"mssql，但帳戶名稱可以是任何您喜歡的項目。 系統會提示您輸入新密碼的帳戶：

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > 它是安全性最佳作法，專用的 AD 帳戶的 SQL Server，以便與其他服務使用相同的帳戶不共用的 SQL Server 認證。 不過，您可以重複使用現有的 AD 帳戶如果您想要的話，如果您知道帳戶的密碼 （需要在下一個步驟中產生 keytab 檔案）。

2. 設定使用此帳戶的 ServicePrincipalName (SPN)`setspn.exe`工具。 SPN 格式必須完全依指定，在下列範例： 您可以找到的完整的網域名稱[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]主機電腦執行`hostname --all-fqdns`上[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]主機和 TCP 連接埠應為 1433年除非您已設定[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用不同的連接埠號碼。

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > 如果您收到 「 存取權限不足，"錯誤，您需要網域系統管理員檢查您有足夠的權限來設定此帳戶的 SPN。
   >
   > 如果您在未來變更的 TCP 連接埠，您將需要再次執行 setspn 命令，使用新的連接埠號碼。 您也必須將新的 SPN 加入 SQL Server 服務 keytab 下一節中的步驟。

3. 如需詳細資訊，請參閱 [註冊 Kerberos 連接的服務主體名稱](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)。

## <a name="configure-includessnoversionincludesssnoversion-mdmd-service-keytab"></a>設定[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]服務 keytab

1. 檢查先前的步驟中建立的 AD 帳戶金鑰的版本號碼 (kvno)。 它通常是 2，但它可能是另一個整數，如果您變更帳戶的密碼多次。 在[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]主機電腦上，執行下列命令：

   ```bash
   kinit user@CONTOSO.COM

   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

2. 建立 AD 使用者，您在上一個步驟中建立的 keytab 檔案。 若要這樣做，我們將使用 **[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)**。 出現提示時，輸入該 AD 帳戶的密碼。

   ```bash
   sudo ktutil

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

   > [!NOTE]
   > Ktutil 工具不會不會驗證的密碼，因此請確定您正確輸入。

3. 此存取的任何人`keytab`檔案可以模擬[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]網域上，因此請確定您的檔案這類限制存取只有`mssql`帳戶具有讀取權限：

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
   sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
   ```

4. 設定[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用這個`keytab`Kerberos 驗證的檔案：

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
   sudo systemctl restart mssql-server
   ```

## <a name="create-ad-based-logins-in-transact-sql"></a>在 TRANSACT-SQL 中建立 AD 為基礎的登入

1. 連接到[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]並建立新的 AD 為基礎的登入：

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

2. 確認登入現在會列示在[sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)系統目錄檢視：

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a name="connect-to-includessnoversionincludesssnoversion-mdmd-using-ad-authentication"></a>連接到[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用 AD 驗證

用戶端電腦使用您的網域認證登入。 現在您可以連接到[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]無需重新輸入您的密碼，利用 AD 驗證。 如果您建立的 AD 群組的登入，該群組的成員任何 AD 使用者可以連線相同的方式。

特定的連接字串參數，用戶端使用 AD 驗證取決於您所使用的驅動程式。 一些範例如下。

* `sqlcmd`已加入網域的 Linux 用戶端上

   登入加入網域的 Linux 用戶端使用`ssh`和您的網域認證：

   ```bash
   ssh -l user@contoso.com client.contoso.com
   ```

   請確定您已安裝[mssql 工具](sql-server-linux-setup-tools.md)封裝，然後使用連接`sqlcmd`未指定任何認證：

   ```bash
   sqlcmd -S mssql.contoso.com
   ```

* 已加入網域的 Windows 用戶端上的 SSMS

   已加入網域的 Windows 用戶端使用網域認證登入。 請確定[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]已安裝，然後連接到您[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]藉由指定的執行個體**Windows 驗證**中**連接到伺服器**對話方塊。

* 使用其他用戶端驅動程式的 AD 驗證

  * JDBC:[使用 Kerberos 整合式驗證來連接 SQL Server](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server)
  * ODBC:[使用整合式的驗證](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)
  * ADO.NET:[連接字串語法](https://msdn.microsoft.com/library/system.data.sqlclient.sqlauthenticationmethod(v=vs.110).aspx)
  
## <a name="next-steps"></a>後續的步驟

在本教學課程中，我們逐步進行作業的方式設定 Active Directory 驗證與 SQL Server on Linux。 您已了解如何以：
> [!div class="checklist"]
> * 加入[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]AD 網域的主機
> * 建立 AD 使用者輸入[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]和設定 SPN
> * 設定[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]服務 keytab
> * 在 TRANSACT-SQL 中建立 AD 為基礎的登入
> * 連接到[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用 AD 驗證

接下來，瀏覽其他安全性案例適用於 SQL Server on Linux。

> [!div class="nextstepaction"]
>[加密連接到 SQL Server on Linux](sql-server-linux-encrypted-connections.md)
