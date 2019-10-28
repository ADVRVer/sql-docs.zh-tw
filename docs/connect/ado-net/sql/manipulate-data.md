---
title: 操作資料
description: 提供編寫 MARS 應用程式的範例。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: df430bbacb69e1d95d001e4f9340ca60473503cd
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452160"
---
# <a name="manipulating-data"></a>操作資料

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[下載 ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

在引入 Multiple Active Result Sets （MARS）之前，開發人員必須使用多個連接或伺服器端資料指標來解決特定案例。 此外，當在交易情況中使用多重連線時，需要繫結連線 (使用 **sp_getbindtoken** 及 **sp_bindsession**)。 下列案例示範如何使用已啟用 MARS 的連接，而不是多個連接。  
  
## <a name="using-multiple-commands-with-mars"></a>搭配使用多個命令與 MARS  
下列主控台應用程式示範如何使用兩個具有兩個 <xref:Microsoft.Data.SqlClient.SqlCommand> 物件的 <xref:Microsoft.Data.SqlClient.SqlDataReader> 物件，以及已啟用 MARS 的單一 <xref:Microsoft.Data.SqlClient.SqlConnection> 物件。  
  
### <a name="example"></a>範例  
此範例會開啟與**AdventureWorks**資料庫的單一連接。 使用 <xref:Microsoft.Data.SqlClient.SqlCommand> 物件時，會建立 <xref:Microsoft.Data.SqlClient.SqlDataReader>。 使用讀取器時，會開啟第二個 <xref:Microsoft.Data.SqlClient.SqlDataReader>，使用第一個 <xref:Microsoft.Data.SqlClient.SqlDataReader> 的資料做為第二個讀取器的 WHERE 子句輸入。  
  
> [!NOTE]
>  下列範例使用包含於 SQL Server 的 **AdventureWorks** 範例資料庫。 範例程式碼中提供的連接字串假設本機電腦上已安裝並可使用資料庫。 視環境需要修改連接字串。  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a>使用 MARS 讀取和更新資料  
MARS 允許將連接用於讀取作業和資料操作語言（DML）作業，其中包含一個以上的暫止操作。 這項功能可讓應用程式不需要處理連接忙碌的錯誤。 此外，MARS 也可以取代伺服器端資料指標的使用者，這通常會耗用更多資源。 最後，因為多個作業可在單一連線上進行操作，所以可共用相同的交易內容，而無需使用 **sp_getbindtoken** 及 **sp_bindsession** 系統預存程序。  
  
### <a name="example"></a>範例  
下列主控台應用程式示範如何使用兩個具有三個 <xref:Microsoft.Data.SqlClient.SqlCommand> 物件的 <xref:Microsoft.Data.SqlClient.SqlDataReader> 物件，以及已啟用 MARS 的單一 <xref:Microsoft.Data.SqlClient.SqlConnection> 物件。 第一個命令物件會抓取其信用評等為5的廠商清單。 第二個命令物件會使用 <xref:Microsoft.Data.SqlClient.SqlDataReader> 所提供的廠商識別碼，載入第二個 <xref:Microsoft.Data.SqlClient.SqlDataReader>，其中包含特定廠商的所有產品。 第二個 <xref:Microsoft.Data.SqlClient.SqlDataReader> 會造訪每個產品記錄。 將會執行計算，以判斷新的 **OnOrderQty** 應該是什麼。 然後使用第三個命令物件，以新值來更新 **ProductVendor** 資料表。 這整個程式會在單一交易內進行，並在結束時回復。  
  
> [!NOTE]
>  下列範例使用包含於 SQL Server 的 **AdventureWorks** 範例資料庫。 範例程式碼中提供的連接字串假設本機電腦上已安裝並可使用資料庫。 視環境需要修改連接字串。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="next-steps"></a>後續步驟
- [Multiple Active Result Set (MARS)](multiple-active-result-sets-mars.md)
