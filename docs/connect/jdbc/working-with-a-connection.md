---
title: 使用連接 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5bfafa2a259d472d65d224403797bfa1968898b2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="working-with-a-connection"></a>使用連接
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  下列各節提供的不同的方式可連接到範例[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]資料庫使用[SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)類別[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]。  
  
> [!NOTE]  
>  如果您有連接到的問題[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]使用 JDBC 驅動程式，請參閱[連接性疑難排解](../../connect/jdbc/troubleshooting-connectivity.md)建議如何修正它。  
  
## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>使用 DriverManager 類別建立連接  
 最簡單的方式建立的連接[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]資料庫為載入 JDBC 驅動程式，並呼叫 getConnection 方法的 DriverManager 類別，如下所示：  
  
```  
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 此技術將使用驅動程式清單中第一個可用的驅動程式 (可與指定之 URL 順利進行連接)，以建立資料庫連接。  
  
> [!NOTE]  
>  使用 sqljdbc4.jar 類別庫時，應用程式不需要明確註冊或載入此驅動程式使用 Class.forName 方法。 DriverManager 類別的 getConnection 方法呼叫時，就有一個適當的驅動程式位於從已註冊的 JDBC 驅動程式的集合。 如需詳細資訊，請參閱＜使用 JDBC Driver＞。  
  
## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>使用 SQLServerDriver 類別建立連接  
 如果您有指定 DriverManager 驅動程式清單中的特定驅動程式，您可以建立資料庫連接使用[連接](../../connect/jdbc/reference/connect-method-sqlserverdriver.md)方法[SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md)類別，如下所示：  
  
```  
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```  
  
## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>使用 SQLServerDataSource 類別建立連接  
 如果您必須建立的連接使用[SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)類別，您可以使用類別的各種 setter 方法，才能呼叫[getConnection](../../connect/jdbc/reference/getconnection-method.md)方法，如下所示：  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setUser("MyUserName");  
ds.setPassword("*****");  
ds.setServerName("localhost");  
ds.setPortNumber(1433);   
ds.setDatabaseName("AdventureWorks");  
Connection con = ds.getConnection();  
```  
  
## <a name="creating-a-connection-that-targets-a-very-specific-data-source"></a>建立以相當特定的資料來源為目標的連接  
 如果您必須建立以相當特定的資料來源為目標的資料庫連接，有一些方法可供您採用。 每種方法均視您使用連接 URL 所設定的屬性而定。  
  
 若要連接到遠端伺服器的預設執行個體，請使用下列方法：  
  
 `String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"`  
  
 若要連接到伺服器上的特定通訊埠，請使用下列方法：  
  
 `String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"`  
  
 若要連接到伺服器上的具名執行個體，請使用下列方法：  
  
 `String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"`  
  
 若要連接到伺服器上的特定資料庫，請使用下列方法：  
  
 `String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"`  
  
 如需更多連接 URL 範例，請參閱[建立連接 URL](../../connect/jdbc/building-the-connection-url.md)。  
  
## <a name="creating-a-connection-with-a-custom-login-time-out"></a>建立具有自訂登入逾時的連接  
 如果您必須調整伺服器負載或網路流量，您可建立具有特定登入逾時值 (以秒計) 的連接，如下所示：  
  
 `String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"`  
  
## <a name="create-a-connection-with-application-level-identity"></a>建立具有應用程式層級識別的連接  
 如果您必須使用記錄及設定檔作業，您將必須識別來自特定應用程式的連接，如下所示：  
  
 `String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"`  
  
## <a name="closing-a-connection"></a>關閉連接  
 您可以呼叫，以明確關閉資料庫連接[關閉](../../connect/jdbc/reference/close-method-sqlserverconnection.md)SQLServerConnection 類別方法，如下所示：  
  
 `con.close();`  
  
 這會釋出的 SQLServerConnection 物件所使用的資料庫資源，或將連接傳回連接集區管理的集區的案例中。  
  
> [!NOTE]  
>  呼叫 close 方法也會回復任何暫止交易。  
  
## <a name="see-also"></a>另請參閱  
 [使用 JDBC Driver 連接到 SQL Server](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
