---
title: "配置控制代碼並連接到 SQL Server (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 87e3ab58220fd3b24a9e47c68bfa6a23de61f7a1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>配置控制代碼並連接到 SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>配置控制代碼並連接到 SQL Server  
  
1.  加入 ODBC 標頭檔 Sql.h、Sqlext.h、Sqltypes.h。  
  
2.  加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驅動程式專屬的標頭檔 Odbcss.h。  
  
3.  呼叫[SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396)與**HandleType** SQL_HANDLE_ENV 來初始化 ODBC 並配置環境控制代碼。  
  
4.  呼叫[SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)與**屬性**設定為 SQL_ATTR_ODBC_VERSION 並**ValuePtr**設定為 sql_ov_odbc3 時，表示應用程式會使用 ODBC 3.x 格式函式呼叫。  
  
5.  （選擇性） 呼叫[SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)來設定其他環境選項或呼叫[SQLGetEnvAttr](http://go.microsoft.com/fwlink/?LinkId=58403)取得環境選項。  
  
6.  呼叫[SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396)與**HandleType**配置連接控制代碼利用 SQL_HANDLE_DBC。  
  
7.  （選擇性） 呼叫[SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)設定連接選項，或呼叫[SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)來取得連接選項。  
  
8.  呼叫要用於連接到現有的資料來源的 SQLConnect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
     或  
  
     呼叫[SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md)若要使用的連接字串連接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
     完整的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接字串至少擁有下列其中一種形式：  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     如果連接字串不完整， **SQLDriverConnect**可以提示輸入所需的資訊。 這由指定的值控制*DriverCompletion*參數。  
  
     \- 或 -  
  
     呼叫[SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)反覆進行的方式來建立連接字串，並連接到在多次[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
9. （選擇性） 呼叫[SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md)以取得驅動程式屬性和行為[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料來源。  
  
10. 配置與使用陳述式。  
  
11. 呼叫中斷 SQLDisconnect[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]並且讓連接控制代碼可以進行新的連接。  
  
12. 呼叫[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)與**HandleType**來釋放連接控制代碼利用 SQL_HANDLE_DBC。  
  
13. 呼叫**SQLFreeHandle**與**HandleType** SQL_HANDLE_ENV 來釋放環境控制代碼。  
  
> [!IMPORTANT]  
>  盡可能使用 Windows 驗證。 如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。 請避免將認證儲存在檔案中。 如果您必須保存認證，則應該用 [Win32 crypto API](http://go.microsoft.com/fwlink/?LinkId=64532) 加密這些認證。  
  
## <a name="example"></a>範例  
 這個範例會示範呼叫**SQLDriverConnect**連接到的執行個體[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]而不需要現有的 ODBC 資料來源。 藉由傳遞至不完整的連接字串**SQLDriverConnect**，它會使 ODBC 驅動程式會提示使用者輸入遺漏的資訊。  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
