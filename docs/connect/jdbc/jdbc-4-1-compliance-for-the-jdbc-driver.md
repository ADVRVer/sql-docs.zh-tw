---
title: "JDBC 4.1 相容性的 JDBC 驅動程式 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f087fd40-8451-478e-b465-43112c711515
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8221755d220caec5588c8ed1343e360799b82694
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="jdbc-41-compliance-for-the-jdbc-driver"></a>適用於 JDBC 驅動程式的 JDBC 4.1 相容性
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  適用於 SQL Server 的 Microsoft JDBC 驅動程式 4.2 之前的版本，與 Java 資料庫連線 API 4.0 規格相容。 本節不適用於在 4.2 版之前的版本。  
  
 Microsoft JDBC Driver 4.2 for SQL Server 可使用下列 API 方法，支援 Java 資料庫連線 API 4.1 規格。  
  
 **SQLServerConnection 類別**  
  
|新的方法|Description|JDBC 驅動程式實作|  
|----------------|-----------------|--------------------------------|  
|void abort(Executor executor)|終止對 SQL Server 的開啟連接。|如 java.sql.Connection 介面中所述實作。 如需詳細資訊，請參閱[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)。|  
|void setSchema(String schema)|設定目前連接的結構描述。|SQL Server 不支援目前工作階段的結構描述設定。 如果呼叫了此方法，則此驅動程式會以無訊息模式記錄警告訊息。 如需詳細資訊，請參閱[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)。|  
|String getSchema()|傳回目前連接的結構描述名稱。|因為 SQL Server 不支援目前連接的結構描述設定，所以此驅動程式改為傳回該使用者的預設結構描述。 如需詳細資訊，請參閱[java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html)。|  
  
 **SQLServerDatabaseMetaData 類別**  
  
|新的方法|Description|JDBC 驅動程式實作|  
|----------------|-----------------|--------------------------------|  
|boolean generatedKeyAlwaysReturned()|當此驅動程式支援擷取產生的索引鍵時，便會傳回 true|如 java.sql 中所述實作。 DatabaseMetaData 介面。 如需詳細資訊，請參閱[java.sql.DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html)。|  
|ResultSet getPseudoColumns(String catalog, String schemaPattern,String tableNamePattern,String columnNamePattern)|擷取虛擬/隱藏資料行的描述|因為 SQL Server 沒有虛擬資料行的形式概念，所以會傳回空的結果集。 如需詳細資訊，請參閱[java.sql.DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html)。|  
  
 **SQLServerStatement 類別**  
  
|新的方法|Description|JDBC 驅動程式實作|  
|----------------|-----------------|--------------------------------|  
|void closeOnCompletion()|指定與該陳述式所有相依的結果集已關閉時，將會關閉這個陳述式。|如 java.sql.Statement 介面中所述實作。 如需詳細資訊，請參閱[java.sql.Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html)。|  
|boolean isCloseOnCompletion()|傳回值，表示與該陳述式所有相依的結果集已關閉時，是否要關閉這個陳述式。|如 java.sql.Statement 介面中所述實作。 如需詳細資訊，請參閱[java.sql.Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html)。|  
  
 Microsoft JDBC Driver 4.2 for SQL Server 可使用下列功能，支援 Java 資料庫連線 API 4.1 規格。  
  
|新功能|Description|  
|-----------------|-----------------|  
|新的逸出函數<br /><br /> 限制傳回的資料列逸出|部分支援<br /><br /> 逸出語法： 限制\<資料列 > [OFFSET < 資料列位移 >]<br /><br /> 逸出語法有兩個部分： 必要的部分為「資料列」，指定要傳回的資料列數目，選擇性的部分為「資料列位移」，指定開始傳回資料列之前要略過的資料列數目。<br /><br /> 此驅動程式只支援必要的部分，方法是轉換查詢為使用 'TOP’，而非 LIMIT (SQL Server 不支援 'LIMIT')。<br /><br /> 如果使用了選擇性部分「資料列位移」，則此驅動程式會擲回例外狀況，因為 SQL Server 並沒有任何支援的內建建構。<br /><br /> 如需詳細資訊，請參閱[使用 SQL 逸出序列](https://msdn.microsoft.com/en-us/library/ms378045.aspx)。|  
  
 Microsoft JDBC Driver 4.2 for SQL Server 可使用下列資料類型對應，支援 Java 資料庫連線 API 4.1 規格。  
  
|資料類型對應|Description|  
|------------------------|-----------------|  
|PreparedStatement.setObject() 和 PreparedStatement.setNull() 方法現在支援新的資料類型對應。|1.新的 Java JDBC 類型對應<br /><br /> (a) 從 java.math.BigInteger 到 JDBC BIGINT<br /><br /> (b) 從 java.util.Date 和 java.util.Calendar 到 JDBC TIMESTAMP<br /><br /> 2.新的資料類型轉換：<br /><br /> (a) 從 java.math.BigInteger 到 CHAR、VARCHAR、LONGVARCHAR 和 BIGINT<br /><br /> (b) 從 java.util.Date 和 java.util.Calendar 到 CHAR、VARCHAR、LONGVARCHAR、DATE、TIME 和 TIMESTAMP<br /><br /> 如需詳細資訊，請參閱 JDBC 4.1 規格。|  
  
  
