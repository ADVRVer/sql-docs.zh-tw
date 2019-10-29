---
title: 資料表值參數
description: 描述如何使用在 SQL Server 2008 中引進的資料表值參數。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: cb8eec87d0d36eb7deb8663e40407c0067967def
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451927"
---
# <a name="table-valued-parameters"></a>資料表值參數

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[下載 ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

資料表值參數提供從用戶端應用程式，將多個資料列的資料封送至 SQL Sever 的簡便方式，而不需多次來回存取或特殊的伺服器端邏輯才能處理資料。 您可以使用資料表值參數，以一個參數化命令在用戶端應用程式中封裝資料列的資料，並傳送至伺服器。 傳入的資料列會儲存於資料表變數中，之後可使用 Transact-SQL 進行運算。  
  
資料表值參數中的資料行值可透過標準的 Transact-SQL SELECT 陳述式加以存取。 資料表值參數為強型別參數，其結構會自動驗證。 資料表值參數的大小只受限於伺服器記憶體。  
  
> [!NOTE]
>  您無法以資料表值參數傳回資料。 資料表值參數是僅限輸入;不支援 OUTPUT 關鍵字。  
  
如需有關資料表值參數的詳細資訊，請參閱下列資源。  
  
|資源|Description|  
|--------------|-----------------|  
|《SQL Server 線上叢書》中的[資料表值參數 (資料庫引擎)](https://go.microsoft.com/fwlink/?LinkId=98363)|描述如何建立及使用資料表值參數。|  
|SQL Server 線上叢書中的[使用者定義資料表類型](https://go.microsoft.com/fwlink/?LinkId=98364)|說明用來宣告資料表值參數的使用者定義資料表類型。|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>在舊版 SQL Server 中傳遞多個資料列  
在 SQL Server 2008 中引進資料表值參數之前，將多個資料列傳遞至預存程序或參數化 SQL 命令的選項有所限制。 開發人員可以從下列選項中選擇，將多個資料列傳遞至伺服器：  
  
- 使用一系列的個別參數來代表多個資料行和資料列中的值。 使用這個方法可以傳遞的資料量受限於允許的參數數目。 SQL Server 程序最多可以有 2100 個參數。 需要伺服器端邏輯，才能將這些個別的值組合成資料表變數或臨時表進行處理。  
  
- 將多個資料值組合成分隔字串或 XML 檔，然後將這些文字值傳遞給程式或語句。 這需要程式或語句包含驗證資料結構和 unbundling 值所需的邏輯。  
  
- 針對會影響多個資料列的資料修改建立一系列的個別 SQL 語句，例如，藉由呼叫 <xref:Microsoft.Data.SqlClient.SqlDataAdapter> 的 `Update` 方法所建立。 變更可以個別提交至伺服器，或批次處理成群組。 不過，即使是以包含多個語句的批次提交，每個語句都會在伺服器上個別執行。  
  
- 使用 `bcp` 公用程式或 <xref:Microsoft.Data.SqlClient.SqlBulkCopy> 物件，將許多資料列載入資料表。 雖然這項技術非常有效率，但除非將資料載入臨時表或資料表變數中，否則不支援伺服器端處理。  
  
## <a name="creating-table-valued-parameter-types"></a>建立資料表值參數類型  
資料表值參數是以使用 Transact-SQL CREATE TYPE 陳述式所定義的強型別資料表結構為基礎。 您必須先在 SQL Server 中建立資料表類型並定義此結構，然後才能在用戶端應用程式中使用資料表值參數。 如需建立資料表類型的詳細資訊，請參閱《SQL Server 線上叢書》中的[使用者定義資料表類型](https://go.microsoft.com/fwlink/?LinkID=98364)。  
  
下列語句會建立名為 CategoryTableType 的資料表類型，其中包含 [類別目錄] 和 [類別名稱] 資料行：  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
建立資料表類型之後，您可以根據該類型來宣告資料表值參數。 下列 Transact-SQL 片段將示範如何在預存程序定義中宣告資料表值參數。 請注意，必須要有 READONLY 關鍵字才能宣告資料表值參數。  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>使用資料表值參數修改資料 (Transact-SQL)  
資料表值參數可用於以集合為基礎的資料修改（藉由執行單一語句來影響多個資料列）。 例如，您可以選取資料表值參數中的所有資料列，並將它們插入資料庫資料表中，或者您可以藉由將資料表值參數聯結至您要更新的資料表來建立 update 語句。  
  
下列 Transact-SQL UPDATE 陳述式會示範如何將資料表值參數聯結至 Categories 資料表，藉以運用此參數。 當您在 FROM 子句中使用資料表值參數搭配聯結時，您也必須將它設為別名，如下所示，其中資料表值參數的別名為 "ec"：  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
這個 Transact-SQL 範例將示範如何從資料表值參數中選取資料列，以便在單一集合式作業中執行 INSERT。  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>資料表值參數的限制  
資料表值參數有幾項限制：  
  
- 您無法將資料表值參數傳遞至 [CLR 使用者定義函式](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)。  
  
- 資料表值參數只能編制索引，以支援 UNIQUE 或 PRIMARY KEY 條件約束。 SQL Server 不會維護資料表值參數的統計資料。  
  
- 資料表值參數在 Transact-SQL 程式碼中處於唯讀狀態。 您無法更新資料表值參數資料列中的資料行值，也無法插入或刪除資料列。 若要在資料表值參數中修改傳遞至預存程式或參數化語句的資料，您必須將資料插入臨時表或資料表變數中。  
  
- 您不能使用 ALTER TABLE 語句來修改資料表值參數的設計。  
  
## <a name="configuring-a-sqlparameter-example"></a>設定 SqlParameter 範例  
<xref:Microsoft.Data.SqlClient> 支援從 <xref:System.Data.DataTable>、<xref:System.Data.Common.DbDataReader> 或 <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.Data.SqlClient.Server.SqlDataRecord>物件填入資料表值參數。 您必須使用 <xref:Microsoft.Data.SqlClient.SqlParameter> 的 <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> 屬性來指定資料表值參數的類型名稱。 `TypeName` 必須符合先前在伺服器上建立的相容型別名稱。 下列程式碼片段示範如何設定 <xref:Microsoft.Data.SqlClient.SqlParameter> 以插入資料。  
 
在下列範例中，`addedCategories` 變數包含 <xref:System.Data.DataTable>。 若要查看變數的填入方式，請參閱下一節將[資料表值參數傳遞至預存程式](#passing)中的範例。

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```   
  
您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數，如本片段所示：  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
## <a name="passing"></a> 將資料表值參數傳遞至預存程序  
這個範例示範如何將資料表值參數資料傳遞至預存程式。 程式碼會使用 <xref:System.Data.DataTable.GetChanges%2A> 方法，將加入的資料列解壓縮至新的 <xref:System.Data.DataTable>。 然後，程式碼會定義 <xref:Microsoft.Data.SqlClient.SqlCommand>，將 <xref:Microsoft.Data.SqlClient.SqlCommand.CommandType%2A> 屬性設定為 <xref:System.Data.CommandType.StoredProcedure>。 <xref:Microsoft.Data.SqlClient.SqlParameter> 是使用 <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 方法填入，而且 <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> 設定為 `Structured`。 然後，<xref:Microsoft.Data.SqlClient.SqlCommand> 會使用 <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 方法來執行。  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>將資料表值參數傳遞至參數化 SQL 語句  
 下列範例示範如何將資料插入 dbo。Category 資料表：使用 INSERT 語句搭配包含資料表值參數當做資料來源的 SELECT 子查詢。 將資料表值參數傳遞至參數化 SQL 語句時，您必須使用 <xref:Microsoft.Data.SqlClient.SqlParameter> 的新 <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A> 屬性來指定資料表值參數的類型名稱。 這個 `TypeName` 必須符合先前在伺服器上建立的相容型別名稱。 此範例中的程式碼會使用 `TypeName` 屬性來參考 dbo 中定義的類型結構。CategoryTableType.  
  
> [!NOTE]
>  如果您在資料表值參數中提供識別欄位的值，就必須發出會話的 SET IDENTITY_INSERT 語句。  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
## <a name="streaming-rows-with-a-datareader"></a>使用 DataReader 串流資料列  
您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數。 下列程式碼片段示範如何使用 <xref:System.Data.OracleClient.OracleCommand> 和 <xref:System.Data.OracleClient.OracleDataReader>，從 Oracle 資料庫中取出資料。 然後，程式碼會設定 <xref:Microsoft.Data.SqlClient.SqlCommand>，以使用單一輸入參數來叫用預存程式。 <xref:Microsoft.Data.SqlClient.SqlParameter> 的 <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> 屬性會設定為 [`Structured`]。 <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 會將 `OracleDataReader` 結果集當做資料表值參數傳遞至預存程式。  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
## <a name="next-steps"></a>後續步驟
- [ADO.NET 中的 SQL Server 資料作業](sql-server-data-operations.md)
