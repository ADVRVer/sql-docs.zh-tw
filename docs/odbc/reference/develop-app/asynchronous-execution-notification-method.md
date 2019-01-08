---
title: 非同步執行 （通知方法） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6aa634f154eb0594c76ae7e65b8d237175a3f92e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52543401"
---
# <a name="asynchronous-execution-notification-method"></a>非同步執行 (通知方法)
ODBC 可讓您連接和陳述式作業的非同步執行。 應用程式執行緒可以處於非同步模式下呼叫 ODBC 函數，並在作業完成時，可讓應用程式執行緒執行其他工作之前，函式可以傳回。 在 Windows 7 SDK 中，針對非同步的陳述式或連接作業，應用程式會判斷非同步作業已完成使用輪詢方法。 如需詳細資訊，請參閱 <<c0> [ 非同步執行 （輪詢的方法）](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)。 從 Windows 8 SDK 中，您就可以判斷非同步作業已完成使用的通知方法。  
  
 在輪詢方法中，應用程式需要呼叫的非同步函式每的次它想要作業的狀態。 通知方法很類似回呼，並且在 ADO.NET 中的等候。 ODBC，不過，會使用 Win32 事件與通知的物件。  
  
 ODBC 資料指標程式庫和 ODBC 非同步通知不能在相同的時間。 將設定這兩個屬性會傳回 SQLSTATE S1119 發生錯誤 （資料指標程式庫和非同步通知無法啟用在相同的時間）。  
  
 請參閱[非同步函式完成的通知](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md)驅動程式開發人員的資訊。  
  
> [!NOTE]  
>  資料指標程式庫不支援的通知方法。 如果它嘗試啟用的通知方法時啟用 SQLSetConnectAttr，透過資料指標程式庫，應用程式會收到錯誤訊息。  
  
## <a name="overview"></a>總覽  
 處於非同步模式下呼叫 ODBC 函數時，會將程式控制權回到呼叫的應用程式立即，傳回碼為 SQL_STILL_EXECUTING。 應用程式必須重複輪詢函式，直到傳回 SQL_STILL_EXECUTING 以外的項目。 輪詢迴圈會增加 CPU 使用率，在許多非同步的情況下導致效能不佳。  
  
 每次使用通知模型時，會停用輪詢模型。 應用程式不應該再次呼叫原始函式。 呼叫[SQLCompleteAsync 函式](../../../odbc/reference/syntax/sqlcompleteasync-function.md)以完成非同步作業。 如果應用程式會在非同步作業完成之前再次呼叫原始函式，呼叫會傳回 sql_error，其中包含 SQLSTATE IM017 （非同步的 「 通知 」 模式中，已停用輪詢）。  
  
 應用程式使用通知模型時，可以呼叫**SQLCancel**或是**SQLCancelHandle**來取消陳述式或連接的作業。 如果取消要求成功，ODBC 會傳回 SQL_SUCCESS。 此訊息不會指出實際取消函式之;表示已處理取消要求。 是否實際取消函式是驅動程式相依性和資料來源而定。 當取消作業時，驅動程式管理員仍將事件發出信號。 驅動程式管理員會傳回 SQL_ERROR 傳回碼緩衝區中，而狀態是 SQLSTATE HY008 （已取消的作業） 來指出取消是否成功。 如果函式完成其正常的處理程序，驅動程式管理員會傳回 SQL_SUCCESS 或 SQL_SUCCESS_WITH_INFO。  
  
### <a name="downlevel-behavior"></a>舊版的行為  
 ODBC 3.81 上完整支援這項通知的 ODBC 驅動程式管理員版本。  
  
|應用程式的 ODBC 版本|驅動程式管理員版本|驅動程式版本|行為|  
|------------------------------|----------------------------|--------------------|--------------|  
|新的應用程式的任何 ODBC 版本|ODBC 3.81|ODBC 3.80 驅動程式|應用程式可以使用這項功能，如果驅動程式支援這項功能，否則驅動程式管理員會發生錯誤。|  
|新的應用程式的任何 ODBC 版本|ODBC 3.81|Pre-ODBC 3.80 驅動程式|如果驅動程式不支援這項功能，驅動程式管理員將會發生錯誤。|  
|新的應用程式的任何 ODBC 版本|Pre-ODBC 3.81|任意|當應用程式會使用這項功能時，舊的驅動程式管理員會將新的屬性，為驅動程式特定屬性，且驅動程式應該發生錯誤。新的驅動程式管理員會將這些屬性傳遞至驅動程式。|  
  
 應用程式應該檢查驅動程式管理員版本，才能使用此功能。 否則，如果撰寫不夠周全的驅動程式不發生錯誤，驅動程式管理員版本會預先 ODBC 3.81 行為未定義。  
  
## <a name="use-cases"></a>使用案例  
 此區段會顯示針對非同步執行和的輪詢機制的使用案例。  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>整合多個 ODBC 來源的資料  
 資料整合應用程式以非同步方式擷取多個資料來源的資料。 某些資料來自遠端資料來源，有些資料會從本機檔案。 應用程式無法繼續，直到非同步作業完成為止。  
  
 而不是重複輪詢作業，以判斷它是否完整，應用程式可以建立事件物件，並與 ODBC 連接控制代碼或 ODBC 陳述式控制代碼建立關聯。 接著，應用程式呼叫作業系統的同步處理等候上一個事件的物件或許多事件物件 （ODBC 事件和其他的 Windows 事件） 的 Api。 對應的 ODBC 非同步作業完成時，ODBC 會發出信號的事件物件。  
  
 在 Windows 中，將會使用 Win32 事件物件，會為使用者提供統一的程式設計模型。 其他平台上的驅動程式管理員可以使用這些平台特定的事件物件實作。  
  
 下列程式碼範例示範如何使用連接和陳述式的非同步通知：  
  
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
 ODBC 應用程式可以決定 ODBC 驅動程式是否支援非同步通知，藉由呼叫[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)。 ODBC 驅動程式管理員會因此呼叫**SQLGetInfo** SQL_ASYNC_NOTIFICATION 與驅動程式。  
  
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
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Win32 事件處理常式關聯至 ODBC 控制代碼  
 應用程式會負責建立 Win32 事件物件，使用對應的 Win32 函式。 應用程式可以關聯一的 ODBC 連接控制代碼或一的 ODBC 陳述式控制代碼的一個 Win32 事件處理常式。  
  
 連接屬性 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 和 SQL_ATTR_ASYNC_DBC_EVENT 決定 ODBC 是否處於非同步模式下執行，以及 ODBC 是否啟用連接控制代碼的通知模式。 SQL_ATTR_ASYNC_ENABLE 和 SQL_ATTR_ASYNC_STMT_EVENT 的陳述式屬性決定 ODBC 是否處於非同步模式下執行，以及 ODBC 是否啟用的陳述式控制代碼的通知模式。  
  
|SQL_ATTR_ASYNC_ENABLE 或 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENT 或 SQL_ATTR_ASYNC_DBC_EVENT|模式|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|啟用|非 null|非同步通知|  
|啟用|null|非同步輪詢|  
|Disable|任意|同步的|  
  
 應用程式可以暫時停用非同步作業模式。 如果連接層級的非同步作業已停用，則 ODBC 會略過 SQL_ATTR_ASYNC_DBC_EVENT 的值。 如果陳述式層級的非同步作業已停用，則 ODBC 會略過 SQL_ATTR_ASYNC_STMT_EVENT 的值。  
  
 同步呼叫**SQLSetStmtAttr**和**SQLSetConnectAttr**  
 -   **SQLSetConnectAttr**支援非同步作業，但引動過程**SQLSetConnectAttr**設 SQL_ATTR_ASYNC_DBC_EVENT 一定是同步。  
  
-   **SQLSetStmtAttr**不支援非同步執行。  
  
 錯誤外案例  
 當**SQLSetConnectAttr**進行連接，驅動程式管理員無法判斷要使用哪一個驅動程式之前呼叫。 因此，驅動程式管理員會傳回成功**SQLSetConnectAttr**但可能無法準備好在驅動程式中設定屬性。 驅動程式管理員將會在應用程式呼叫的連線函式時，設定這些屬性。 驅動程式管理員可能會錯誤外，因為驅動程式不支援非同步作業。  
  
 連接屬性的繼承  
 通常，連接的陳述式會繼承連接屬性。 不過，屬性 SQL_ATTR_ASYNC_DBC_EVENT 是不可繼承的而且只會影響連接作業。  
  
 ODBC 連接控制代碼相關聯的事件處理常式，ODBC 應用程式呼叫 ODBC API **SQLSetConnectAttr** ，並指定 SQL_ATTR_ASYNC_DBC_EVENT 屬性和事件處理的屬性值。 新的 ODBC 屬性 SQL_ATTR_ASYNC_DBC_EVENT 屬於型別 SQL_IS_POINTER。  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 通常，應用程式建立自動重設事件物件。 ODBC 不會重設事件的物件。 應用程式必須確定該物件不是處於收到信號的狀態之前呼叫任何非同步的 ODBC 函式。  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENT 是驅動程式管理員專用的屬性，將不會設定驅動程式中。  
  
 SQL_ATTR_ASYNC_DBC_EVENT 的預設值是 NULL。 取得或設定 SQL_ATTR_ASYNC_DBC_EVENT 如果驅動程式不支援非同步通知，將會傳回 sql_error，其中包含 SQLSTATE HY092 （無效的屬性/選項識別碼）。  
  
 如果最後一個 SQL_ATTR_ASYNC_DBC_EVENT 值上設定 ODBC 連接控制代碼不是 NULL，並藉由設定屬性與 SQL_ASYNC_DBC_ENABLE_ON，呼叫任何 ODBC 連接 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 啟用非同步模式的應用程式支援非同步模式的函式會完成通知。 如果設定 ODBC 連接控制代碼上的最後一個 SQL_ATTR_ASYNC_DBC_EVENT 值是 NULL，ODBC 不會傳送應用程式任何通知，不論是否啟用非同步模式。  
  
 應用程式可以設定 SQL_ATTR_ASYNC_DBC_EVENT 之前或之後設定 SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE 的屬性。  
  
 應用程式可以設定 ODBC 連接控制代碼上 SQL_ATTR_ASYNC_DBC_EVENT 屬性之前呼叫連線函式 (**SQLConnect**， **SQLBrowseConnect**，或**SQLDriverConnect**)。 ODBC 驅動程式管理員不知道應用程式將使用的 ODBC 驅動程式，因為它會傳回 SQL_SUCCESS。 當應用程式呼叫的連線函式時，ODBC 驅動程式管理員會檢查驅動程式是否支援非同步通知。 如果驅動程式不支援非同步通知，ODBC 驅動程式管理員會傳回 sql_error，其中包含 SQLSTATE S1_118 （驅動程式不支援非同步通知）。 如果驅動程式支援非同步通知，ODBC 驅動程式管理員將會呼叫此驅動程式，並設定 SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK 和 SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT 對應的屬性。  
  
 同樣地，應用程式呼叫**SQLSetStmtAttr** ODBC 陳述式處理，並指定 SQL_ATTR_ASYNC_STMT_EVENT 屬性，啟用或停用陳述式層級的非同步通知。 因為陳述式的函式一律會呼叫後建立連線時， **SQLSetStmtAttr**會傳回 sql_error，其中包含 SQLSTATE S1_118 （驅動程式不支援非同步通知） 時，立即對應驅動程式不支援非同步作業，或驅動程式支援非同步作業，但不支援非同步通知。  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENT，可以設為 NULL，會將不會設定驅動程式中的驅動程式管理員專用屬性。  
  
 SQL_ATTR_ASYNC_STMT_EVENT 的預設值是 NULL。 如果驅動程式不支援非同步通知，取得或設定 SQL_ATTR_ASYNC_ STMT_EVENT 屬性會傳回 sql_error，其中包含 SQLSTATE HY092 （無效的屬性/選項識別碼）。  
  
 應用程式應該不會與多個 ODBC 控制代碼關聯相同的事件控制代碼。 否則，一則通知將會遺失如果兩個非同步的 ODBC 函式叫用完成共用相同的事件控制代碼的兩個控制代碼。 若要避免連接控制代碼從繼承相同的事件控制代碼的陳述式控制代碼，ODBC 會傳回 sql_error，其中包含 SQLSTATE IM016 （無法陳述式將屬性設定成連接控制代碼），如果應用程式在連接控制代碼上設定 SQL_ATTR_ASYNC_STMT_EVENT。  
  
### <a name="calling-asynchronous-odbc-functions"></a>呼叫非同步的 ODBC 函式  
 啟用非同步通知，並啟動非同步作業之後, 應用程式可以呼叫任何 ODBC 函數。 如果函式所屬支援非同步作業的函式集，應用程式會完成通知的作業完成後，不論是否函式會失敗或成功。  唯一的例外是應用程式呼叫 ODBC 函數的無效連接或陳述式控制代碼。 在此情況下，ODBC 會不取得的事件控制代碼，並將它設定為收到信號的狀態。  
  
 應用程式必須確定相關聯的事件物件會在未收到信號的狀態啟動對應的 ODBC 控制代碼上的非同步作業之前。 ODBC 不會重設事件的物件。  
  
### <a name="getting-notification-from-odbc"></a>從 ODBC 取得通知  
 應用程式執行緒可以呼叫**WaitForSingleObject**等候上一個事件處理常式或呼叫**WaitForMultipleObjects**等候事件控制代碼的陣列，並暫停直到其中一個或所有事件物件變成已收到訊號或已超過逾時間隔。  
  
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
