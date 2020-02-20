---
title: SQLXML 資料類型範例 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8f2ff25b-71fd-46d7-b6de-d656095d2aad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df376535f8f6c6a7d98e1744a2d2b70e813d400a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028278"
---
# <a name="sqlxml-data-type-sample"></a>SQLXML 資料類型範例

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

此 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 範例應用程式示範如何在關聯式資料庫中儲存 XML 資料、如何從資料庫中擷取 XML 資料，以及如何剖析具有 **SQLXML** Java 資料類型的 XML 資料。

本節中的程式碼範例會使用 Simple API for XML (SAX) 剖析器。 SAX 是一套公開開發的標準，可用於以事件為基礎的方式剖析 XML 文件。 此外，它也會提供用於使用 XML 資料的應用程式開發介面。 請注意，應用程式也可以使用任何其他 XML 剖析器，例如文件物件模型 (DOM) 或 Streaming API for XML (StAX)。

文件物件模型 (DOM) 會提供 XML 文件、片段、節點或節點集的程式表示法。 此外，它也會提供用於使用 XML 資料的應用程式開發介面。 同樣地，Streaming API for XML (StAX) 是以 Java 為基礎的 API，可用於提取剖析 XML。

> [!IMPORTANT]  
> 若要使用 SAX 剖析器 API，您必須從 javax.xml 封裝匯入標準 SAX 實作。

此範例的程式碼檔案名稱為 SqlXmlDataType.java，並位於下列位置：

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes
```

## <a name="requirements"></a>需求

若要執行此範例應用程式，您必須將 Classpath 設定為包含 sqljdbc4.jar 檔案。 如果 Classpath 遺漏 sqljdbc4.jar 的項目，範例應用程式將會擲回「找不到類別」的例外狀況。 如需如何設定 classpath 的詳細資訊，請參閱[使用 JDBC 驅動程式](../../../connect/jdbc/using-the-jdbc-driver.md)。

此外，若要執行此範例應用程式，您必須存取 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 範例資料庫。

## <a name="example"></a>範例

在下列範例中，範例程式碼會建立 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 資料庫的連線，然後呼叫 createSampleTables 方法。

createSampleTables 方法會卸除 TestTable1 和 TestTable2 測試資料表 (如果它們存在的話)。 然後，它會將兩個資料列插入 TestTable1 中。

此外，程式碼範例包含下列三種方法以及一個名為 ExampleContentHandler 的額外類別。

ExampleContentHandler 類別會實作針對剖析器事件定義方法的自訂內容處理常式。

showGetters 方法示範如何使用 SAX、ContentHandler 和 XMLReader 來剖析 SQLXML 物件中的資料。 首先，程式碼範例會建立自訂內容處理常式的執行個體，亦即 ExampleContentHandler。 接著，它會建立並執行從 TestTable1 中傳回一組資料的 SQL 陳述式。 然後，程式碼範例會取得 SAX 剖析器並剖析 XML 資料。

showSetters 方法示範如何使用 SAX、ContentHandler 和 ResultSet 來設定 **xml** 資料行。 首先，它會使用 Connection 類別的 [createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) 方法來建立空的 SQLXML 物件。 然後，它會取得內容處理常式的執行個體，以便將資料寫入 SQLXML 物件中。 接著，程式碼範例會將資料寫入 TestTable1。 最後，範例程式碼會逐一查看結果集中的資料列，並且使用 [getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) 方法來讀取 XML 資料。

showTransformer 方法將示範如何從某份資料表中取得 XML 資料，然後使用 SAX 和 Transformer，將該 XML 資料插入另一份資料表中。 首先，它會從 TestTable1 中擷取來源 SQLXML 物件。 然後，它會使用 Connection 類別的 [createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md) 方法來建立空的目的地 SQLXML 物件。 接著，它會更新目的地 SQLXML 物件並將 XML 資料寫入 TestTable2。 最後，範例程式碼會逐一查看結果集中的資料列，並且使用 [getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md) 方法來讀取 TestTable2 中的 XML 資料。

[!code[JDBC#UsingSQLXML1](../../../connect/jdbc/codesnippet/Java/sqlxml-data-type-sample_1.java)]

## <a name="see-also"></a>另請參閱

[使用資料類型 &#40;JDBC&#41;](../../../connect/jdbc/code-samples/working-with-data-types-jdbc.md)
