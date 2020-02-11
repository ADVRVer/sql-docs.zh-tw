---
title: 使用加密而不進行驗證 |Microsoft Docs
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], encryption
- cryptography [SQL Server Native Client]
- SQLNCLI, encryption
- encryption [SQL Server Native Client]
- SQL Server Native Client, encryption
ms.assetid: f4c63206-80bb-4d31-84ae-ccfcd563effa
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7805a5bc9d18ab183ba1d741dc4962dd6e6fb196
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73787994"
---
# <a name="using-encryption-without-validation"></a>使用加密而不需驗證
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 一律會加密與登入有關的網路封包。 如果當它啟動時未在伺服器上提供任何憑證，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會產生自行簽署的憑證，該憑證會用來加密登入封包。  

自我簽署憑證不保證安全性。 加密的交握是以 NT LAN Manager （NTLM）為基礎。 強烈建議您在 SQL Server 上布建可驗證的憑證，以提供安全連線。 傳輸安全性層（TLS）只能透過憑證驗證來保護。

應用程式也可要求加密所有網路流量，其方式是使用連接字串關鍵字或連接屬性。 當搭配**IDbInitialize：： Initialize**使用提供者字串時，關鍵字為 "Encrypt OLE DB"，或在搭配使用初始化字串與**IDataInitialize**時，使用 ADO 和 OLE DB 的 "Encryption for Data"。 這也可以透過使用 [ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **強制通訊協定加密**] 選項 Configuration Manager，並將用戶端設定為要求加密的連線。 根據預設，加密連接的所有網路流量會要求在伺服器上提供憑證。 藉由將您的用戶端設定為信任伺服器上的憑證，您可能會容易遭受攔截式攻擊。 如果您在伺服器上部署可驗證的憑證，請務必將 [信任憑證的用戶端設定] 變更為 [FALSE]。

如需連接字串關鍵字的詳細資訊，請參閱搭配[使用連接字串關鍵字與 SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。  
  
 若要在伺服器上尚未佈建憑證時使用加密，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 組態管理員可用來設定 [強制通訊協定加密]**** 和 [信任伺服器憑證]**** 選項。 在此情況下，如果伺服器上未提供任何可驗證的憑證，加密將會使用自行簽署的伺服器憑證，而不需驗證。  
  
 應用程式可能也會使用 "TrustServerCertificate" 關鍵字或它的關聯連接屬性，以便保證加密將會發生。 應用程式設定絕對不會減少 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用戶端組態管理員所設定的安全性層級，但是可能會強化它。 例如，如果未針對用戶端設定 [強制通訊協定加密]****，應用程式可能會自行要求加密。 如果要保證加密，甚至是在尚未提供伺服器憑證時，應用程式可能會要求加密和 "TrustServerCertificate"。 但是，如果用戶端組態中未啟用 "TrustServerCertificate"，仍然需要提供的伺服器憑證。 下表描述所有的案例：  
  
|強制通訊協定加密用戶端設定|信任伺服器憑證用戶端設定|資料的連接字串/連接屬性加密/使用加密|連接字串/連接屬性信任伺服器憑證|結果|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|否|N/A|無 (預設值)|忽略|不發生任何加密。|  
|否|N/A|是|無 (預設值)|只有當有可驗證的伺服器憑證時才會發生加密，否則連接嘗試會失敗。|  
|否|N/A|是|是|加密一定會發生，但是可能會使用自行簽署的伺服器憑證。|  
|是|否|忽略|忽略|只有當有可驗證的伺服器憑證時才會發生加密，否則連接嘗試會失敗。|  
|是|是|無 (預設值)|忽略|加密一定會發生，但是可能會使用自行簽署的伺服器憑證。|  
|是|是|是|無 (預設值)|只有當有可驗證的伺服器憑證時才會發生加密，否則連接嘗試會失敗。|  
|是|是|是|是|加密一定會發生，但是可能會使用自行簽署的伺服器憑證。|  
||||||

> [!CAUTION]
> 上表僅提供不同設定下系統行為的指南。 針對安全連線能力，請確定用戶端和伺服器都需要加密。 此外，請確定伺服器具有可驗證的憑證，且用戶端上的**TrustServerCertificate**設定設定為 FALSE。

## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB 提供者  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者透過新增 SSPROP_INIT_TRUST_SERVER_CERTIFICATE 資料來源初始化屬性（在 DBPROPSET_SQLSERVERDBINIT 屬性集內執行），而不需驗證，即可支援加密。 此外，也已經加入新的連接字串關鍵字 "TrustServerCertificate"。 它可接受 yes 或 no 值；預設值是 no。 當使用服務元件時，它可接受 true 或 false 值；false 是預設值。  
  
 如需 DBPROPSET_SQLSERVERDBINIT 屬性集之增強功能的詳細資訊，請參閱[初始化和授權屬性](../../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC 驅動程式  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驅動程式透過[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)和[SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)函式的新增功能，支援加密而不進行驗證。 已經加入 SQL_COPT_SS_TRUST_SERVER_CERTIFICATE 來接受 SQL_TRUST_SERVER_CERTIFICATE_YES 或 SQL_TRUST_SERVER_CERTIFICATE_NO，預設值為 SQL_TRUST_SERVER_CERTIFICATE_NO。 此外，也已經加入新的連接字串關鍵字 "TrustServerCertificate"。 它可接受 yes 或 no 值；預設值是 "no"。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client 功能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
