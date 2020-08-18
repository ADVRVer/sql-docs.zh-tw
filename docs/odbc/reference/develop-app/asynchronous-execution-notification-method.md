---
description: 非同步執行 (通知方法)
title: 非同步執行 (通知方法) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19c201d71d42c40277ad67cef25922e55e97de12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483121"
---
# <a name="asynchronous-execution-notification-method"></a>非同步執行 (通知方法)
ODBC 允許非同步執行連接和語句作業。 應用程式執行緒可以在非同步模式中呼叫 ODBC 函數，而且函式可以在作業完成之前傳回，讓應用程式執行緒執行其他工作。 在 Windows 7 SDK 中，針對非同步語句或連接作業，應用程式會使用輪詢方法來判斷非同步作業已完成。 如需詳細資訊，請參閱 [非同步執行 (輪詢方法) ](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)。 從 Windows 8 SDK 開始，您可以使用通知方法來判斷非同步作業是否已完成。  
  
 在輪詢方法中，應用程式需要在每次需要作業的狀態時呼叫非同步函式。 通知方法類似于回呼並等候 ADO.NET。 但是，ODBC 會使用 Win32 事件作為通知物件。  
  
 ODBC 資料指標程式庫和 ODBC 非同步通知不能同時使用。 設定這兩個屬性將會傳回 SQLSTATE S1119 (資料指標程式庫的錯誤，而且無法同時啟用非同步通知) 。  
  
 如需驅動程式開發人員的資訊，請參閱非同步函式 [完成的通知](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md) 。  
  
> [!NOTE]  
>  資料指標程式庫不支援通知方法。 如果應用程式嘗試在啟用通知方法時透過 SQLSetConnectAttr 啟用資料指標程式庫，則會收到錯誤訊息。  
  
## <a name="overview"></a>概觀  
 在非同步模式中呼叫 ODBC 函數時，會立即將控制項傳回給呼叫的應用程式，並 SQL_STILL_EXECUTING 傳回碼。 應用程式必須重複輪詢函式，直到它傳回 SQL_STILL_EXECUTING 以外的內容為止。 輪詢迴圈會增加 CPU 使用率，在許多非同步案例中造成效能不佳。  
  
 每當使用通知模型時，就會停用輪詢模型。 應用程式不應該再次呼叫原始函數。 呼叫 [SQLCompleteAsync 函數](../../../odbc/reference/syntax/sqlcompleteasync-function.md) 來完成非同步作業。 如果在非同步作業完成之前，應用程式再次呼叫原始函式，則呼叫會傳回 SQL_ERROR，且 SQLSTATE IM017 (輪詢會在非同步通知模式) 中停用。  
  
 使用通知模型時，應用程式可以呼叫 **SQLCancel** 或 **SQLCancelHandle** 來取消語句或連接作業。 如果取消要求成功，ODBC 將會傳回 SQL_SUCCESS。 此訊息不表示函式實際上已取消;指出已處理取消要求。 是否真的取消函式與驅動程式相依，而且與資料來源相依。 當作業取消時，驅動程式管理員仍會發出事件的信號。 驅動程式管理員會在傳回碼緩衝區中傳回 SQL_ERROR，且狀態為 [已取消] 的 [SQLSTATE HY008] ([作業取消]) 表示取消成功。 如果函式已完成正常處理，驅動程式管理員會傳回 SQL_SUCCESS 或 SQL_SUCCESS_WITH_INFO。  
  
### <a name="downlevel-behavior"></a>下層行為  
 在完成時支援此通知的 ODBC 驅動程式管理員版本是 ODBC 3.81。  
  
|應用程式 ODBC 版本|驅動程式管理員版本|驅動程式版本|行為|  
|------------------------------|----------------------------|--------------------|--------------|  
|任何 ODBC 版本的新應用程式|ODBC 3.81|ODBC 3.80 驅動程式|如果驅動程式支援這項功能，應用程式可以使用這項功能，否則驅動程式管理員將會發生錯誤。|  
|任何 ODBC 版本的新應用程式|ODBC 3.81|預先 ODBC 3.80 驅動程式|如果驅動程式不支援此功能，驅動程式管理員將會發生錯誤。|  
|任何 ODBC 版本的新應用程式|預先 ODBC 3.81|任意|當應用程式使用這項功能時，舊的驅動程式管理員會將新的屬性視為驅動程式特定的屬性，而且驅動程式應該會發生錯誤。新的驅動程式管理員不會將這些屬性傳遞至驅動程式。|  
  
 應用程式在使用這項功能之前，應該先檢查驅動程式管理員版本。 否則，如果撰寫不佳的驅動程式未發生錯誤，且驅動程式管理員版本是預先 ODBC 3.81，則行為是未定義的。  
  
## <a name="use-cases"></a>使用案例  
 本節說明非同步執行和輪詢機制的使用案例。  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>整合多個 ODBC 來源的資料  
 資料整合應用程式會以非同步方式從多個資料來源提取資料。 有些資料來自遠端資料源，有些資料來自本機檔案。 在非同步作業完成之前，應用程式無法繼續。  
  
 應用程式可以建立事件物件，並將它與 ODBC 連接控制碼或 ODBC 語句控制碼建立關聯，而不是重複輪詢作業來判斷是否已完成。 然後，應用程式會呼叫作業系統同步處理 Api 來等候一個事件物件或許多事件物件， (ODBC 事件和其他 Windows 事件) 。 當對應的 ODBC 非同步作業完成時，ODBC 會對事件物件發出信號。  
  
 在 Windows 上，將會使用 Win32 事件物件，並且會提供使用者統一的程式設計模型。 其他平臺上的驅動程式管理員可以使用這些平臺特定的事件物件執行。  
  
 下列程式碼範例將示範如何使用連接和語句非同步通知：  
  
```  
// This function opens NUMBER_OPERATIONS connections and executes one query on statement of each connection.  
// Asynchronous Notification is used  
  
#define NUMBER_OPERATIONS 5  
int AsyncNotificationSample(void)  
{  
    RETCODE     rc;  
  
    SQLHENV     hEnv              = NULL;  
    SQLHDBC     arhDbc[NUMBER_OPERATIONS]         = {NULL};  
    SQLHSTMT    arhStmt[NUMBER_OPERATIONS]        = {NULL};  
  
    HANDLE      arhDBCEvent[NUMBER_OPERATIONS]    = {NULL};  
    RETCODE     arrcDBC[NUMBER_OPERATIONS]        = {0};  
    HANDLE      arhSTMTEvent[NUMBER_OPERATIONS]   = {NULL};  
    RETCODE     arrcSTMT[NUMBER_OPERATIONS]       = {0};  
  
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &hEnv);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    rc = SQLSetEnvAttr(hEnv,  
        SQL_ATTR_ODBC_VERSION,  
        (SQLPOINTER) SQL_OV_ODBC3_80,  
        SQL_IS_INTEGER);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    // Connection operations begin here  
  
    // Alloc NUMBER_OPERATIONS connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_DBC, hEnv, &arhDbc[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable DBC Async on all connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE, (SQLPOINTER)SQL_ASYNC_DBC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Application must create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhDBCEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhDBCEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all connection handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_EVENT, arhDBCEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate connect establishing  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLDriverConnect(arhDbc[i], NULL, (SQLTCHAR*)TEXT("Driver={ODBC Driver 11 for SQL Server};SERVER=dp-srv-sql2k;DATABASE=pubs;UID=sa;PWD=XYZ;"), SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE); // Wait All  
  
    // Complete connect API calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], & arrcDBC[i]);  
    }  
  
    BOOL fFail = FALSE; // Whether some connection openning fails.  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcDBC[i]) )   
            fFail = TRUE;  
    }  
  
    // If some SQLDriverConnect() fail, clean up.  
    if (fFail)  
    {  
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {  
                SQLDisconnect(arhDbc[i]); // This is also async  
            }  
            else  
            {  
                SetEvent(arhDBCEvent[i]); // Previous SQLDriverConnect() failed. No need to call SQLDisconnect().  
            }  
        }  
        WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE);   
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {     
                SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], &arrcDBC[i]);; // To Complete  
            }  
        }  
  
        goto Cleanup;  
    }  
  
    // Statement Operations begin here  
  
    // Alloc statement handle  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_STMT, arhDbc[i], &arhStmt[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable STMT Async on all statement handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_ENABLE, (SQLPOINTER)SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhSTMTEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhSTMTEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all statement handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_STMT_EVENT, arhSTMTEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate SQLExecDirect() calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLExecDirect(arhStmt[i], (SQLTCHAR*)TEXT("select au_lname, au_fname from authors"), SQL_NTS);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE); // Wait All  
  
    // Now, call SQLCompleteAsync to complete the operation and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return values  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        //Do some binding jobs here, set SQL_ATTR_ROW_ARRAY_SIZE   
    }  
  
    // Now, initiate fetching  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLFetch(arhStmt[i]);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE);   
  
    // Now, to complete the operations and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    // USE fetched data here!!  
  
Cleanup:  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhStmt[NUMBER_OPERATIONS])  
        {  
            SQLFreeHandle(SQL_HANDLE_STMT, arhStmt[i]);  
            arhStmt[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhSTMTEvent[i])  
        {  
            CloseHandle(arhSTMTEvent[i]);  
            arhSTMTEvent[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDbc[i])  
        {  
            SQLFreeHandle(SQL_HANDLE_DBC, arhDbc[i]);  
            arhDbc[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDBCEvent[i])  
        {  
            CloseHandle(arhDBCEvent[i]);  
            arhDBCEvent[i] = NULL;  
        }  
    }  
  
    if (hEnv)  
    {  
        SQLFreeHandle(SQL_HANDLE_ENV, hEnv);  
        hEnv = NULL;  
    }  
  
    return 0;  
}  
  
```  
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>判斷驅動程式是否支援非同步通知  
 ODBC 應用程式可以藉由呼叫 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)來判斷 odbc 驅動程式是否支援非同步通知。 ODBC 驅動程式管理員將會使用 SQL_ASYNC_NOTIFICATION 來呼叫驅動程式的 **SQLGetInfo** 。  
  
```  
SQLUINTEGER InfoValue;  
SQLLEN      cbInfoLength;  
  
SQLRETURN retcode;  
retcode = SQLGetInfo (hDbc,   
                      SQL_ASYNC_NOTIFICATION,   
                      &InfoValue,  
                      sizeof(InfoValue),  
                      NULL);  
if (SQL_SUCCEEDED(retcode))  
{  
if (SQL_ASYNC_NOTIFICATION_CAPABLE == InfoValue)  
      {  
          // The driver supports asynchronous notification  
      }  
      else if (SQL_ASYNC_NOTIFICATION_NOT_CAPABLE == InfoValue)  
      {  
          // The driver does not support asynchronous notification  
      }  
}  
```  
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>建立 Win32 事件控制碼與 ODBC 控制碼的關聯  
 應用程式會負責使用對應的 Win32 函數建立 Win32 事件物件。 應用程式可以將一個 Win32 事件控制碼與一個 ODBC 連接控制碼或一個 ODBC 語句控制碼建立關聯。  
  
 連接屬性 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 和 SQL_ATTR_ASYNC_DBC_EVENT 判斷 ODBC 是否以非同步模式執行，以及 ODBC 是否針對連接控制碼啟用通知模式。 語句屬性 SQL_ATTR_ASYNC_ENABLE 和 SQL_ATTR_ASYNC_STMT_EVENT 判斷 ODBC 是否以非同步模式執行，以及 ODBC 是否針對語句控制碼啟用通知模式。  
  
|SQL_ATTR_ASYNC_ENABLE 或 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT 或 SQL_ATTR_ASYNC_DBC_EVENT|[模式]|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|啟用|非 null|非同步通知|  
|啟用|null|非同步輪詢|  
|停用|任意|同步|  
  
 應用程式可以暫時停用非同步作業模式。 如果已停用連接層級非同步作業，ODBC 會忽略 SQL_ATTR_ASYNC_DBC_EVENT 的值。 如果停用語句層級非同步作業，ODBC 會忽略 SQL_ATTR_ASYNC_STMT_EVENT 的值。  
  
 **SQLSetStmtAttr**和**SQLSetConnectAttr**的同步呼叫  
 -   **SQLSetConnectAttr** 支援非同步作業，但是叫用 **SQLSetConnectAttr** 來設定 SQL_ATTR_ASYNC_DBC_EVENT 一律為同步。  
  
-   **SQLSetStmtAttr** 不支援非同步執行。  
  
 錯誤輸出案例  
 在建立連接之前呼叫 **SQLSetConnectAttr** 時，驅動程式管理員無法判斷要使用哪一個驅動程式。 因此，驅動程式管理員會傳回成功的 **SQLSetConnectAttr** ，但該屬性可能尚未準備好在驅動程式中設定。 當應用程式呼叫連接函數時，驅動程式管理員會設定這些屬性。 驅動程式管理員可能會因為驅動程式不支援非同步作業而發生錯誤。  
  
 連接屬性的繼承  
 通常，連接的語句將會繼承連接屬性。 不過，屬性 SQL_ATTR_ASYNC_DBC_EVENT 不是可繼承的，而且只會影響連接作業。  
  
 為了將事件控制碼與 ODBC 連接控制碼建立關聯，ODBC 應用程式會呼叫 ODBC API **SQLSetConnectAttr** ，並將 SQL_ATTR_ASYNC_DBC_EVENT 指定為屬性，並將事件控制碼指定為屬性值。 新的 ODBC 屬性 SQL_ATTR_ASYNC_DBC_EVENT 是 SQL_IS_POINTER 類型。  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 通常，應用程式會建立自動重設事件物件。 ODBC 不會重設事件物件。 應用程式必須確定在呼叫任何非同步 ODBC 函式之前，物件不是處於已發出信號的狀態。  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT 是驅動程式管理員專用的屬性，不會在驅動程式中設定。  
  
 SQL_ATTR_ASYNC_DBC_EVENT 的預設值為 Null。 如果驅動程式不支援非同步通知，取得或設定 SQL_ATTR_ASYNC_DBC_EVENT 將會傳回具有 SQLSTATE HY092 的 SQL_ERROR (不正確屬性/選項識別碼) 。  
  
 如果 ODBC 連接控制碼上設定的最後一個 SQL_ATTR_ASYNC_DBC_EVENT 值不是 Null，而且應用程式已啟用非同步模式，其方式是設定屬性 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 與 SQL_ASYNC_DBC_ENABLE_ON，則呼叫支援非同步模式的任何 ODBC 連接函數都會得到完成通知。 如果 ODBC 連接控制碼上設定的最後一個 SQL_ATTR_ASYNC_DBC_EVENT 值為 Null，則不論是否啟用非同步模式，ODBC 都不會傳送任何通知給應用程式。  
  
 應用程式可以在設定屬性 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 之前或之後設定 SQL_ATTR_ASYNC_DBC_EVENT。  
  
 在呼叫連接函數 (**SQLConnect**、 **SQLBrowseConnect**或 **SQLDriverConnect**) 之前，應用程式可以設定 ODBC 連接控制碼上的 SQL_ATTR_ASYNC_DBC_EVENT 屬性。 由於 ODBC 驅動程式管理員不知道應用程式將使用哪一個 ODBC 驅動程式，因此它會傳回 SQL_SUCCESS。 當應用程式呼叫連接函數時，ODBC 驅動程式管理員會檢查驅動程式是否支援非同步通知。 如果驅動程式不支援非同步通知，ODBC 驅動程式管理員將會傳回 SQL_ERROR 與 SQLSTATE S1_118 (驅動程式不支援非同步通知) 。 如果驅動程式支援非同步通知，ODBC 驅動程式管理員會呼叫驅動程式，並將對應的屬性 SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK 和 SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT。  
  
 同樣地，應用程式會呼叫 ODBC 語句控制碼上的 **SQLSetStmtAttr** ，並指定要啟用或停用語句層級非同步通知的 SQL_ATTR_ASYNC_STMT_EVENT 屬性。 因為在建立連接之後一律會呼叫語句函式，所以 **SQLSetStmtAttr** 會傳回具有 S1_118 SQLSTATE 的 SQL_ERROR， (驅動程式會在對應的驅動程式不支援非同步作業，或者驅動程式支援非同步作業，但不支援非同步通知時，立即支援非同步通知) 。  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT （可以設定為 Null）是驅動程式管理員專用的屬性，不會在驅動程式中設定。  
  
 SQL_ATTR_ASYNC_STMT_EVENT 的預設值為 Null。 如果驅動程式不支援非同步通知，取得或設定 SQL_ATTR_ASYNC_ STMT_EVENT 屬性將會傳回具有 SQLSTATE HY092 的 SQL_ERROR (不正確屬性/選項識別碼) 。  
  
 應用程式不應該讓相同的事件控制碼與一個以上的 ODBC 控制碼產生關聯。 否則，如果在兩個共用相同事件控制碼的控制碼上完成兩個非同步 ODBC 函式呼叫，則會遺失一個通知。 為了避免語句控制碼繼承連接控制碼的相同事件控制碼，ODBC 會傳回 SQL_ERROR with SQLSTATE IM016 (如果應用程式在連接控制碼上設定 SQL_ATTR_ASYNC_STMT_EVENT，則無法將語句屬性設定為連接控制碼) 。  
  
### <a name="calling-asynchronous-odbc-functions"></a>呼叫非同步 ODBC 函數  
 啟用非同步通知並啟動非同步作業之後，應用程式就可以呼叫任何 ODBC 函數。 如果函式屬於支援非同步作業的函式集合，則不論函式是否失敗或成功，應用程式都將會在作業完成時取得完成通知。  唯一的例外是應用程式會使用不正確連接或語句控制碼來呼叫 ODBC 函數。 在此情況下，ODBC 不會取得事件控制碼，並將其設定為已發出信號的狀態。  
  
 應用程式必須先確定關聯的事件物件處於非信號狀態，然後才在對應的 ODBC 控制碼上啟動非同步作業。 ODBC 不會重設事件物件。  
  
### <a name="getting-notification-from-odbc"></a>從 ODBC 取得通知  
 應用程式執行緒可以呼叫 **WaitForSingleObject** 來等候一個事件處理常式，或呼叫 **WaitForMultipleObjects** 來等候事件控制碼的陣列，並將其暫止，直到其中一個或所有事件物件變成發出信號或逾時間隔為止。  
  
```  
DWORD dwStatus = WaitForSingleObject(  
                        hEvent,  // The event associated with the ODBC handle  
                        5000     // timeout is 5000 millisecond   
);  
  
If (dwStatus == WAIT_TIMEOUT)  
{  
    // time-out interval elapsed before all the events are signaled.   
}  
Else  
{  
    // Call the corresponding Asynchronous ODBC API to complete all processing and retrieve the return code.  
}  
```
