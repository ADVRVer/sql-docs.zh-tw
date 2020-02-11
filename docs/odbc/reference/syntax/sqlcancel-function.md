---
title: SQLCancel 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCancel
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCancel
helpviewer_keywords:
- SQLCancel function [ODBC]
ms.assetid: ac0b5972-627f-4440-8c5a-0e8da728726d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 94f823cdefe4b3e5a62beb62062356dad3a88a03
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036123"
---
# <a name="sqlcancel-function"></a>SQLCancel 函式
**標準**  
 引進的版本： ODBC 1.0 標準合規性： ISO 92  
  
 **摘要**  
 **SQLCancel**會取消語句的處理。  
  
 若要取消對連接或語句的處理，請使用[SQLCancelHandle 函數](../../../odbc/reference/syntax/sqlcancelhandle-function.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
SQLRETURN SQLCancel(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引數  
 *StatementHandle*  
 源語句控制碼。  
  
## <a name="returns"></a>傳回值  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR 或 SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLCancel**傳回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO 時，可以藉由呼叫具有 SQL_HANDLE_STMT *HandleType*和*StatementHandle**控制碼*的**SQLGetDiagRec**來取得相關聯的 SQLSTATE 值。 下表列出**SQLCancel**常傳回的 SQLSTATE 值，並在此函式的內容中說明每一個值;「（DM）」標記法優先于驅動程式管理員所傳回之 SQLSTATEs 的描述。 除非另有說明，否則，與每個 SQLSTATE 值相關聯的傳回碼都是 SQL_ERROR。  
  
|SQLSTATE|錯誤|描述|  
|--------------|-----------|-----------------|  
|01000|一般警告|驅動程式特定的參考用訊息。 （函數會傳回 SQL_SUCCESS_WITH_INFO）。|  
|HY000|一般錯誤|發生錯誤，但沒有任何特定 SQLSTATE，且未定義任何執行特定的 SQLSTATE。 [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)在引數* \*MessageText*緩衝區中傳回的錯誤訊息描述錯誤及其原因。|  
|HY001|記憶體配置錯誤|驅動程式無法配置支援執行或完成函數所需的記憶體。|  
|HY010|函數順序錯誤|（DM）已針對與*StatementHandle*相關聯的連接控制碼呼叫以非同步方式執行的函式。 呼叫**SQLCancel**函數時，這個非同步函式仍在執行中。<br /><br /> （DM）取消作業失敗，因為在與*StatementHandle*相關聯的連接控制碼上進行非同步作業。|  
|HY013|記憶體管理錯誤|無法處理函數呼叫，因為無法存取基礎記憶體物件，可能是因為記憶體不足的狀況。|  
|HY018|伺服器拒絕取消要求|伺服器已拒絕取消要求。|  
|HY117|連接因未知的交易狀態而暫停。 僅允許中斷連線和唯讀功能。|（DM）如需暫停狀態的詳細資訊，請參閱[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)函式。|  
|HYT01|連接逾時已過期|在資料來源回應要求之前，連接逾時時間已過期。 連接逾時時間是透過**SQLSetConnectAttr**設定，SQL_ATTR_CONNECTION_TIMEOUT。|  
|IM001|驅動程式不支援此功能|（DM）與*StatementHandle*相關聯的驅動程式不支援此功能。|  
  
## <a name="comments"></a>註解  
 **SQLCancel**可以取消語句上的下列處理類型：  
  
-   在語句上以非同步方式執行的函式。  
  
-   語句上需要資料的函數。  
  
-   在另一個執行緒上的語句上執行的函式。  
  
 在 ODBC 2 中。*x*，如果應用程式在未于語句上進行處理時呼叫**SQLCancel** ，則**SQLCancel**與使用 SQL_CLOSE 選項的**SQLFreeStmt**具有相同的效果。此行為僅針對完整性而定義，而應用程式應該呼叫**SQLFreeStmt**或**SQLCloseCursor**來關閉資料指標。  
  
 當呼叫**SQLCancel**來取消在語句中以非同步方式執行的函式，或在需要資料的語句上使用函式時，會清除已取消之函式所張貼的診斷記錄，而**SQLCancel**會張貼自己的診斷記錄;不過，呼叫**SQLCancel**來取消在另一個執行緒上的語句上執行的函式時，不會清除已取消之函式的診斷記錄，也不會張貼自己的診斷記錄。  
  
## <a name="canceling-asynchronous-processing"></a>取消非同步處理  
 在應用程式以非同步方式呼叫函式之後，它會重複呼叫函式，以判斷它是否已完成處理。 如果函數仍在處理中，它會傳回 SQL_STILL_EXECUTING。 如果函式已完成處理，則會傳回不同的程式碼。  
  
 在呼叫傳回 SQL_STILL_EXECUTING 的函式之後，應用程式可以呼叫**SQLCancel**來取消函數。 如果取消要求成功，驅動程式會傳回 SQL_SUCCESS。 此訊息不表示已實際取消函式;這表示已處理取消要求。 當或如果函式實際上已取消，則會與驅動程式相依且與資料來源相關。 應用程式必須繼續呼叫原始函式，直到傳回碼不 SQL_STILL_EXECUTING 為止。 如果已成功取消函式，則傳回碼為 SQL_ERROR 並 SQLSTATE HY008 （作業已取消）。 如果函式已完成其正常處理，則傳回碼會 SQL_SUCCESS 或 SQL_SUCCESS_WITH_INFO 如果函式成功或 SQL_ERROR，則為，如果函式失敗，則為 HY008 （作業已取消）以外的 SQLSTATE。  
  
> [!NOTE]  
>  在 ODBC 3.5 中，不會在語句上進行任何處理時呼叫**SQLCancel** ，而是不會將它視為具有 SQL_CLOSE 選項的**SQLFreeStmt** ，但完全不會有任何作用。 若要關閉資料指標，應用程式應該呼叫**SQLCloseCursor**，而不是**SQLCancel**。  
  
 如需非同步處理的詳細資訊，請參閱[非同步執行](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)。  
  
## <a name="canceling-functions-that-need-data"></a>取消需要資料的函數  
 在**SQLExecute**或**SQLExecDirect**傳回 SQL_NEED_DATA，而且在傳送所有資料執行中參數的資料之前，應用程式可以呼叫**SQLCancel**來取消語句執行。 在取消語句之後，應用程式可以再次呼叫**SQLExecute**或**SQLExecDirect** 。 如需詳細資訊，請參閱[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)。  
  
 在**SQLBulkOperations**或**SQLSetPos**傳回 SQL_NEED_DATA，而且在傳送資料到執行中的所有資料行之前，應用程式可以呼叫**SQLCancel**來取消作業。 取消作業之後，應用程式可以再次呼叫**SQLBulkOperations**或**SQLSetPos** ;取消不會影響資料指標狀態或目前的資料指標位置。 如需詳細資訊，請參閱[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)或[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)。  
  
## <a name="canceling-functions-executing-on-another-thread"></a>取消在另一個執行緒上執行的函式  
 在多執行緒應用程式中，應用程式可以取消正在另一個執行緒上執行的函式。 若要取消函式，應用程式會以目標函式所使用的相同語句控制碼呼叫**SQLCancel** ，但在不同的執行緒上。 函式的取消方式取決於驅動程式和作業系統。 就像取消以非同步方式執行的函式一樣， **SQLCancel**的傳回碼只會指出驅動程式是否已成功處理要求。 只能傳回 SQL_SUCCESS 或 SQL_ERROR;不會傳回任何診斷資訊。 如果已取消原始函式，它會傳回 SQL_ERROR 並 SQLSTATE HY008 （作業已取消）。  
  
 如果在另一個執行緒上呼叫**SQLCancel**來取消語句執行時正在執行 SQL 語句，則執行可能會成功，並在取消也成功時傳回 SQL_SUCCESS。 在此情況下，驅動程式管理員會假設語句執行所開啟的資料指標是由取消所關閉，因此應用程式將無法使用資料指標。  
  
 如需執行緒的詳細資訊，請參閱[多執行緒](../../../odbc/reference/develop-app/multithreading.md)。  
  
## <a name="related-functions"></a>相關函數  
  
|如需下列資訊|請參閱|  
|---------------------------|---------|  
|將緩衝區系結至參數|[SQLBindParameter 函數](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|執行大量插入或更新作業|[SQLBulkOperations 函式](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|除了**SQLCancel**的功能之外，取消在連接控制碼上非同步執行的函式。|[SQLCancelHandle 函式](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|執行 SQL 語句|[SQLExecDirect 函式](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|執行備妥的 SQL 語句|[SQLExecute 函式](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|釋放語句控制碼|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|取得診斷記錄的欄位或診斷標頭的欄位|[SQLGetDiagField 函數](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
|取得診斷資料結構的多個欄位|[SQLGetDiagRec 函式](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
|傳回用來傳送資料的下一個參數|[SQLParamData 函式](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|在執行時間傳送參數資料|[SQLPutData 函數](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|將資料指標定位於資料列集、重新整理資料列集中的資料，或更新或刪除結果集中的資料|[SQLSetPos 函式](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>另請參閱  
 [ODBC API 參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
