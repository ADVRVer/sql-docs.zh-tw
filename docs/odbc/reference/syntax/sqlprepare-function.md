---
description: SQLPrepare 函數
title: SQLPrepare 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPrepare
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPrepare
helpviewer_keywords:
- SQLPrepare function [ODBC]
ms.assetid: 332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3b5d68aae8033b0710ee052b001c7942eb1f7d6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487184"
---
# <a name="sqlprepare-function"></a>SQLPrepare 函數
**一致性**  
 引進的版本： ODBC 1.0 標準合規性： ISO 92  
  
 **總結**  
 **SQLPrepare** 準備要執行的 SQL 字串。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
SQLRETURN SQLPrepare(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     StatementText,  
     SQLINTEGER    TextLength);  
```  
  
## <a name="arguments"></a>引數  
 *StatementHandle*  
 輸出語句控制碼。  
  
 *StatementText*  
 輸出SQL 文字字串。  
  
 *TextLength*  
 輸出**StatementText* 的長度（以字元為單位）。  
  
## <a name="returns"></a>傳回  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR 或 SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLPrepare**傳回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO 時，可以藉由呼叫**SQLGetDiagRec**和*HandleType* （SQL_HANDLE_STMT）和*StatementHandle*的*控制碼*來取得相關聯的 SQLSTATE 值。 下表列出 **SQLPrepare** 常傳回的 SQLSTATE 值，並在此函式的內容中說明每一個值;「 (DM) 」標記法優先于驅動程式管理員所傳回的 SQLSTATEs 描述。 除非另有說明，否則會 SQL_ERROR 與每個 SQLSTATE 值相關聯的傳回碼。  
  
|SQLSTATE|錯誤|描述|  
|--------------|-----------|-----------------|  
|01000|一般警告|驅動程式特定的告知性訊息。  (函數會傳回 SQL_SUCCESS_WITH_INFO。 ) |  
|01S02|選項值已變更|指定的語句屬性無效，因為執行中的工作狀況，所以暫時取代了類似的值。 您可以呼叫 (**SQLGetStmtAttr** 來判斷暫時替代值的值。 ) 替代值對 *StatementHandle* 有效，直到資料指標關閉為止。 可以變更的語句屬性包括： SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE SQL_ATTR_KEYSET_SIZE SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT SQL_ATTR_SIMULATE_CURSOR<br /><br />  (函數會傳回 SQL_SUCCESS_WITH_INFO。 ) |  
|08S01|通訊連結失敗|在函式完成處理之前，驅動程式與連接驅動程式的資料來源之間的通訊連結失敗。|  
|21S01|插入值清單與資料行清單不相符|\**StatementText* 包含 **INSERT** 語句，而要插入的值數目不符合衍生資料表的程度。|  
|21S02|衍生資料表的程度與資料行清單不相符|\**StatementText* 包含 **CREATE VIEW** 語句，而指定的名稱數目與查詢規格所定義之衍生資料表的程度不同。|  
|22018|轉換規格的字元值無效|**StatementText* 包含包含常值或參數的 SQL 語句，且值與相關聯之資料表資料行的資料類型不相容。|  
|22019|不正確 escape 字元|引數*StatementText*包含**LIKE**述詞，**其中包含 WHERE**子句中的**escape** ，**而 escape 字元之後的**escape 字元長度不等於1。|  
|22025|不正確 escape 順序|引數*StatementText*在**WHERE**子句中包含「**LIKE** _pattern 值_ **escape** _escape 字元_」，而模式值中的 ESCAPE 字元後面的字元不是 "%" 或 "_"。|  
|24000|指標狀態無效| (DM) 在 *StatementHandle*上開啟資料指標，且已呼叫 **SQLFetch** 或 **SQLFetchScroll** 。<br /><br /> 在 *StatementHandle*上開啟了資料指標，但尚未呼叫 **SQLFetch** 或 **SQLFetchScroll** 。|  
|34000|指標名稱無效|\**StatementText* 包含已定位的 **DELETE** 或定位的 **更新**，且正在準備的語句所參考的資料指標並未開啟。|  
|3D000|不正確目錄名稱|*StatementText*中指定的目錄名稱無效。|  
|3F000|不正確架構名稱|*StatementText*中指定的架構名稱無效。|  
|42000|語法錯誤或存取違規|\**StatementText* 包含未 preparable 或包含語法錯誤的 SQL 語句。<br /><br /> **StatementText* 包含的語句，使用者沒有必要的許可權。|  
|42S01|基表或視圖已經存在|\**StatementText* 包含 **CREATE TABLE** 或 **CREATE VIEW** 語句，而且指定的資料表名稱或視圖名稱已存在。|  
|42S02|找不到基表或視圖|\**StatementText* 包含 **Drop TABLE** 或 **drop VIEW** 語句，而且指定的資料表名稱或視圖名稱不存在。<br /><br /> \**StatementText* 包含 **ALTER TABLE** 語句，但指定的資料表名稱不存在。<br /><br /> \**StatementText* 包含 **CREATE VIEW** 語句，而且查詢規格所定義的資料表名稱或視圖名稱不存在。<br /><br /> \**StatementText* 包含 **CREATE INDEX** 語句，但指定的資料表名稱不存在。<br /><br /> \**StatementText* 包含 **GRANT** 或 **REVOKE** 語句，且指定的資料表名稱或視圖名稱不存在。<br /><br /> \**StatementText* 包含 **SELECT** 語句，而指定的資料表名稱或視圖名稱不存在。<br /><br /> \**StatementText* 包含 **DELETE**、 **INSERT**或 **UPDATE** 語句，但指定的資料表名稱不存在。<br /><br /> \**StatementText* 包含 **CREATE TABLE** 語句，以及在條件約束中指定的資料表 (參考的資料表不是所建立的資料表) 不存在。|  
|42S11|索引已經存在|\**StatementText* 包含 **CREATE INDEX** 語句，且指定的索引名稱已存在。|  
|42S12|找不到索引|\**StatementText* 包含 **DROP INDEX** 語句，但指定的索引名稱不存在。|  
|42S21|資料行已存在|\**StatementText* 包含 **ALTER TABLE** 語句，而 **ADD** 子句中所指定的資料行不是唯一的，也不會識別基表中的現有資料行。|  
|42S22|找不到資料行|\**StatementText* 包含 **CREATE INDEX** 語句，而且資料行清單中指定的一或多個資料行名稱不存在。<br /><br /> \**StatementText* 包含 **GRANT** 或 **REVOKE** 語句，且指定的資料行名稱不存在。<br /><br /> \**StatementText* 包含 **SELECT**、 **DELETE**、 **INSERT**或 **UPDATE** 語句，但指定的資料行名稱不存在。<br /><br /> \**StatementText* 包含 **CREATE TABLE** 語句，以及在條件約束中指定的資料行 (參考) 不存在的資料表。|  
|HY000|一般錯誤|發生未定義特定 SQLSTATE 的錯誤，且未定義任何執行特定的 SQLSTATE。 **SQLGetDiagRec**在* \* MessageText*緩衝區中傳回的錯誤訊息會描述錯誤及其原因。|  
|HY001|記憶體配置錯誤|驅動程式無法配置支援執行或完成函式所需的記憶體。|  
|HY008|已取消作業|*StatementHandle*已啟用非同步處理。 已呼叫函式，並在它完成執行之前，在*StatementHandle*上呼叫**SQLCancel**或**SQLCancelHandle** ，然後在*StatementHandle*上再次呼叫該函式。<br /><br /> 呼叫函式，並在完成執行之前，從多執行緒應用程式中的不同執行緒在*StatementHandle*上呼叫**SQLCancel**或**SQLCancelHandle** 。|  
|HY009|Null 指標的用法無效| (DM) *StatementText* 為 null 指標。|  
|HY010|函數順序錯誤| (DM) 以非同步方式執行的函式，是與 *StatementHandle*相關聯的連接控制碼所呼叫。 呼叫 **SQLPrepare** 函式時，仍在執行此非同步函式。<br /><br /> 針對*StatementHandle*呼叫**SQLExecute**、 **SQLEXECDIRECT**或**SQLMoreResults** () DM，並傳回 SQL_PARAM_DATA_AVAILABLE。 在抓取所有資料流程參數的資料之前，會呼叫此函數。<br /><br />  (DM) 以非同步方式執行的函式 (不是針對 *StatementHandle* 呼叫這個) ，而且在呼叫此函式時仍在執行。<br /><br /> 針對*StatementHandle*呼叫 (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**或**SQLSetPos** ，並傳回 SQL_NEED_DATA。 在傳送所有資料執行中參數或資料行的資料之前，會呼叫此函數。|  
|HY013|記憶體管理錯誤|無法處理函式呼叫，因為無法存取基礎記憶體物件，可能是因為記憶體不足的情況。|  
|HY090|不正確字串或緩衝區長度| (DM) 引數 *TextLength* 小於或等於0，但不等於 SQL_NTS。|  
|HY117|由於未知的交易狀態，連接已暫止。 只允許中斷連接和唯讀功能。| (DM) 如需暫停狀態的詳細資訊，請參閱 [SQLEndTran 函數](../../../odbc/reference/syntax/sqlendtran-function.md)。|  
|HYC00|未執行選用功能|並行設定對所定義的資料指標類型而言是不正確。<br /><br /> SQL_ATTR_USE_BOOKMARKS 語句屬性已設定為 SQL_UB_VARIABLE，而且 SQL_ATTR_CURSOR_TYPE 語句屬性已設定為驅動程式不支援書簽的資料指標類型。|  
|HYT00|已超過逾時的設定|在資料來源傳回結果集之前已過期的超時時間。 Timeout 期限是透過 **SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT 設定。|  
|HYT01|連接逾時已過期|連接逾時期間已在資料來源回應要求之前過期。 連接逾時期間是透過 **SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT 設定。|  
|IM001|驅動程式不支援此功能| (DM) 與 *StatementHandle* 相關聯的驅動程式不支援此功能。|  
|IM017|非同步通知模式中的輪詢已停用|每當使用通知模型時，就會停用輪詢。|  
|IM018|尚未呼叫**SQLCompleteAsync**來完成這個控制碼上先前的非同步作業。|如果控制碼上先前的函式呼叫傳回 SQL_STILL_EXECUTING，而且如果啟用了通知模式，則必須在控制碼上呼叫 **SQLCompleteAsync** ，以進行後置處理，並完成作業。|  
  
## <a name="comments"></a>註解  
 應用程式會呼叫 **SQLPrepare** ，將 SQL 語句傳送到資料來源以進行準備。 如需備妥執行的詳細資訊，請參閱 [準備執行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)。 應用程式可在 SQL 語句中包含一或多個參數標記。 若要包含參數標記，應用程式會將問號 (？ ) 到 SQL 字串的適當位置。 如需參數的詳細資訊，請參閱 [語句參數](../../../odbc/reference/develop-app/statement-parameters.md)。  
  
> [!NOTE]  
>  如果應用程式使用 **SQLPrepare** 來準備和 **SQLExecute** 提交 **COMMIT** 或 **ROLLBACK** 語句，則 DBMS 產品之間將無法互通。 若要認可或回復交易，請呼叫 **SQLEndTran**。  
  
 驅動程式可以修改語句來使用資料來源所使用的 SQL 形式，然後將它提交到資料來源以進行準備。 尤其是，驅動程式會修改用來定義特定功能之 SQL 語法的 escape 序列。  (如需 SQL 語句文法的說明，請參閱 [ODBC 中的 Escape](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) Sequence 和 [附錄 C： SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)。針對驅動程式，) 語句控制碼類似于內嵌 SQL 程式碼中的語句識別碼。 如果資料來源支援語句識別碼，驅動程式可以將語句識別碼和參數值傳送至資料來源。  
  
 在備妥語句之後，應用程式會使用語句控制碼，在稍後的函式呼叫中參考語句。 您可以藉由呼叫 **SQLExecute** 來重新執行與語句控制碼相關聯的備妥語句，直到應用程式使用 SQL_DROP 選項 **來釋** 出語句，或是在 **SQLPrepare**、 **SQLExecDirect**或其中一個目錄函數的呼叫中使用語句控制碼 (**SQLColumns**、 **SQLTables**) 等等。 當應用程式準備語句之後，它就可以要求有關結果集格式的資訊。 針對某些實作為，在**SQLPrepare**之後呼叫**SQLDescribeCol**或**SQLDescribeParam** ，可能無法像在**SQLExecute**或**SQLExecDirect**之後呼叫函數一樣有效率。  
  
 當應用程式呼叫 **SQLPrepare**時，某些驅動程式無法傳回語法錯誤或存取違規。 驅動程式可以處理語法錯誤和存取違規、只有語法錯誤，或不是語法錯誤或存取違規。 因此，應用程式必須能夠在呼叫後續相關的函式（例如 **SQLNumResultCols**、 **SQLDescribeCol**、 **SQLColAttribute**和 **SQLExecute**）時處理這些狀況。  
  
 視驅動程式和資料來源的功能而定，在準備語句時，可能會檢查參數資訊 (例如) 資料類型 (如果所有參數都已系結) 或在執行時 (所有參數都未系結) 。 為了達到最大的互通性，應用程式應該在相同的語句上準備新的 SQL 語句之前，解除所有套用至舊 SQL 語句的參數的系結。 這可防止由於舊的參數資訊套用至新的語句而造成的錯誤。  
  
> [!IMPORTANT]  
>  藉由明確呼叫 **SQLEndTran** 或在自動認可模式下工作來認可交易，可能會導致資料來源刪除連接上所有語句的存取計畫。 如需詳細資訊，請參閱 SQL_CURSOR_COMMIT_BEHAVIOR 和 SQL_CURSOR_ROLLBACK_BEHAVIOR 資訊類型 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) 以及 [交易對資料指標和備妥語句的影響](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)。  
  
## <a name="code-example"></a>程式碼範例  
 請參閱 [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)、 [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)和 [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)。  
  
## <a name="related-functions"></a>相關函數  
  
|如需下列資訊|請參閱|  
|---------------------------|---------|  
|配置語句控制碼|[SQLAllocHandle 函式](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|將緩衝區系結至結果集內的資料行|[SQLBindCol 函數](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|將緩衝區系結至參數|[SQLBindParameter 函式](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|取消語句處理|[SQLCancel 函式](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|執行認可或復原操作|[SQLEndTran 函數](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|執行 SQL 語句|[SQLExecDirect 函式](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|執行已備妥的 SQL 語句|[SQLExecute 函式](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|傳回受語句影響的資料列數目|[SQLRowCount 函數](../../../odbc/reference/syntax/sqlrowcount-function.md)|  
|設定資料指標名稱|[SQLSetCursorName 函式](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>另請參閱  
 [ODBC API 參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
