---
title: "使用連接共用 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 699d4e8a-34bf-4c60-b0d5-4a10dad6084a
caps.latest.revision: "30"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b0125330ff44030e354423b105710fc6806f337
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="using-connection-pooling"></a>使用連接共用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]提供支援 Java platform Enterprise Edition (Java EE) 連接共用。 JDBC Driver 會實作 JDBC 3.0 所需的介面，讓驅動程式能夠參與中介軟體供應商所提供且和 JDBC 3.0 相容的任何連接共用實作。 Java EE 應用程式伺服器這類的中介軟體，經常會提供相容的連接共用機能。 JDBC Driver 將參與這些環境中的共用連接。  
  
> [!NOTE]  
>  雖然 JDBC Driver 支援 Java EE 連接共用，但是它不會提供自己的共用實作。 驅動程式會依賴協力廠商的 Java 應用程式伺服器來管理連接。  
  
## <a name="remarks"></a>備註  
 連接共用實作的類別如下所示。  
  
|類別|實作|Description|  
|-----------|----------------|-----------------|  
|com.microsoft.sqlserver.jdbc。 SQLServerXADataSource|javax.sql.ConnectionPoolDataSource 和 javax.sql.XADataSource|我們建議您改用[SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)需要所有 Java EE 伺服器類別，因為它會實作所有的 JDBC 3.0 共用和 XA 介面。|  
|com.microsoft.sqlserver.jdbc。 SQLServerConnectionPoolDataSource|javax.sql.ConnectionPoolDataSource|這個類別是 Connection Factory，可讓 Java EE 應用程式伺服器以實體連接擴展其連接集區。 如果 Java EE 供應商的組態需要有實作 javax.sql.ConnectionPoolDataSource 的類別，將類別名稱指定為[SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)。 我們通常會建議您改用[SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)類別，因為它實作共用和 XA 介面，並已在多個 Java EE 伺服器組態中獲得驗證。|  
  
 JDBC 應用程式程式碼應該一律明確地關閉連接，才能從共用獲得最多益處。 當應用程式明確關閉連接時，共用實作可以立即重複使用連接。 如果未關閉連接，則其他應用程式無法重複使用它。 應用程式可以使用`finally`建構，以確定即使發生例外狀況關閉共用的連接。  
  
> [!NOTE]  
>  JDBC 驅動程式將連接傳回集區時，目前不會呼叫 sp_reset_connection 預存程序； 而是會依靠協力廠商的 Java 應用程式伺服器，讓連接回到原始的狀態。  
  
## <a name="see-also"></a>請參閱＜  
 [使用 JDBC Driver 連接到 SQL Server](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
