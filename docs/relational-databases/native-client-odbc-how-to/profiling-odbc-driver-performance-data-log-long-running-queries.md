---
title: 記錄長時間執行的查詢 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- queries [ODBC]
ms.assetid: b9c1ddce-1dd9-409d-a414-8b544d616273
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9dab917b4adbbb186b916f68f74481b4a3ccbf8b
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2018
ms.locfileid: "35701019"
---
# <a name="profiling-odbc-driver-performance-data---log-long-running-queries"></a>程式碼剖析的 ODBC 驅動程式效能資料的記錄長時間執行的查詢
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  此範例會顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 驅動程式專用選項，用以記錄長時間執行的查詢。 執行時，此範例會建立 Odbcqry.log，其中包含執行超過應用程式設定之間隔的查詢清單。 IA64 不支援此範例。 此範例是針對 ODBC 3.0 版或更新版本所開發。  
  
> [!IMPORTANT]  
>  盡可能使用 Windows 驗證。 如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。 請避免將認證儲存在檔案中。 如果您必須保存認證，則應該用 [Win32 crypto API](http://go.microsoft.com/fwlink/?LinkId=64532) 加密這些認證。  
  
### <a name="to-log-long-running-queries-using-odbc-administrator"></a>使用 ODBC 管理員記錄長時間執行的查詢  
  
1.  在**控制台**，連按兩下**系統管理工具**，然後按兩下 **資料來源 (ODBC)**。 (或者，您也可以從命令提示字元執行 odbcad32.exe)。  
  
2.  按一下**使用者 DSN**，**系統 DSN**，或**檔案 DSN**  索引標籤。  
  
3.  按一下記錄長時間執行之查詢的資料來源。  
  
4.  按一下**設定**。  
  
5.  在 Microsoft SQL Server 設定 DSN 精靈，瀏覽至包含頁面**將長時間執行的查詢儲存到記錄檔**。  
  
6.  選取**將長時間執行的查詢儲存到記錄檔**。 在方塊中，放置應該記錄其長時間執行查詢之檔案的名稱。 （選擇性） 按一下**瀏覽**瀏覽檔案系統的查詢記錄。  
  
7.  設定查詢逾時間隔，以毫秒為單位，在**長時間查詢的時間 （毫秒）** 方塊。  
  
### <a name="to-log-long-running-queries-data-programmatically"></a>以程式設計方式記錄長時間執行的查詢資料  
  
1.  呼叫[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)利用 SQL_COPT_SS_PERF_QUERY_LOG 以及長時間執行的查詢記錄檔的完整路徑和檔案名稱。 例如：  
  
    ```  
    C:\\Odbcqry.log  
    ```  
  
2.  呼叫[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)與 sql_copt_ss_perf_query_interval 會設定為逾時間隔，以毫秒為單位。  
  
3.  呼叫[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)利用 SQL_COPT_SS_PERF_QUERY 和 SQL_PERF_START 開始記錄長時間執行的查詢。  
  
4.  呼叫[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)利用 SQL_COPT_SS_PERF_QUERY 和 SQL_PERF_STOP 停止記錄長時間執行的查詢。  
  
## <a name="example"></a>範例  
 您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫  (您可以從 [Microsoft SQL Server Samples and Community Projects](http://go.microsoft.com/fwlink/?LinkID=85384) (Microsoft SQL Server 範例和社群專案) 首頁下載 AdventureWorks 範例資料庫)。此資料來源必須以作業系統提供的 ODBC 驅動程式為基礎 (驅動程式名稱為 "SQL Server")。 如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。  
  
 這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。 若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。 根據預設，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 會安裝至具名執行個體。  
  
 使用 odbc32.lib 編譯。  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // sample uses Integrated Security, create SQL Server DSN using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log long-running queries, including the file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_LOG, &"odbcqry.log", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the long-running query interval (in milliseconds).  Note that for version 2.50 and 2.65  
   // drivers, this value is specified in seconds, not milliseconds.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_INTERVAL, (SQLPOINTER)3000, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the long-running query log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle then execute commands.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
           return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [分析 ODBC 驅動程式效能的如何主題&#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-odbc.md)  
  
  
