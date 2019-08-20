---
title: JDBC 驅動程式的 Always Encrypted API 參考 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6962a2aa-9508-4d4f-a78c-905e2bc68615
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 79cf8ce1b951621d58105d18b847306ff620d114
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028479"
---
# <a name="always-encrypted-api-reference-for-the-jdbc-driver"></a>JDBC 驅動程式的 Always Encrypted API 參考
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  一律加密可讓用戶端將用戶端應用程式內的機密資料進行加密，且永遠不會顯示 SQL Server 的加密金鑰。 安裝在用戶端電腦上且啟用 Always Encrypted 的驅動程式，透過自動將 SQL Server 用戶端應用程式中的敏感性資料加密與解密，進而達到此功能。 驅動程式會先將敏感資料行中的資料進行加密，才會將資料傳遞至 SQL Server，並自動重寫查詢以保留應用程式的語意。 同樣地，驅動程式會以透明的方式，將查詢結果中加密資料庫資料行所儲存的資料解密。 如需詳細資訊, 請參閱[Always Encrypted (資料庫引擎)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)和搭配[使用 Always Encrypted 與 JDBC 驅動程式](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)。  
  
> [!NOTE]  
>  只有搭載 SQL Server 2016 且適用於 SQL Server 的 Microsoft JDBC Driver 6.0 或更高版本才支援 Always Encrypted。  
  
 ## <a name="always-encrypted-api-references"></a>Always Encrypted API 參考
 
 針對使用一律加密的用戶端應用程式所用，JDBC 驅動程式 API 有幾項新項目及修改項目。  
  
 **SQLServerConnection 類別**  
  
|名稱|描述|  
|----------|-----------------|  
|新的連接字串關鍵字：<br /><br /> columnEncryptionSetting|columnEncryptionSetting=Enabled 會啟用連線的 Always Encrypted 功能，而 columnEncryptionSetting=Disabled 會予以停用。 接受的值為 Enabled/Disabled。 預設值為 Disabled。|  
|新方法：<br /><br /> `public static void setColumnEncryptionTrustedMasterKeyPaths(Map<String, List\<String>> trustedKeyPaths)`<br /><br /> `public static void updateColumnEncryptionTrustedMasterKeyPaths(String server, List\<String> trustedKeyPaths)`<br /><br /> `public static void removeColumnEncryptionTrustedMasterKeyPaths(String server)`|可讓您為資料庫伺服器設定/更新/移除受信任的金鑰路徑清單。 如果驅動程式在處理應用程式查詢時接收到不在清單上的金鑰路徑，則查詢會失敗。 此屬性會針對受到安全性攻擊危害的 SQL Server 提供額外的保護，這類 SQL Server 會傳送假的金鑰路徑，而可能會導致遺漏金鑰存放區認證。|  
|新方法：<br /><br /> `public static Map<String, List\<String>> getColumnEncryptionTrustedMasterKeyPaths()`|會傳回資料庫伺服器的受信任金鑰路徑清單。|  
|新方法：<br /><br /> `public static void registerColumnEncryptionKeyStoreProviders (Map\<String, SQLServerColumnEncryptionKeyStoreProvider> clientKeyStoreProviders)`|可讓您註冊自訂金鑰存放區提供者。 它是一個字典，會將金鑰存放區提供者名稱對應至金鑰存放區提供者實作。<br /><br /> 若要使用 JVM 金鑰存放區，您需要使用 JVM 金鑰存放區認證將 SQLServerColumnEncryptionJVMKeyStoreProvider 物件具現化，並向驅動程式註冊它。 此提供者的名稱必須是 'MSSQL_JVM_KEYSTORE'。<br /><br /> 若要使用 Azure Key Vault 存放區, 您必須具現化 SQLServerColumnEncryptionAzureKeyStoreProvider 物件, 並向驅動程式註冊它。 此提供者的名稱必須是 ' AZURE_KEY_VAULT '。|
|`public final boolean getSendTimeAsDatetime()`|傳回 sendTimeAsDatetime 連接屬性的設定。|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)`|修改 sendTimeAsDatetime 連接屬性的設定。|

 **SQLServerConnectionPoolProxy 類別**
 
|名稱|描述|  
|----------|-----------------|  
|`public final boolean getSendTimeAsDatetime()` | 傳回 sendTimeAsDatetime 連接屬性的設定。|
|`public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)` | 修改 sendTimeAsDatetime 連接屬性的設定。|
     
  
 **SQLServerDataSource 類別**  
  
|名稱|描述|  
|----------|-----------------|  
|`public void setColumnEncryptionSetting(String columnEncryptionSetting)`|啟用/停用資料來源物件的一律加密功能。<br /><br /> 預設值為 Disabled。|  
|`public String getColumnEncryptionSetting()`|擷取資料來源物件的一律加密功能設定。|
|`public void setKeyStoreAuthentication(String keyStoreAuthentication)`|設定可識別金鑰存放區的名稱。 只有支援的值是用來識別 JAVA 金鑰存放區的**JAVAKeyStorePassword** 。<br/><br/>預設值是 null。|
|`public String getKeyStoreAuthentication()`|取得資料來源物件的 keyStoreAuthentication 設定值。|
|`public void setKeyStoreSecret(String keyStoreSecret)`|設定 JAVA 金鑰存放區的密碼。 金鑰存放區和金鑰的密碼必須相同。 請注意, keyStoreAuthentication 必須使用**JAVAKeyStorePassword**來設定。|
|`public void setKeyStoreLocation(String keyStoreLocation)`|設定位置, 包括 JAVA 金鑰儲存區的檔案名。 請注意, keyStoreAuthentication 必須使用**JAVAKeyStorePassword**來設定。|
|`public String getKeyStoreLocation()`|抓取 JAVA 金鑰存放區的 keyStoreLocation。|
  
 **SQLServerColumnEncryptionJavaKeyStoreProvider 類別**  
  
 Java 金鑰存放區的金鑰存放區提供者實作。 此類別可讓您將儲存在 Java 金鑰存放區中的憑證，當成資料行主要金鑰使用。  
  
 建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionJavaKeyStoreProvider (String keyStoreLocation, char[] keyStoreSecret)`|JAVA 金鑰存放區的金鑰存放區提供者。|  
  
 方法  
  
|名稱|描述|  
|----------|-----------------|  
|`public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)`|將資料行加密金鑰的指定加密值解密。 加密的值必須使用具指定金鑰路徑的憑證，以及指定的演算法，進而加以加密。<br /><br /> **金鑰路徑的格式應為下列其中一項：**<br /><br /> 憑證指紋：<certificate_thumbprint><br /><br /> 別名：<certificate_alias><br /><br /> 覆寫 SQLServerColumnEncryptionKeyStoreProvider。 decryptColumnEncryptionKey(String, String, Byte[])。)|  
|`public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)`|使用具指定金鑰路徑的憑證，以及指定的演算法，將資料行加密金鑰加密。<br /><br /> **金鑰路徑的格式應為下列其中一項：**<br /><br /> 憑證指紋：<certificate_thumbprint><br /><br /> 別名：<certificate_alias><br /><br /> 覆寫 SQLServerColumnEncryptionKeyStoreProvider。 encryptColumnEncryptionKey(String, String, Byte[])。)|  
|`public void setName (String name)`|設定此金鑰存放區提供者的名稱。|
|`public String getName ()`|取得此金鑰存放區提供者的名稱。|
  
 **SQLServerColumnEncryptionAzureKeyVaultProvider 類別**  
  
 Azure Key Vault 的金鑰存放區提供者實作。 此類別可讓您使用儲存在 Azure Key Vault 中的金鑰做為資料行主要金鑰。  
  
 建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`public SQLServerColumnEncryptionAzureKeyVaultProvider (String clientId, String clientKey)`|Azure Key Vault 的金鑰存放區提供者。  您必須提供識別碼和要求權杖的用戶端金鑰, 以向 Azure Key Vault 進行驗證。|  
  
 方法  
  
|名稱|描述|  
|----------|-----------------|  
| `public byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)` | Decryptes 加密的資料行加密金鑰 (CEK)。 透過使用主要金鑰路徑所指定之非對稱金鑰的 RSA 加密演算法, 即可完成這項解密。<br />覆寫 SQLServerColumnEncryptionKeyStoreProvider。 decryptColumnEncryptionKey(String, String, Byte[])。) |  
| `public byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[] columnEncryptionKey)` | 將指定的資料行主要金鑰提供給指定的演算法, 以加密資料行加密金鑰。<br />覆寫 SQLServerColumnEncryptionKeyStoreProvider。 encryptColumnEncryptionKey(String, String, Byte[])。) |  
|`public void setName (String name)`|設定此金鑰存放區提供者的名稱。|
|`public String getName ()`|取得此金鑰存放區提供者的名稱。|  
  
  
 **SQLServerKeyVaultAuthenticationCallback 介面**  
  
 此介面包含一個方法, 可供使用者執行 Azure Key Vault 驗證。  
  
 方法  
  
|名稱|描述|  
|----------|-----------------|  
|`public String getAccessToken(String authority, String resource, String scope);`|需要覆寫方法。 方法是用來取得 Azure Key Vault 的存取權杖。|  
  
 **SQLServerColumnEncryptionKeyStoreProvider 類別**  
  
 擴充此類別來實作自訂金鑰存放區提供者。  
  
|名稱|描述|  
|----------|-----------------|  
|SQLServerColumnEncryptionKeyStoreProvider|所有金鑰存放區提供者的基底類別。 自訂提供者必須衍生自此類別並覆寫其成員函式，然後使用 SQLServerConnection 予以註冊。 Sqlserverconnection.registercolumnencryptionkeystoreproviders ()。|  
  
 方法  
  
|名稱|描述|  
|----------|-----------------|  
|`public abstract byte[] decryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte [] encryptedColumnEncryptionKey)`|用來將資料行加密金鑰的指定加密值解密的基底類別方法。 加密的值必須使用具有指定金鑰路徑的資料行主要金鑰和指定的演算法，進而加以加密。|  
|`public abstract byte[] encryptColumnEncryptionKey (String masterKeyPath, String encryptionAlgorithm, byte[]  columnEncryptionKey)`|基底類別方法，使用具指定金鑰路徑的資料行主要金鑰，以及指定的演算法，進而將資料加密金鑰加密。|
|`public abstract void setName(String name)`|設定此金鑰存放區提供者的名稱。|
|`public abstract String getName()`|取得此金鑰存放區提供者的名稱。|  
  
 **SQLServerPreparedStatement**類別中的新或多載方法  
  
|名稱|描述|  
|----------|-----------------|  
|`public void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale)`<br /><br /> `public void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale)`<br /><br /> `public void setTime(int parameterIndex, java.sql.Time x, int scale)`<br /><br /> `public void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale)` <br />`public void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale)`|這些方法會以有效位數或小數位數引數或兩者來進行多載, 以支援針對需要有效位數和小數位數資訊的特定資料類型 Always Encrypted。|  
|`public void setMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setSmallMoney(int parameterIndex, BigDecimal x)`<br /><br /> `public void setUniqueIdentifier(int parameterIndex, String guid)`<br /><br /> `public void setDateTime(int parameterIndex, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(int parameterIndex, java.sql.Timestamp x)`|新增這些方法, 以支援 money、smallmoney、uniqueidentifier、datetime 和 Smalldatetime 資料類型的 Always Encrypted。 <br/><br/>請注意, 現有`setTimestamp()`的方法會用來將參數值傳送至已加密的 datetime2 資料行。 針對 encrypted datetime 和 Smalldatetime 資料行, 分別使用`setDateTime()`新`setSmallDateTime()`的方法和。|  
|`public final void setBigDecimal(int parameterIndex, BigDecimal x, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setSmallMoney(int parameterIndex, BigDecimal x, boolean forceEncrypt)`<br /><br /> `public final void setBoolean(int parameterIndex, boolean x, boolean forceEncrypt)`<br /><br /> `public final void setByte(int parameterIndex, byte x, boolean forceEncrypt)`<br /><br /> `public final void setBytes(int parameterIndex, byte x[], boolean forceEncrypt)`<br /><br /> `public final void setUniqueIdentifier(int parameterIndex, String guid, boolean forceEncrypt)`<br /><br /> `public final void setDouble(int parameterIndex, double x, boolean forceEncrypt)`<br /><br /> `public final void setFloat(int parameterIndex, float x, boolean forceEncrypt)`<br /><br /> `public final void setInt(int parameterIndex, int value, boolean forceEncrypt)`<br /><br /> `public final void setLong(int parameterIndex, long x, boolean forceEncrypt)`<br /><br /> `public final setObject(int parameterIndex, Object x, int targetSqlType, Integer precision, int scale, boolean forceEncrypt)`<br /><br /> `public final void setObject(int parameterIndex, Object x, SQLType targetSqlType, Integer precision, Integer scale, boolean forceEncrypt)`<br /><br /> `public final void setShort(int parameterIndex, short x, boolean forceEncrypt)`<br /><br /> `public final void setString(int parameterIndex, String str, boolean forceEncrypt)`<br /><br /> `public final void setNString(int parameterIndex, String value, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTimeOffset(int parameterIndex, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`<br /><br /> `public final void setDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setSmallDateTime(int parameterIndex, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public final void setDate(int parameterIndex, java.sql.Date x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTime(int parameterIndex, java.sql.Time x, java.util.Calendar cal, boolean forceEncrypt)`<br /><br /> `public final void setTimestamp(int parameterIndex, java.sql.Timestamp x, java.util.Calendar cal, boolean forceEncrypt)`|將指定的參數設定為指定的 Java 值。<br /><br /> 如果布林值 forceEncrypt 設定為 true, 則只有在指定資料行已加密, 而且在連接或語句上啟用 Always Encrypted 時, 才會設定查詢參數。<br /><br /> 如果布林值 forceEncrypt 設定為 false, 驅動程式將不會強制加密參數。|  
  
 **SQLServerCallableStatement**類別中的新或多載方法  
  
|名稱|描述|  
|----------|-----------------|  
|`public void registerOutParameter(int parameterIndex, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(int parameterIndex, SQLType sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, int sqlType, int precision, int scale)`<br /><br /> `public void registerOutParameter(String parameterName, SQLType sqlType, int precision, int scale)`<br />`public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale)`<br/><br/>`public final void setObject(String sCol, Object x, int targetSqlType, Integer precision, int scale)`|這些方法會以有效位數或小數位數引數或兩者來進行多載, 以支援針對需要有效位數和小數位數資訊的特定資料類型 Always Encrypted。|  
|`public void setDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid)`<br /><br /> `public void setMoney(String parameterName, BigDecimal bd)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd)`<br/><br/>`public Timestamp getDateTime(int index)`<br/><br/>`public Timestamp getDateTime(String sCol)`<br/><br/>`public Timestamp getDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(int index)`<br/><br/>`public Timestamp getSmallDateTime(String sCol)`<br/><br/>`public Timestamp getSmallDateTime(int index, Calendar cal)`<br/><br/>`public Timestamp getSmallDateTime(String name, Calendar cal)`<br/><br/>`public BigDecimal getMoney(int index)`<br/><br/>`public BigDecimal getMoney(String sCol)`<br/><br/>`public BigDecimal getSmallMoney(int index)`<br/><br/>`public BigDecimal getSmallMoney(String sCol)`|新增這些方法, 以支援 money、smallmoney、uniqueidentifier、datetime 和 Smalldatetime 資料類型的 Always Encrypted。 <br/><br/>請注意, 現有`setTimestamp()`的方法會用來將參數值傳送至已加密的 datetime2 資料行。 針對 encrypted datetime 和 Smalldatetime 資料行, 分別使用`setDateTime()`新`setSmallDateTime()`的方法和。|  
|`public void setObject(String parameterName, Object o, int n, int m, boolean forceEncrypt)`<br /><br /> `public void setObject(String parameterName, Object obj, SQLType jdbcType, int scale, boolean forceEncrypt)`<br /><br /> `public void setDate(String parameterName, java.sql.Date x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTime(String parameterName, java.sql.Time x, Calendar c, boolean forceEncrypt)`<br /><br /> `public void setDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setDateTimeOffset(String parameterName, microsoft.sql.DateTimeOffset t, int scale, boolean forceEncrypt)`<br /><br /> `public void setSmallDateTime(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp t, int scale, boolean forceEncrypt)`<br /><br /> `public void setTimestamp(String parameterName, java.sql.Timestamp x, boolean forceEncrypt)`<br /><br /> `public void setUniqueIdentifier(String parameterName, String guid, boolean forceEncrypt)`<br /><br /> `public void setBytes(String parameterName, byte[] b, boolean forceEncrypt)`<br /><br /> `public void setByte(String parameterName, byte b, boolean forceEncrypt)`<br /><br /> `public void setString(String parameterName, String s, boolean forceEncrypt)`<br /><br /> `public final void setNString(String parameterName, String value, boolean forceEncrypt)<br /><br /> public void setMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setSmallMoney(String parameterName, BigDecimal bd, boolean forceEncrypt)`<br /><br /> `public void setBigDecimal(String parameterName, BigDecimal bd, int precision, int scale, boolean forceEncrypt)`<br /><br /> `public void setDouble(String parameterName, double d, boolean forceEncrypt)`<br /><br /> `public void setFloat(String parameterName, float f, boolean forceEncrypt)`<br /><br /> `public void setInt(String parameterName, int i, boolean forceEncrypt)`<br /><br /> `public void setLong(String parameterName, long l, boolean forceEncrypt)`<br /><br /> `public void setShort(String parameterName, short s, boolean forceEncrypt)`<br /><br /> `public void setBoolean(String parameterNames, boolean b, boolean forceEncrypt)`<br/><br/>`public void setTimeStamp(String sCol, java.sql.Timestamp x, Calendar c, Boolean forceEncrypt)`|將指定的參數設定為指定的 Java 值。<br /><br /> 如果布林值 forceEncrypt 設定為 true, 則只有在指定資料行已加密, 而且在連接或語句上啟用 Always Encrypted 時, 才會設定查詢參數。<br /><br /> 如果布林值 forceEncrypt 設定為 false, 驅動程式將不會強制加密參數。|
 

 **SQLServerResultSet**類別中的新或多載方法  
  
|名稱|描述|  
|----------|-----------------|  
|`public String getUniqueIdentifier(int columnIndex)`<br/><br/>`public String getUniqueIdentifier(String columnLabel)`<br/><br/>   `public java.sql.Timestamp getDateTime(int columnIndex)` <br/><br/> `public java.sql.Timestamp getDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getDateTime(int columnIndex, Calendar cal)`   <br/><br/>`public java.sql.Timestamp getDateTime(String colName, Calendar cal)`    <br/><br/>`public java.sql.Timestamp getSmallDateTime(int columnIndex)`    <br/><br/> `public java.sql.Timestamp getSmallDateTime(String columnName)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(int columnIndex, Calendar cal)`   <br/><br/> `public java.sql.Timestamp getSmallDateTime(String colName, Calendar cal)`   <br/><br/>  `public BigDecimal getMoney(int columnIndex)`  <br/><br/> `public BigDecimal getMoney(String columnName)`   <br/><br/> `public BigDecimal getSmallMoney(int columnIndex)`   <br/><br/>  `public BigDecimal getSmallMoney(String columnName)`  <br/><br/>`public void updateMoney(String columnName, BigDecimal x)`    <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x)`  <br/><br/>     `public void updateDateTime(int index, java.sql.Timestamp x)` <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x)` |新增這些方法, 以支援 money、smallmoney、uniqueidentifier、datetime 和 Smalldatetime 資料類型的 Always Encrypted。 <br/><br/>請注意, 現有`updateTimestamp()`的方法會用來更新加密的 datetime2 資料行。 針對 encrypted datetime 和 Smalldatetime 資料行, 分別使用`updateDateTime()`新`updateSmallDateTime()`的方法和。|
|`public void updateBoolean(int index, boolean x, boolean forceEncrypt)`  <br/><br/>  `public void updateByte(int index, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(int index, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(int index, int x, boolean forceEncrypt)`   <br/><br/>  `public void updateLong(int index, long x, boolean forceEncrypt)`  <br/><br/> `public void updateFloat(int index, float x, boolean forceEncrypt)`   <br/><br/> `public void updateDouble(int index, double x, boolean forceEncrypt)`   <br/><br/> `public void updateMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateSmallMoney(int index, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallMoney(String columnName, BigDecimal x, boolean forceEncrypt)`  <br/><br/> `public void updateBigDecimal(int index, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateString(int columnIndex, String stringValue, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(int columnIndex, String nString, boolean forceEncrypt)`  <br/><br/>  `public void updateNString(String columnLabel, String nString, boolean forceEncrypt)`  <br/><br/> `public void updateBytes(int index, byte x[], boolean forceEncrypt)   <br/><br/>  public void updateDate(int index, java.sql.Date x, boolean forceEncrypt)`  <br/><br/> `public void updateTime(int index, java.sql.Time x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateTimestamp(int index, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/> `public void updateDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/> `public void updateSmallDateTime(int index, java.sql.Timestamp x, Integer scale, boolean forceEncrypt)`   <br/><br/>  `public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateUniqueIdentifier(int index, String x, boolean forceEncrypt)`    <br/><br/>  `public void updateObject(int index, Object x, int precision, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateObject(int index, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateBoolean(String columnName, boolean x, boolean forceEncrypt)`    <br/><br/>  `public void updateByte(String columnName, byte x, boolean forceEncrypt)`  <br/><br/>  `public void updateShort(String columnName, short x, boolean forceEncrypt)`  <br/><br/> `public void updateInt(String columnName, int x, boolean forceEncrypt)`   <br/><br/>   `public void updateLong(String columnName, long x, boolean forceEncrypt)` <br/><br/>  `public void updateFloat(String columnName, float x, boolean forceEncrypt)`  <br/><br/>  `public void updateDouble(String columnName, double x, boolean forceEncrypt)  <br/><br/> public void updateBigDecimal(String columnName, BigDecimal x, boolean forceEncrypt)`   <br/><br/>  `public void updateBigDecimal(String columnName, BigDecimal x, Integer precision, Integer scale, boolean forceEncrypt)`  <br/><br/> `public void updateString(String columnName, String x, boolean forceEncrypt)`   <br/><br/>  `public void updateBytes(String columnName, byte x[], boolean forceEncrypt)`  <br/><br/> `public void updateDate(String columnName, java.sql.Date x, boolean forceEncrypt)`   <br/><br/>  `public void updateTime(String columnName, java.sql.Time x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateTimestamp(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/> `public void updateDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`   <br/><br/>  `public void updateSmallDateTime(String columnName, java.sql.Timestamp x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateDateTimeOffset(String columnName, microsoft.sql.DateTimeOffset x, int scale, boolean forceEncrypt)`  <br/><br/>  `public void updateUniqueIdentifier(String columnName, String x, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object x, int precision, int scale, boolean forceEncrypt)`<br/><br/>`public void updateObject(String columnName, Object obj, SQLType targetSqlType, int scale, boolean forceEncrypt)`|將指定的資料行更新為給定的 java 值。<br/><br/>如果布林值 forceEncrypt 設定為 true, 則只有當資料行已加密, 而且在連接或語句上啟用 Always Encrypted 時, 才會設定該資料行。<br/><br/>如果布林值 forceEncrypt 設定為 false, 驅動程式將不會強制加密參數。|

  
在**microsoft .Sql 類型**類別中的新類型

|名稱|描述|  
|----------|-----------------|  
|DATETIME、SMALLDATETIME、MONEY、SMALLMONEY、GUID|當您使用`setObject()/updateObject()` API 方法將參數值傳送至**加密**的 datetime、Smalldatetime、money、smallmoney、uniqueidentifier 資料行時, 請使用這些類型做為目標 SQL 類型。|  
  
  
 **Sqlserverstatementcolumnencryptionsetting.resultset 列舉**  
  
 指定讀取及寫入加密的資料行時, 傳送和接收資料的方式。 根據您的特定查詢, 當使用非加密的資料行時, 略過 Always Encrypted 驅動程式的處理可能會降低效能影響。 請注意, 這些設定不能用來略過加密並取得純文字資料的存取權。  
  
 **語法**  
  
```java
Public enum  SQLServerStatementColumnEncryptionSetting  
```  
  
 **成員**  
  
|名稱|描述|  
|----------|-----------------|  
|UseConnectionSetting|指定命令應該預設為連接字串中的 Always Encrypted 設定。|  
|已啟用|啟用查詢的 Always Encrypted。|  
|ResultSetOnly|指定驅動程式中的 Always Encrypted 常式只應處理命令的結果。 當命令沒有需要加密的參數時, 請使用此值。|  
|已停用|停用查詢的 Always Encrypted。|  
  
 AE 的語句層級設定會新增至 SQLServerConnection 類別和 SQLServerConnectionPoolProxy 類別。 這些類別中的下列方法會使用新的設定進行多載。  
  
|名稱|描述|  
|----------|-----------------|  
|`public Statement createStatement(int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|建立語句物件, 它會產生具有指定類型、並行、保留性和資料行加密設定的 ResultSet 物件。|  
|`public CallableStatement prepareCall(String sql, int nType, int nConcur, int statementHoldability, SQLServerStatementColumnEncryptionSetting stmtColEncSetiing)`|使用指定的資料行加密設定來建立 JAVA.sql.callablestatement 物件, 以產生具有指定類型、並行和保留性的 ResultSet 物件。|  
|`public PreparedStatement prepareStatement(String sql, int autogeneratedKeys, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|使用指定的資料行加密設定, 建立具有可抓取自動產生金鑰之功能的 JAVA.sql.preparedstatement 物件。|  
|`public PreparedStatement prepareStatement(String sql, String[] columnNames, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|使用指定的資料行加密設定來建立 JAVA.sql.preparedstatement 物件, 以產生具有給定資料行名稱的 ResultSet 物件。|  
|`public PreparedStatement prepareStatement(String sql, int[] columnIndexes, SQLServerStatementColumnEncryptionSetting stmtColEncSetting`|使用指定的資料行加密設定來建立 JAVA.sql.preparedstatement 物件, 以使用指定的資料行索引來產生 ResultSet 物件。|  
|`public PreparedStatement prepareStatement(String sql, int nType, int nConcur, int nHold, SQLServerStatementColumnEncryptionSetting stmtColEncSetting)`|使用指定的資料行加密設定來建立 JAVA.sql.preparedstatement 物件, 以產生具有指定類型、並行和保留性的 ResultSet 物件。|  
  
> [!NOTE]  
>  如果已停用查詢的 Always Encrypted, 且查詢具有需要加密的參數 (對應至加密資料行的參數), 則查詢將會失敗。  
>   
>  如果已針對查詢停用 Always Encrypted, 且查詢傳回來自加密資料行的結果, 則查詢會傳回加密值。 加密的值將會有 Varbinary 資料類型。  
  
 ## <a name="see-also"></a>另請參閱  
 [搭配 JDBC 驅動程式使用 Always Encrypted](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  
  

