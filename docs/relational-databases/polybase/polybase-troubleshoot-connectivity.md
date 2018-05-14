---
title: 對 PolyBase Kerberos 的連線問題進行疑難排解 | Microsoft Docs
author: alazad-msft
ms.author: alazad
manager: craigg
ms.assetid: ''
ms.component: polybase
ms.technology: database
ms.suite: sql
ms.custom: ''
ms.tgt_pltfrm: na
ms.devlang: ''
ms.topic: article
ms.date: 07/19/2017"
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.openlocfilehash: dce5bc3018cb223a8d3c9f0f85aa56c8aba1e4f3
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="troubleshoot-polybase-kerberos-connectivity"></a>對 PolyBase Kerberos 的連線問題進行疑難排解
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
對受 Kerberos 保護的 Hadoop 叢集使用 PolyBase 時，您可以使用 PolyBase 內建的互動式診斷工具，協助對驗證問題進行疑難排解。 

本文章即為指南，會帶您逐步了解利用此工具對這類問題進行偵錯的流程。

## <a name="prerequisites"></a>Prerequisites

1. 安裝具有 PolyBase 的 SQL Server 2016 RTM CU6 / SQL Server 2016 SP1 CU3 / SQL Server 2017 或更新版本
1. 受 Kerberos (Active Directory 或 MIT) 保護的 Hadoop 叢集 (Cloudera 或 Hortonworks)

## <a name="introduction"></a>簡介
這會協助您初步了解 Kerberos 通訊協定的概要。 其中包含三個動作項目：
1. Kerberos 用戶端 (SQL Server)
1. 受保護的資源 (HDFS、MR2、YARN 以及作業記錄等等)
1. 金鑰發佈中心 (在 Active Directory 中稱為網域控制站)

Hadoop 的每個受保護資源皆以唯一**服務主體名稱 (SPN)** 向**金鑰發佈中心 (KDC)** 註冊，這屬於 Hadoop 叢集之 Kerberization 程序的一部份。 目標是要讓用戶端從 KDC 中，針對想要存取的特定 SPN 取得臨時使用者票證 (稱為**票證授權票證 (TGT))**，以要求另一個臨時票證 (稱為**服務票證 (ST))**。  
在 PolyBase 中，針對任何受 Kerberos 保護的資源要求驗證時，會發生下列四趟來回行程交握：
1. SQL Server 連線至 KDC，並為使用者取得 TGT。 KDC 的私密金鑰會用來為 TGT 加密。
1. SQL Server 呼叫 Hadoop 的受保護資源 (例如 HDFS)，並判斷需要 ST 的 SPN。
1. SQL Server 回到 KDC，並傳回 TGT，然後要求 ST 以存取該特定的受保護資源。 受保護服務的私密金鑰會用來為 ST 加密。
1. SQL Server 將 ST 轉送至 Hadoop，並完成驗證以對該服務建立工作階段。

![](./media/polybase-sqlserver.png)

驗證問題會歸類至一或多個上述步驟中。 為了協助加快偵錯流程，PolyBase 引入了整合式診斷工具，能夠協助識別失敗點。

## <a name="troubleshooting"></a>疑難排解
PolyBase 具備多個組態 XML，這些 XML 包含 Hadoop 叢集的屬性。 亦即下列檔案：
- core-site.xml
- hdfs-site.xml
- hive-site.xml
- jaas.conf
- mapred-site.xml
- yarn-site.xml

這些檔案位於：

\\[系統磁碟機\\]:{安裝路徑}\\{執行個體}\\{名稱}\\MSSQL\\Binn\\Polybase\\Hadoop\\conf

舉例來說，SQL Server 2016 的預設位置即為 "C:\\Program Files\\Microsoft SQL Server\\MSSQL13.MSSQLSERVER\\MSSQL\\Binn\\Polybase\\Hadoop\\conf"。

使用下列三個依據環境設定值的屬性，更新 PolyBase 組態檔之一的 **core-site.xml**：
```xml
<property>
    <name>polybase.kerberos.realm</name>
    <value>CONTOSO.COM</value>
</property>
<property>
    <name>polybase.kerberos.kdchost</name>
    <value>kerberos.contoso.com</value>
</property>
<property>
    <name>hadoop.security.authentication</name>
    <value>KERBEROS</value>
</property>
```
若要進行下推作業，之後也必須更新其他 XML，不過只要有設定此檔案，至少就能夠存取 HDFS 檔案系統。

因為此工具獨立於 SQL Server 之外執行，所以若是更新了組態 XML，也不必執行或是重新啟動此工具。 若要執行此工具，請在安裝 SQL Server 的主機上執行下列命令：

```
> cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase  
> java -classpath ".\Hadoop\conf;.\Hadoop\*;.\Hadoop\HDP2_2\*" com.microsoft.polybase.client.HdfsBridge {Name Node Address} {Name Node Port} {Service Principal} {Filepath containing Service Principal's Password} {Remote HDFS file path (optional)}
```

## <a name="arguments"></a>引數
| 引數 | 描述|
| --- | --- |
| *Name Node Address* | 名稱節點的 IP 或 FQDN。 也就是 CREATE EXTERNAL DATA SOURCE T-SQL 中的 "LOCATION" 引數。|
| *Name Node Port* | 名稱節點的連接埠。 也就是 CREATE EXTERNAL DATA SOURCE T-SQL 中的 "LOCATION" 引數。 這通常是 8020。 |
| *Service Principal* | KDC 的管理服務主體。 這應該要與您在 CREATE DATABASE SCOPED CREDENTIAL T-SQL 的 "IDENTITY" 引數中使用的值相符。|
| *Service Password* | 將密碼儲存在檔案中，並將檔案路徑傳遞至此處，而不在主控台鍵入密碼。 檔案內容應該要與您在 CREATE DATABASE SCOPED CREDENTIAL T-SQL 的 "SECRET" 引數中使用的值相符。 |
| *遠端 HDFS 檔案路徑 (選擇性) * | 所要存取之現有檔案的路徑。 若未指定，將會使用根 "/"。 |

## <a name="example"></a>範例
```dos
java -classpath ".\Hadoop\conf;.\Hadoop\*;.\Hadoop\HDP2_2\*" com.microsoft.polybase.client.HdfsBridge 10.193.27.232 8020 admin_user C:\temp\kerberos_pass.txt
```
輸出是增強型偵錯的詳細資訊，但不論您使用 MIT 或 AD，都只能尋找四個主要檢查點。 這四個檢查點會對應到上述的四項步驟。 

下列摘要來自 MIT KDC。 您可以於文章結尾處的參考中，參考 MIT 及 AD 的完整範例輸出。

## <a name="checkpoint-1"></a>檢查點 1
應該要有 Server Principal = krbtgt/*MYREALM.COM@MYREALM.COM* 的票證十六進位傾印。 這表示 SQL Server 已成功對 KDC 進行驗證，並已收到 TGT。 如果沒有，表示問題僅發生在 SQL Server 與 KDC 之間，而非 Hadoop。

PolyBase **不**支援 AD 與 MIT 之間的信任關係，而且必須針對 Hadoop 叢集中設定的相同 KDC 進行設定。 在這類環境中，在該 KDC 上手動建立服務帳戶，並加以執行驗證是可行的。
```dos
|>>> KrbAsReq creating message 
 >>> KrbKdcReq send: kdc=kerberos.contoso.com UDP:88, timeout=30000, number of retries =3, #bytes=143 
 >>> KDCCommunication: kdc=kerberos.contoso.com UDP:88, timeout=30000,Attempt =1, #bytes=143 
 >>> KrbKdcReq send: #bytes read=646 
 >>> KdcAccessibility: remove kerberos.contoso.com 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 >>> KrbAsRep cons in KrbAsReq.getReply myuser 
 [2017-04-25 21:34:33,548] INFO 687[main] - com.microsoft.polybase.client.KerberosSecureLogin.secureLogin(KerberosSecureLogin.java:97) - Subject: 
 Principal: admin_user@CONTOSO.COM 
 Private Credential: Ticket (hex) = 
 0000: 61 82 01 48 30 82 01 44 A0 03 02 01 05 A1 0E 1B a..H0..D........ 
 0010: 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D A2 21 30 .CONTOSO.COM.!0 
 0020: 1F A0 03 02 01 02 A1 18 30 16 1B 06 6B 72 62 74 ........0...krbt 
 0030: 67 74 1B 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D gt..CONTOSO.COM 
 0040: A3 82 01 08 30 82 01 04 A0 03 02 01 10 A1 03 02 ....0........... 
 *[…Condensed…]* 
 0140: 67 6D F6 41 6C EB E0 C3 3A B2 BD B1 gm.Al...:... 
 Client Principal = admin_user@CONTOSO.COM 
 Server Principal = krbtgt/CONTOSO.COM@CONTOSO.COM 
 *[…Condensed…]* 
 [2017-04-25 21:34:34,500] INFO 1639[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1579) - Successfully authenticated against KDC server. 
```
## <a name="checkpoint-2"></a>檢查點 2
PolyBase 將會嘗試存取 HDFS，但因為要求未包含必要的服務票證而失敗。
```dos
 [2017-04-25 21:34:34,501] INFO 1640[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1584) - Attempting to access external filesystem at URI: hdfs://10.193.27.232:8020 
 Found ticket for admin_user@CONTOSO.COM to go to krbtgt/CONTOSO.COM@CONTOSO.COM expiring on Wed Apr 26 21:34:33 UTC 2017 
 Entered Krb5Context.initSecContext with state=STATE_NEW 
 Found ticket for admin_user@CONTOSO.COM to go to krbtgt/CONTOSO.COM@CONTOSO.COM expiring on Wed Apr 26 21:34:33 UTC 2017 
 Service ticket not found in the subject 
```
## <a name="checkpoint-3"></a>檢查點 3
第二個十六進位傾印表示 SQL Server 已成功使用 TGT，並從 KDC 取得了名稱節點的 SPN 適用的服務票證。
```dos
 >>> KrbKdcReq send: kdc=kerberos.contoso.com UDP:88, timeout=30000, number of retries =3, #bytes=664 
 >>> KDCCommunication: kdc=kerberos.contoso.com UDP:88, timeout=30000,Attempt =1, #bytes=664 
 >>> KrbKdcReq send: #bytes read=669 
 >>> KdcAccessibility: remove kerberos.contoso.com 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 >>> KrbApReq: APOptions are 00100000 00000000 00000000 00000000 
 >>> EType: sun.security.krb5.internal.crypto.Des3CbcHmacSha1KdEType 
 Krb5Context setting mySeqNumber to: 1033039363 
 Created InitSecContextToken: 
 0000: 01 00 6E 82 02 4B 30 82 02 47 A0 03 02 01 05 A1 ..n..K0..G...... 
 0010: 03 02 01 0E A2 07 03 05 00 20 00 00 00 A3 82 01 ......... ...... 
 0020: 63 61 82 01 5F 30 82 01 5B A0 03 02 01 05 A1 0E ca.._0..[....... 
 0030: 1B 0C 41 50 53 48 44 50 4D 53 2E 43 4F 4D A2 26 ..CONTOSO.COM.& 
 0040: 30 24 A0 03 02 01 00 A1 1D 30 1B 1B 02 6E 6E 1B 0$.......0...nn. 
 0050: 15 73 68 61 73 74 61 2D 68 64 70 32 35 2D 30 30 .hadoop-hdp25-00 
 0060: 2E 6C 6F 63 61 6C A3 82 01 1A 30 82 01 16 A0 03 .local....0..... 
 0070: 02 01 10 A1 03 02 01 01 A2 82 01 08 04 82 01 04 ................ 
 *[…Condensed…]* 
 0240: 03 E3 68 72 C4 D2 8D C2 8A 63 52 1F AE 26 B6 88 ..hr.....cR..&.. 
 0250: C4 . 
```
## <a name="checkpoint-4"></a>檢查點 4
最後，應將目標路徑的檔案內容與確認訊息一同印出。 這表示 Hadoop 已使用 ST 驗證 SQL Server，而且受保護資源的存取權已授與工作階段。

達到此檢查點即可確認：(i) 前述的三個動作項目皆能正確地進行通訊，(ii) core-site.xml 及 jaas.conf 皆正確，(iii) KDC 能夠辨識您的認證。
```dos
 [2017-04-25 21:34:35,096] INFO 2235[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1586) - File properties for "/": FileStatus{path=hdfs://10.193.27.232:8020/; isDirectory=true; modification_time=1492028259862; access_time=0; owner=hdfs; group=hdfs; permission=rwxr-xr-x; isSymlink=false} 
 [2017-04-25 21:34:35,098] INFO 2237[main] - com.microsoft.polybase.client.HdfsBridge.main(HdfsBridge.java:1587) - Successfully accessed the external file system. 
```
## <a name="common-errors"></a>常見錯誤
若已執行工具，但是卻「未」列印目標路徑的檔案屬性 (檢查點 4)，則會在中途擲回例外狀況。 請檢閱例外狀況，並細想在這四個步驟的流程中，是哪個環節的內容出了問題。 請依序思考下列可能發生的常見問題：
| 例外狀況及訊息 | 原因 | 
| --- | --- |
| org.apache.hadoop.security.AccessControlException<br>未啟用簡單驗證。 可用項目：[TOKEN, KERBEROS] | 未將 core-site.xml 的 hadoop.security.authentication 屬性設定為 "KERBEROS"。|
|javax.security.auth.login.LoginException<br>在 Kerberos 資料庫中找不到用戶端 (6) - CLIENT_NOT_FOUND |    在 core-site.xml 中指定的領域沒有提供的管理服務主體。|
| javax.security.auth.login.LoginException<br> 總和檢查碼失敗 |    管理服務主體存在，但是密碼不正確。 |
| 原生組態名稱：C:\Windows\krb5.ini<br>從原生組態載入 | 這不是例外狀況，但是表示 Java 的 krb5LoginModule 在您的電腦上偵測到自訂用戶端組態。 請檢查您的用戶端設定，因為這可能就是造成問題的原因。 |
| javax.security.auth.login.LoginException<br>java.lang.IllegalArgumentException<br>不合法的主體名稱 admin_user@CONTOSO.COM: org.apache.hadoop.security.authentication.util.KerberosName$NoMatchingRule：未將任何規則套用至 admin_user@CONTOSO.COM | 對每個 Hadoop 叢集，依照適當規則將屬性 “hadoop.security.auth_to_local” 新增至 core-site.xml。 |
| java.net.ConnectException<br>嘗試存取位於 URI hdfs://10.193.27.230:8020 的外部檔案系統<br>發生連線例外狀況，導致從 IAAS16981207/10.107.0.245 對 10.193.27.230:8020 呼叫失敗 | 針對 KDC 的驗證已成功，但是無法存取 Hadoop 名稱節點。 請檢查名稱節點 IP 及連接埠。 請驗證已在 Hadoop 上停用防火牆。 |
| java.io.FileNotFoundException<br>檔案不存在：/test/data.csv |    驗證已成功，但是指定的位置不存在。 請先檢查路徑，或先以根 "/" 測試。 |
## <a name="debugging-tips"></a>偵錯提示
### <a name="mit-kdc"></a>MIT KDC  
您可以在 KDC 主機或任何已設定的 KDC 用戶端上，執行 **kadmin.local** > (管理員登入) >**listprincs**，以檢視所有已向 KDC 註冊的 SPN (包含管理員在內)。 若已正確地將 Hadoop 叢集 Kerberos 化，叢集中為數眾多的每項服務都應該各有一個可用的 SPN (例如 nn、dn、rm、yarn、spnego 等等)根據預設，可以在 **/etc/security/keytabs** 找到這些 SPN 的對應 keytab 檔案 (密碼替代)。 KDC 的私密金鑰會用來為其加密。  

此外，也請考慮使用 [kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html) 工具在本機驗證 KDC 上的管理員認證。 範例使用方式為：*kinit identity@MYREALM.COM*。 如果出現輸入密碼的提示即表示身分識別存在。  
根據預設，KDC 記錄會位在 **/var/log/krb5kdc.log**，其中包括為票證提出的所有要求，包括提出該要求的用戶端 IP。 應該會有兩個要求，來自該工具執行所在的 SQL Server 電腦 IP：首先是驗證伺服器對 TGT 的要求 - **AS\_REQ**，其次是票證授與伺服器對 ST 的要求 - **TGS\_REQ**。
```bash
 [root@MY-KDC log]# tail -2 /var/log/krb5kdc.log 
 May 09 09:48:26 MY-KDC.local krb5kdc[2547](info): **AS_REQ** (3 etypes {17 16 23}) 10.107.0.245: ISSUE: authtime 1494348506, etypes {rep=16 tkt=16 ses=16}, admin_user@CONTOSO.COM for **krbtgt/CONTOSO.COM@CONTOSO.COM** 
 May 09 09:48:29 MY-KDC.local krb5kdc[2547](info): **TGS_REQ** (3 etypes {17 16 23}) 10.107.0.245: ISSUE: authtime 1494348506, etypes {rep=16 tkt=16 ses=16}, admin_user@CONTOSO.COM for **nn/hadoop-hdp25-00.local@CONTOSO.COM** 
```
### <a name="active-directory"></a>Active Directory 
在 Active Directory 中，您可以瀏覽至 [控制台] > [Active Directory 使用者和電腦] > *MyRealm* > *MyOrganizationalUnit*，以檢視 SPN。 若已正確地將 Hadoop 叢集 Kerberos 化，叢集中為數眾多的每項服務都應該各有一個可用的 SPN (例如 nn、dn、rm、yarn、spnego 等等)

## <a name="see-also"></a>另請參閱
[使用 Active Directory 驗證整合 PolyBase 與 Cloudera](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/10/17/integrating-polybase-with-cloudera-using-active-directory-authentication)  
[Cloudera 的 CDH Kerberos 設定指南](https://www.cloudera.com/documentation/enterprise/5-6-x/topics/cm_sg_principal_keytab.html)  
[Hortonworks 的 HDP Kerberos 設定指南](https://docs.hortonworks.com/HDPDocuments/Ambari-2.2.0.0/bk_Ambari_Security_Guide/content/ch_configuring_amb_hdp_for_kerberos.html)  
[Polybase 疑難排解](polybase-troubleshooting.md)


