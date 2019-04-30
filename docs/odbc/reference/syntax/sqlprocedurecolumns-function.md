---
title: SQLProcedureColumns 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLProcedureColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedureColumns
helpviewer_keywords:
- SQLProcedureColumns function [ODBC]
ms.assetid: 4ca37b28-a6df-465b-8988-d422d37fc025
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b47ef4c2df8a326d993a95e056b27d331dc649f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186201"
---
# <a name="sqlprocedurecolumns-function"></a>SQLProcedureColumns 函數
**合規性**  
 導入的版本：ODBC 1.0 標準的合規性：ODBC  
  
 **摘要**  
 **SQLProcedureColumns**傳回的輸入和輸出參數，以及構成結果集針對指定的程序的資料行清單。 驅動程式會傳回在指定的陳述式上當作結果集的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
  
SQLRETURN SQLProcedureColumns(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     ProcName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>引數  
 *StatementHandle*  
 [輸入]陳述式控制代碼。  
  
 *CatalogName*  
 [輸入]程序類別目錄名稱。 如果驅動程式支援的目錄，對於某些程序，但不適用於其他人使用，例如當驅動程式會擷取資料從不同的 Dbms，空字串 ("") 表示這些程序，沒有目錄。 *CatalogName*不能包含字串的搜尋模式。  
  
 如果 SQL_ATTR_METADATA_ID 陳述式屬性設定為 SQL_TRUE， *CatalogName*會被視為識別項和其案例並不重要。 SQL_FALSE，才*CatalogName*是一般的引數; 也就是，則會視為和其案例很重要。 如需詳細資訊，請參閱 <<c0> [ 目錄函式中的引數](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)。  
  
 *NameLength1*  
 [輸入]中的字元長度 **CatalogName*。  
  
 *SchemaName*  
 [輸入]程序結構描述名稱的字串搜尋模式。 如果驅動程式支援的結構描述，對於某些程序，但不適用於其他人使用，例如當驅動程式會擷取資料從不同的 Dbms，空字串 ("") 表示這些程序，並沒有結構描述。  
  
 如果 SQL_ATTR_METADATA_ID 陳述式屬性設定為 SQL_TRUE， *SchemaName*會被視為識別項和其案例並不重要。 SQL_FALSE，才*SchemaName*模式值引數; 也就是，則會視為和其案例很重要。  
  
 *NameLength2*  
 [輸入]中的字元長度 **SchemaName*。  
  
 *ProcName*  
 [輸入]程序名稱的字串搜尋模式。  
  
 如果 SQL_ATTR_METADATA_ID 陳述式屬性設定為 SQL_TRUE， *ProcName*會被視為識別項和其案例並不重要。 SQL_FALSE，才*ProcName*模式值引數; 也就是，則會視為和其案例很重要。  
  
 *NameLength3*  
 [輸入]中的字元長度 **ProcName*。  
  
 *ColumnName*  
 [輸入]資料行名稱的字串搜尋模式。  
  
 如果 SQL_ATTR_METADATA_ID 陳述式屬性設定為 SQL_TRUE， *ColumnName*會被視為識別項和其案例並不重要。 SQL_FALSE，才*ColumnName*模式值引數; 也就是，則會視為和其案例很重要。  
  
 *NameLength4*  
 [輸入]中的字元長度 **ColumnName*。  
  
## <a name="returns"></a>傳回值  
 SQL_SUCCESS、 SQL_SUCCESS_WITH_INFO、 SQL_STILL_EXECUTING、 SQL_ERROR 或 SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLProcedureColumns**會傳回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO，相關聯的 SQLSTATE 值，可由呼叫**SQLGetDiagRec**具有*HandleType*利用 SQL_HANDLE_STMT 的並*處理*的*StatementHandle*。 下表列出通常所傳回的 SQLSTATE 值**SQLProcedureColumns** ，並說明每個內容中的此函式; 標記法 」 (DM) 」 之前，驅動程式所傳回的 Sqlstate 的描述管理員。 傳回每個 SQLSTATE 值相關聯的程式碼會是 SQL_ERROR，除非另有指示。  
  
|SQLSTATE|錯誤|描述|  
|--------------|-----------|-----------------|  
|01000|一般警告|驅動程式特有的告知性訊息。 （函式會傳回 SQL_SUCCESS_WITH_INFO）。|  
|08S01|通訊連結失敗|函式已完成處理之前，驅動程式和驅動程式已連線到資料來源之間的通訊連結失敗。|  
|24000|指標狀態無效|資料指標是開啟*StatementHandle*，並**SQLFetch**或是**SQLFetchScroll**呼叫。 如果此錯誤會傳回由驅動程式管理員**SQLFetch**或**SQLFetchScroll**尚未傳回 sql_no_data 之後，以及如果驅動程式會傳回**SQLFetch**或**SQLFetchScroll**傳回 sql_no_data 為止。<br /><br /> 資料指標是開啟*StatementHandle*，但**SQLFetch**或是**SQLFetchScroll**尚未呼叫。|  
|40001|序列化失敗|交易已回復因為與另一個交易資源鎖死。|  
|40003|未知的陳述式完成|此函式執行期間失敗的相關聯的連接，並無法判斷交易的狀態。|  
|HY000|一般錯誤|其中沒有任何特定的 SQLSTATE 和沒有實作特定的 SQLSTATE 所定義，就會發生錯誤。 所傳回的錯誤訊息**SQLError**中 *\*MessageText*緩衝區描述錯誤和其原因。|  
|HY001|記憶體配置錯誤|驅動程式無法配置記憶體，才能支援執行或完成函式。|  
|HY008|已取消作業|非同步處理已啟用*StatementHandle*。 呼叫函式，和之前執行，完成**SQLCancel**或是**SQLCancelHandle**上呼叫*StatementHandle*。 然後在上一次呼叫函式*StatementHandle*。<br /><br /> 呼叫函式，和之前已完成執行時， **SQLCancel**或是**SQLCancelHandle**上呼叫*StatementHandle*從不同的執行緒中多執行緒應用程式。|  
|HY009|使用無效的 null 指標|SQL_ATTR_METADATA_ID 陳述式屬性設定為 SQL_TRUE， *CatalogName*引數為 null 指標，以及 SQL_CATALOG_NAME*資訊類型*支援的目錄名稱，傳回。<br /><br /> (DM) SQL_ATTR_METADATA_ID 陳述式屬性設定為 SQL_TRUE，而*SchemaName*， *ProcName*，或*ColumnName*引數是 null 指標。|  
|HY010|函數順序錯誤|(DM) 以非同步方式執行的函式呼叫的連接控制代碼相關聯*StatementHandle*。 SQLProcedureColumns 函式呼叫時，仍執行此 aynschronous 函式。<br /><br /> (DM) **SQLExecute**， **SQLExecDirect**，或**SQLMoreResults**針對呼叫*StatementHandle*並傳回 SQL_PARAM_DATA_可使用。 資料已擷取所有的資料流參數前呼叫此函式。<br /><br /> 以非同步方式執行的函式 （不是此一） 已呼叫 」 (DM) *StatementHandle*和仍在呼叫此函式時所執行。<br /><br /> (DM) **SQLExecute**， **SQLExecDirect**， **SQLBulkOperations**，或**SQLSetPos**針對呼叫*StatementHandle*並傳回 SQL_NEED_DATA。 此函式呼叫之前已傳送的所有資料在執行中參數或資料行的資料。|  
|HY090|字串或緩衝區長度無效|(DM) 其中一個名稱的長度引數的值小於 0，但不是等於 SQL_NTS。<br /><br /> 其中一個名稱的長度引數的值超過最大長度值，對應的目錄、 結構描述、 程序，或資料行名稱。|  
|HY117|連接已因為未知的交易狀態暫止。 只中斷連線，並允許唯讀的函式。|(DM) 如需暫停狀態的詳細資訊，請參閱[SQLEndTran 函式](../../../odbc/reference/syntax/sqlendtran-function.md)。|  
|HYC00|未實作選擇性功能|指定程序類別目錄，並在驅動程式或資料來源不支援目錄。<br /><br /> 指定程序結構描述，且驅動程式或資料來源不支援結構描述。<br /><br /> 程序結構描述、 程序名稱或資料行名稱，為指定的字串搜尋模式和資料來源不支援搜尋模式的一個或多個這些引數。<br /><br /> 驅動程式或資料來源不支援陳述式屬性 SQL_ATTR_CONCURRENCY 和 SQL_ATTR_CURSOR_TYPE 的目前設定的組合。<br /><br /> SQL_ATTR_USE_BOOKMARKS 陳述式屬性設定為 SQL_UB_VARIABLE，且 SQL_ATTR_CURSOR_TYPE 陳述式屬性已設定為驅動程式不支援書籤的資料指標類型。|  
|HYT00|已超過逾時的設定|在逾時期限到期之前的資料來源傳回結果集。 透過設定的逾時期限**SQLSetStmtAttr**，sql_attr_query_timeout 時。|  
|HYT01|連接逾時過期|連接逾時期限到期之前的資料來源回應要求。 透過設定連接逾時期限**SQLSetConnectAttr**，SQL_ATTR_CONNECTION_TIMEOUT。|  
|IM001|驅動程式不支援此函式|(DM) 驅動程式相關聯*StatementHandle*不支援此函式。|  
|IM017|輪詢已停用非同步通知模式|每次使用通知模型時，會停用輪詢。|  
|IM018|**SQLCompleteAsync**尚未完成先前的非同步作業，此控制代碼上呼叫。|如果控制代碼上先前的函式呼叫傳回 SQL_STILL_EXECUTING 和通知模式已啟用，如果**SQLCompleteAsync**必須在執行後置處理，並完成作業的控制代碼上呼叫。|  
  
## <a name="comments"></a>註解  
 此函式通常用於陳述式執行之前擷取程序參數和資料行，如果有的話，構成的程序所傳回的結果集的相關資訊。 如需詳細資訊，請參閱 <<c0> [ 程序](../../../odbc/reference/develop-app/procedures-odbc.md)。  
  
> [!NOTE]  
>  **SQLProcedureColumns**可能不會傳回所有程序所使用的資料行。 例如，驅動程式可能會傳回唯一的程序，並不會產生結果集資料行所使用的參數資訊。  
  
 *SchemaName*， *ProcName*，並*ColumnName*引數接受搜尋模式。 如需有關有效的搜尋模式的詳細資訊，請參閱[模式值引數](../../../odbc/reference/develop-app/pattern-value-arguments.md)。  
  
> [!NOTE]  
>  如需一般用途、 引數和 ODBC 目錄函數的傳回的資料的詳細資訊，請參閱[目錄函數](../../../odbc/reference/develop-app/catalog-functions.md)。  
  
 **SQLProcedureColumns**標準的結果集，依 PROCEDURE_CAT、 PROCEDURE_SCHEM、 程序名稱和 COLUMN_TYPE 排序的方式傳回結果。 針對每個程序，以下列順序傳回資料行名稱： 傳回值的名稱 （依呼叫順序） 的程序引動過程中每個參數的名稱，然後 （依資料行順序） 程序傳回結果集中的每個資料行的名稱。  
  
 應用程式應繫結的驅動程式特有的資料行，相對於結果集的結尾。 如需詳細資訊，請參閱 <<c0> [ 目錄函式所傳回的資料](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)。  
  
 若要判斷 PROCEDURE_CAT、 PROCEDURE_SCHEM、 程序名稱和 COLUMN_NAME 資料行的實際長度，應用程式可以呼叫**SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN，SQL_MAX_SCHEMA_NAME_LEN，SQL_MAX_ 與PROCEDURE_NAME_LEN 和 SQL_MAX_COLUMN_NAME_LEN 選項。  
  
 下列資料行已重新命名，針對 ODBC 3。*x*。 因為應用程式繫結的資料行編號的資料行名稱變更不會影響回溯相容性。  
  
|ODBC 2.0 資料行|ODBC 3。*x*資料行|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|程序 _OWNER|PROCEDURE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 已新增下列資料行所傳回的結果集**SQLProcedureColumns** ODBC 3。*x*:  
  
-   COLUMN_DEF  
  
-   DATETIME_CODE  
  
-   CHAR_OCTET_LENGTH  
  
-   ORDINAL_POSITION  
  
-   IS_NULLABLE  
  
 下表列出結果集內的資料行。 驅動程式，可以定義資料行 19 (IS_NULLABLE) 以外的其他資料行。 應用程式應該取得存取權的驅動程式特有的資料行，倒數，從結果集的結尾，而不是指定明確的序數位置。 如需詳細資訊，請參閱 <<c0> [ 目錄函式所傳回的資料](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)。  
  
|資料行名稱|資料行編號|資料類型|註解|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|程序類別目錄名稱;如果不適用於資料來源，則為 NULL。 如果驅動程式支援目錄對於某些程序，但不適用於其他項目，例如當驅動程式會擷取不同 Dbms 中的資料，它會傳回空字串 ("") 沒有目錄這些程序。|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|程序結構描述名稱;如果不適用於資料來源，則為 NULL。 如果驅動程式支援結構描述對於某些程序，但不適用於其他項目，例如當驅動程式會擷取不同 Dbms 中的資料，它會傳回空字串 ("") 並沒有結構描述的程序。|  
|程序名稱 (ODBC 2.0)|3|非 NULL Varchar|程序名稱。 沒有名稱的程序會傳回空的字串。|  
|COLUMN_NAME (ODBC 2.0)|4|非 NULL Varchar|程序的資料行名稱。 驅動程式會傳回沒有名稱的程序資料行的空字串。|  
|COLUMN_TYPE (ODBC 2.0)|5|Smallint 非 NULL|會定義程序資料行，做為參數或結果集資料行：<br /><br /> SQL_PARAM_TYPE_UNKNOWN:程序的資料行是其類型是未知的參數。 ODBC (1.0)<br /><br /> SQL_PARAM_INPUT:程序的資料行是輸入的參數。 ODBC (1.0)<br /><br /> SQL_PARAM_INPUT_OUTPUT:程序的資料行是輸入/輸出參數。 ODBC (1.0)<br /><br /> SQL_PARAM_OUTPUT:程序的資料行是一個 output 參數。 ODBC (2.0)<br /><br /> SQL_RETURN_VALUE:程序的資料行是此程序的傳回值。 ODBC (2.0)<br /><br /> SQL_RESULT_COL:程序的資料行是結果集資料行。 ODBC (1.0)|  
|DATA_TYPE (ODBC 2.0)|6|Smallint 非 NULL|SQL 資料類型。 這可以是 ODBC SQL 資料類型或驅動程式專屬的 SQL 資料型別。 日期時間和間隔資料類型，此資料行都會傳回精確的資料類型 （例如 SQL_TYPE_TIME 或 SQL_INTERVAL_YEAR_TO_MONTH）。 如需有效的 ODBC SQL 資料類型的清單，請參閱 < [SQL 資料類型](../../../odbc/reference/appendixes/sql-data-types.md)附錄 d:資料類型。 如需驅動程式專用的 SQL 資料類型資訊，請參閱驅動程式的文件。|  
|TYPE_NAME (ODBC 2.0)|7|非 NULL Varchar|資料來源相關的資料型別名稱;比方說，"CHAR"、"VARCHAR"、"MONEY"、"長 VARBINARY"或者"CHAR （） FOR BIT DATA"。|  
|COLUMN_SIZE (ODBC 2.0)|8|Integer|程序上的資料行的資料來源的資料行大小。 會傳回 NULL 的資料類型資料行大小不適用。 如需有關有效位數，請參閱[資料行大小、 小數位數、 傳輸八位元長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)附錄 d:資料類型。|  
|BUFFER_LENGTH (ODBC 2.0)|9|Integer|資料傳輸的位元組長度**SQLGetData**或**SQLFetch**如果 SQL_C_DEFAULT 指定的作業。 針對數值資料，這個大小可能會不同的資料來源上儲存的資料大小。 如需詳細資訊，請參閱 <<c0> [ 資料行大小、 小數位數、 傳輸八位元長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)，附錄 d:資料類型。|  
|DECIMAL_DIGITS (ODBC 2.0)|10|Smallint|資料來源上的程序資料行的小數位數。 會傳回 NULL 的資料類型小數位數不適用。 關於十進位數字的詳細資訊，請參閱[資料行大小、 小數位數、 傳輸八位元長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)，附錄 d:資料類型。|  
|NUM_PREC_RADIX (ODBC 2.0)|11|Smallint|針對數值資料類型，10 或 2。<br /><br /> 如果是 10，COLUMN_SIZE 與 DECIMAL_DIGITS 中的值會提供所允許的資料行的小數位數。 比方說，DECIMAL(12,5) 資料行就會傳回為 10，COLUMN_SIZE 為 12，並為 5; DECIMAL_DIGITS NUM_PREC_RADIX浮點數資料行可能會傳回 NUM_PREC_RADIX 是 10，15，個 COLUMN_SIZE DECIMAL_DIGITS 的 null 值。<br /><br /> 若為 2，COLUMN_SIZE 與 DECIMAL_DIGITS 中的值會提供資料行中允許的位元數。 比方說，浮點數資料行可能會傳回 NUM_PREC_RADIX 為 2 的 53，COLUMN_SIZE 和 DECIMAL_DIGITS 的 null 值。<br /><br /> 會傳回 NULL 的資料型別 NUM_PREC_RADIX 不適用。|  
|可為 NULL (ODBC 2.0)|12|Smallint 非 NULL|是否程序的資料行接受 NULL 值：<br /><br /> SQL_NO_NULLS:程序的資料行不接受 NULL 值。<br /><br /> SQL_NULLABLE:程序的資料行接受 NULL 值。<br /><br /> SQL_NULLABLE_UNKNOWN:不知道如果程序的資料行接受 NULL 值。|  
|註解 (ODBC 2.0)|13|Varchar|程序的資料行的描述。|  
|COLUMN_DEF (ODBC 3.0)|14|Varchar|資料行的預設值。<br /><br /> NULL 指定為預設值，這個資料行為 NULL 一字，不包含在引號中。 無法表示的預設值，而不會截斷，則此資料行就會包含已截斷，沒有封入的單引號。 如果已指定沒有預設值，這個資料行就會是 NULL。<br /><br /> 包含已截斷的值時，產生新的資料行定義中，除了可用 COLUMN_DEF 的值。|  
|SQL_DATA_TYPE (ODBC 3.0)|15|Smallint 非 NULL|SQL 資料類型，因為它的值會出現在描述子 SQL_DESC_TYPE 欄位。 這個資料行是與 DATA_TYPE 資料行，除了 datetime 和間隔資料類型相同。<br /><br /> 日期時間和間隔資料類型，結果集中的 SQL_DATA_TYPE 欄位會傳回 SQL_INTERVAL 或如果是 SQL_DATETIME，而且 SQL_DATETIME_SUB 欄位將會傳回特定的間隔或 datetime 資料類型的子代碼。 (請參閱[附錄 d:資料型別](../../../odbc/reference/appendixes/appendix-d-data-types.md)。)|  
|SQL_DATETIME_SUB (ODBC 3.0)|16|Smallint|日期時間和間隔資料類型的子型別程式碼。 其他資料類型的這個資料行都會傳回 NULL。|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|17|Integer|以位元組為單位的最大長度的字元或二進位資料類型資料行。 所有其他資料類型的這個資料行都會傳回 NULL。|  
|ORDINAL_POSITION (ODBC 3.0)|18|整數不是 NULL|對於輸入和輸出參數，參數的程序中的定義 （增加參數順序，從 1 開始） 中的序數位置。 傳回值 （如果有的話），就會傳回 0。 結果集資料行，結果中的資料行的序數位置設定，第一個資料行，結果集中要與數字 1。 如果有多個結果集，驅動程式專屬的方式傳回資料行的序數位置。|  
|IS_NULLABLE (ODBC 3.0)|19|Varchar|[否] 如果資料行不包含 Null。<br /><br /> 「 是 」 如果資料行可以包括 NULLs。<br /><br /> 如果 Null 屬性不明，這個資料行會傳回長度為零的字串。<br /><br /> 遵照 ISO 規則來決定 Null 屬性。 ISO SQL 標準 DBMS 無法傳回空字串。<br /><br /> 這個資料行的傳回值不同於 NULLABLE 資料行的傳回值。 （請參閱可為 NULL 的資料行的描述。）|  
  
## <a name="code-example"></a>程式碼範例  
 請參閱[程序呼叫](../../../odbc/reference/develop-app/procedure-calls.md)。  
  
## <a name="related-functions"></a>相關函數  
  
|如需詳細資訊|請參閱|  
|---------------------------|---------|  
|繫結至結果集的資料行的緩衝區|[SQLBindCol 函式](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|取消陳述式處理|[SQLCancel 函式](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|擷取單一資料列或順向方向中的資料區塊|[SQLFetch 函式](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|提取資料的區塊，或捲動結果集|[SQLFetchScroll 函式](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|傳回資料來源中的程序的清單|[SQLProcedures 函式](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
  
## <a name="see-also"></a>另請參閱  
 [ODBC API 參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
