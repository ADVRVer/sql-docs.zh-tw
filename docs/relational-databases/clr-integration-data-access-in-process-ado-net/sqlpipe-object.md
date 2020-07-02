---
title: SqlPipe 物件 |Microsoft Docs
description: 對於在 SQL Server 中執行的 CLR 資料庫物件，您可以使用 SqlPipe 物件的 Send 方法，將結果傳送至連接的管道。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
author: rothja
ms.author: jroth
ms.openlocfilehash: 17a26c5897ff10ce636297151cef9f300f4f3056
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765421"
---
# <a name="sqlpipe-object"></a>SqlPipe 物件
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，通常會撰寫將結果或輸出參數傳送至呼叫用戶端的預存程序 (或擴充的預存程序)。  
  
 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程式中，傳回零或多個資料列的任何**SELECT**語句都會將結果傳送至已連線的呼叫端的「管道」。  
  
 若是在中執行的 common language runtime （CLR）資料庫物件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，您可以使用**SqlPipe**物件的**send**方法，將結果傳送至連接的管道。 存取**SqlCoNtext**物件的**Pipe**屬性，以取得**SqlPipe**物件。 **SqlPipe**類別在概念上類似于 ASP.NET 中找到的**回應**類別。 如需詳細資訊，請參閱 .NET Framework 軟體開發套件中的 SqlPipe 類別參考文件集。  
  
## <a name="returning-tabular-results-and-messages"></a>傳回表格式結果和訊息  
 **SqlPipe**有一個**Send**方法，其中有三個多載。 其中包括：  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 Send 方法會將資料直接**傳送**至用戶端或呼叫者。 這通常是取用**SqlPipe**輸出的用戶端，但在嵌套 CLR 預存程式的情況下，輸出取用者也可以是預存程式。 例如，Procedure1 會使用命令文字 "EXEC Procedure2" 呼叫 SqlCommand.ExecuteReader()。 而 Procedure2 也是 Managed 預存程序。 如果 Procedure2 此時呼叫 SqlPipe.Send( SqlDataRecord )，資料列便會傳送至 Procedure1 的讀取器 (Reader)，而非用戶端。  
  
 Send 方法會將出現在用戶端上的字串訊息**傳送**為資訊訊息，相當於在中列印 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。 它也可以使用**SqlDataRecord**來傳送單一資料列結果集，或使用**SqlDataReader**的多資料列結果集。  
  
 **SqlPipe**物件也具有**ExecuteAndSend**方法。 這個方法可用來執行命令（以**SqlCommand**物件的形式傳遞），並將結果直接傳送回呼叫端。 如果已提交的命令中出現錯誤，便會將例外狀況 (Exception) 傳送至管道，但也會傳送複本給呼叫的 Managed 程式碼。 如果呼叫程式碼未攔截到例外狀況，它會將堆疊向上傳播至 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，並在輸出中出現兩次。 如果呼叫程式碼攔截到例外狀況，管道取用者還是會看到錯誤，但是不會有重複的錯誤。  
  
 它只能接受與內容連接相關聯的**SqlCommand** 。它無法接受與非內容連接相關聯的命令。  
  
## <a name="returning-custom-result-sets"></a>傳回自訂結果集  
 Managed 預存程式可以傳送不是來自**SqlDataReader**的結果集。 **SendResultsStart**方法連同**SendResultsRow**和**SendResultsEnd**，可讓預存程式將自訂結果集傳送至用戶端。  
  
 **SendResultsStart**接受**SqlDataRecord**做為輸入。 它會標示結果集的開頭，並使用記錄中繼資料來建構說明結果集的中繼資料。 它不會使用**SendResultsStart**傳送記錄的值。 所有使用**SendResultsRow**傳送的後續資料列，都必須符合該元資料定義。  
  
> [!NOTE]  
>  呼叫**SendResultsStart**方法之後，只能呼叫**SendResultsRow**和**SendResultsEnd** 。 在相同的**SqlPipe**實例中呼叫任何其他方法，會導致**InvalidOperationException**。 **SendResultsEnd**會將**SqlPipe**設定回初始狀態，以便呼叫其他方法。  
  
### <a name="example"></a>範例  
 **UspGetProductLine**預存程式會傳回指定產品線內所有產品的名稱、產品編號、色彩和標價。 這個預存程式會接受與*prodLine*完全相符的專案。  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 下列語句會執行 UspGetProduct 程式，此程式會傳回 [!INCLUDE[tsql](../../includes/tsql-md.md)] 一份旅行自行車產品的**uspGetProduct**清單。  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a>另請參閱  
 [SqlDataRecord 物件](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)   
 [CLR 預存程式](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [ADO.NET 的 SQL Server 同處理序特定擴充](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
