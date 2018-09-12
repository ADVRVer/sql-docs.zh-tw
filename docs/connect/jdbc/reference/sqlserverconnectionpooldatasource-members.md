---
title: SQLServerConnectionPoolDataSource 成員 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dac0337e-8088-488c-a25a-801a2190f6ca
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc4e63a8900368c021b2e1a0638523243eae271a
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787369"
---
# <a name="sqlserverconnectionpooldatasource-members"></a>SQLServerConnectionPoolDataSource 成員
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  下表列出 [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) 類別所公開的成員。  
  
## <a name="constructors"></a>建構函式  
  
|[屬性]|Description|  
|----------|-----------------|  
|[SQLServerConnectionPoolDataSource ()](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-constructor.md)|將 [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) 類別的新執行個體初始化。|  
  
## <a name="fields"></a>欄位  
 無。  
  
## <a name="inherited-fields"></a>繼承的欄位  
 無。  
  
## <a name="methods"></a>方法  
  
|[屬性]|Description|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回 **applicationIntent** 連線屬性的值。|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回應用程式名稱。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 嘗試與此 DataSource 物件所代表的資料來源建立連線。|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回資料庫名稱。|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回資料來源的描述。|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回用於資料庫鏡像設定的容錯移轉伺服器名稱。|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體名稱。|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回**布林**值來指出是否已啟用 lastUpdateCount 屬性。|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回 **int** 值來指出資料庫在報告鎖定逾時前將等待的毫秒數。|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回此 DataSource 物件在嘗試建立連線時將等待的秒數。|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回要用於所有記錄和追蹤訊息的字元輸出資料流。|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回 **multiSubnetFailover** 連線屬性的值。|  
|[getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)|嘗試建立可用來當做共用連接的實體資料庫連接。|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回目前用來與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通訊的連接埠號碼。|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverconnectionpooldatasource.md)|傳回此資料來源物件的參考。|  
|[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回用於以此 DataSource 物件所建立之所有結果集的預設資料指標類型。|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|(繼承自[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回**布林**值來指出是否已啟用以 UNICODE 格式將字串參數傳送到伺服器。|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回正在執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的電腦名稱。|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回用來連線至資料來源的 URL。|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回用來連線資料來源的使用者名稱。|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回用來連線至資料來源的用戶端電腦名稱。|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 傳回**布林**值來指出是否已啟用將 SQL 狀態轉換成符合 XOPEN 規範的狀態。|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)|指出這個物件是否為指定之介面的包裝函式。|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定 **applicationIntent** 連線屬性的值。|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定應用程式名稱。|  
|[setAuthenticationSceme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 表示您希望應用程式使用的整合式安全性種類。|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定要連線的目標資料庫名稱。|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定資料來源的描述。|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定用於資料庫鏡像設定的容錯移轉伺服器名稱。|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體名稱。|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定**布林**值來指出是否已啟用 integratedSecurity 屬性。|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定**布林**值來指出是否已啟用 lastUpdateCount 屬性。|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定 **int** 值來指出資料庫在報告鎖定逾時前將等待的毫秒數。|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|(繼承自[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定此 DataSource 物件在嘗試建立連線時將等待的秒數。|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定要用於所有記錄和追蹤訊息的字元輸出資料流。|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|(繼承自[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定的值**multiSubnetFailover**連接屬性。|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定將用來連線到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的密碼。|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定要用來與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通訊的連接埠號碼。|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定用於以此 DataSource 物件所建立之所有結果集的預設資料指標類型。|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定**布林**值來指出是否已啟用以 UNICODE 格式將字串參數傳送到伺服器。|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定正在執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的電腦名稱。|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定用來連線至資料來源的 URL。|  
|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定用來連線至資料來源的使用者名稱。|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定用來連線至資料來源的用戶端電腦名稱。|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|(繼承自 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)) 設定**布林**值來指出是否已啟用將 SQL 狀態轉換成符合 XOPEN 規範的狀態。|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)|傳回可實作指定介面的物件，此介面可允許存取 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 特定的方法。|  
  
## <a name="inherited-methods"></a>繼承的方法  
  
|類別繼承自：|方法|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerDataSource|getApplicationName, getConnection, getDatabaseName, getDescription, getFailoverPartner, getInstanceName, getLastUpdateCount, getLockTimeout, getLoginTimeout, getLogWriter, getPortNumber, getSelectMethod, getSendStringParametersAsUnicode, getServerName, getURL, getUser, getWorkstationID, getXopenStates, setApplicationName, setDatabaseName, setDescription, setFailoverPartner, setInstanceName, setIntegratedSecurity, setLastUpdateCount, setLockTimeout, setLoginTimeout, setLogWriter, setPassword, setPortNumber, setSelectMethod, setSendStringParametersAsUnicode, setServerName, setURL, setUser, setWorkstationID, setXopenStates|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
|javax.sql.ConnectionPoolDataSource|getLoginTimeout, getLogWriter, setLoginTimeout, setLogWriter, getPooledConnection|  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerConnectionPoolDataSource 類別](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
