---
title: 空間資料類型範例 MSSQL JDBC driver |Microsoft Docs
ms.custom: ''
ms.date: 07/30/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f8ff0fa65eb8cf1fcafe54949504eb42c5e7380
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467726"
---
# <a name="spatial-data-types-sample"></a>空間資料類型範例

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

這[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]範例應用程式示範如何建立、 插入和擷取空間資料類型 （Geometry 和 Geography）。
  
此範例的程式碼檔案名稱為 SpatialDataTypes.java，並位於下列位置：  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes  
```

## <a name="requirements"></a>需求  

若要執行此範例應用程式，您必須將 Classpath 設定為包含 mssql-jdbc jar 檔案。 如需如何設定 classpath 的詳細資訊，請參閱[JDBC 驅動程式使用](../../connect/jdbc/using-the-jdbc-driver.md)。  

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 提供 mssql-jdbc 類別庫檔案，可根據您慣用的 Java Runtime Environment (JRE) 設定來使用。 如需有關選擇哪個 JAR 檔案的詳細資訊，請參閱[JDBC 驅動程式的系統需求](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)。  
  
## <a name="example"></a>範例

在下列範例中，範例程式碼會建立名為 SpatialDataTypesTable_JDBC_Sample 包含 '幾何' 和 'Geography' 的資料行的資料表。

範例首先會從格式-Known 文字 (well-known text，WKT) 表示的點建立 '幾何' 和 'Geography' 的物件。 它會使用參數化查詢使用 SQLServerPreparedStatement 據以對應至每個資料行的資料。

最後，此範例會將資料插入資料表中，並擷取它。 資料會顯示在的 well-known text，WKT 格式。

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;
import com.microsoft.sqlserver.jdbc.Geography;
import com.microsoft.sqlserver.jdbc.Geometry;
import com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement;
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

public class SpatialDataTypes {

    private static String tableName = "SpatialDataTypesTable_JDBC_Sample";

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";
        // Establish the connection.
        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            dropAndCreateTable(stmt);

            // TODO: Implement Sample code
            String geoWKT = "POINT(3 40 5 6)";
            Geometry geomWKT = Geometry.STGeomFromText(geoWKT, 0);
            Geography geogWKT = Geography.STGeomFromText(geoWKT, 4326);

            try (SQLServerPreparedStatement pstmt = (SQLServerPreparedStatement) con
                    .prepareStatement("insert into " + tableName + " values (?, ?)");) {
                pstmt.setGeometry(1, geomWKT);
                pstmt.setGeography(2, geogWKT);
                pstmt.execute();

                SQLServerResultSet rs = (SQLServerResultSet) stmt.executeQuery("select * from " + tableName);
                rs.next();

                System.out.println("Geometry data: " + rs.getGeometry(1));
                System.out.println("Geography data: " + rs.getGeography(2));
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    private static void dropAndCreateTable(Statement stmt) throws SQLException {
        stmt.executeUpdate("if object_id('" + tableName + "','U') is not null" + " drop table " + tableName);

        stmt.executeUpdate("Create table " + tableName + " (c1 geometry, c2 geography)");
    }
}
```

## <a name="see-also"></a>另請參閱  

[使用 JDBC 資料類型](../../connect/jdbc/working-with-data-types-jdbc.md)  
  