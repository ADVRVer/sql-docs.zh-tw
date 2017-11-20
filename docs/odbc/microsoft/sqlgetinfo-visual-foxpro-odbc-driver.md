---
title: "SQLGetInfo （Visual FoxPro ODBC 驅動程式） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: fbc39e3d-67d9-4331-bf5f-76dbd74c4c45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2aa64242f7ae74d7bf815d197e67b91c460e4a54
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetinfo-visual-foxpro-odbc-driver"></a>SQLGetInfo （Visual FoxPro ODBC 驅動程式）
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援： 完整  
  
 ODBC 應用程式開發介面相容性： 層級 1  
  
 傳回 Visual FoxPro ODBC 驅動程式和連接控制代碼相關聯的資料來源的一般資訊*hdbc*。 下列清單顯示每個 Visual FoxPro ODBC 驅動程式所傳回的值*fInfoType*引數和傳回的值相關的註解。  
  
 如需詳細資訊，請參閱[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)中*ODBC 程式設計人員參考*。  
  
## <a name="a"></a>只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，  
 傳回 SQL_ACCESSIBLE_PROCEDURES ' N '。  
  
 SQL_ACCESSIBLE_TABLES 傳回 'Y'。  
  
 SQL_ACTIVE_CONNECTIONS 傳回 0。  
  
 SQL_ACTIVE_STATEMENTS 傳回 0。  
  
 SQL_ALTER_TABLE 傳回 SQL_AT_ADD_COLUMN 或 SQL_AT_DROP_COLUMN。  
  
## <a name="b"></a>B  
 SQL_BOOKMARK_PERSISTENCE 傳回 SQL_BP_SCROLL。  
  
## <a name="c"></a>C  
 SQL_COLUMN_ALIAS 傳回 'Y'。  
  
 SQL_CONCAT_NULL_BEHAVIOR 傳回連接。  
  
 SQL_CONVERT_BIGINT 傳回 0。 Visual FoxPro ODBC 驅動程式不支援*BigInt*。  
  
 SQL_CONVERT_BINARY 傳回 0。  
  
 SQL_CONVERT_BIT 傳回 0。  
  
 SQL_CONVERT_CHAR 傳回 0。  
  
 SQL_CONVERT_DATE 傳回 0。  
  
 SQL_CONVERT_DECIMAL 傳回 0。  
  
 SQL_CONVERT_DOUBLE 傳回 0。  
  
 SQL_CONVERT_FLOAT 傳回 0。  
  
 SQL_CONVERT_INTEGER 傳回 0。  
  
 SQL_CONVERT_LONGVARBINARY 傳回 0。  
  
 SQL_CONVERT_LONGVARCHAR 傳回 0。  
  
 SQL_CONVERT_NUMERIC 傳回 0。  
  
 SQL_CONVERT_REAL 傳回 0。  
  
 SQL_CONVERT_SMALLINT 傳回 0。  
  
 SQL_CONVERT_TIME 傳回 0。  
  
 SQL_CONVERT_TIMESTAMP 傳回 0。  
  
 SQL_CONVERT_TINYINT 傳回 0。  
  
 SQL_CONVERT_VARBINARY 傳回 0。  
  
 SQL_CONVERT_VARCHAR 傳回 0。  
  
 SQL_CONVERT_FUNCTIONS 傳回 0。  
  
 SQL_CORRELATION_NAME 傳回 SQL_CN_ANY。  
  
 SQL_CURSOR_COMMIT_BEHAVIOR 傳回 SQL_CB_PRESERVE。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR 傳回 SQL_CB_PRESERVE。  
  
## <a name="d"></a>D  
 SQL_DATA_SOURCE_NAME 傳回值為 DSN 來傳遞[SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)，或[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md); 如果不指定任何資料來源名稱，則會傳回空字串。  
  
 傳回 SQL_DATA_SOURCE_READ_ONLY ' N '。  
  
 SQL_DATABASE_NAME 到目前的資料庫傳回完整的 UNC 路徑的資料來源是[資料庫](../../odbc/microsoft/visual-foxpro-terminology.md)。 如果資料來源連接的目錄[資料表](../../odbc/microsoft/visual-foxpro-terminology.md)，函數會傳回路徑的目錄。  
  
 SQL_DBMS_NAME 傳回 「 Visual FoxPro"。  
  
 SQL_DBMS_VER 傳回"03.00.0000"。  
  
 SQL_DEFAULT_TXN_ISOLATION 傳回 SQL_TXN_READ_COMMITTED。 中途讀取不可行，但不可重複讀取和虛設項目。  
  
 SQL_DRIVER_HDBC 被實作由驅動程式管理員。  
  
 SQL_DRIVER_HENV 被實作由驅動程式管理員。  
  
 SQL_DRIVER_HLIB 被實作由驅動程式管理員。  
  
 SQL_DRIVER_HSTMT 被實作由驅動程式管理員。  
  
 SQL_DRIVER_NAME 傳回"vfpodbc.dll"。  
  
 SQL_DRIVER_ODBC_VER 傳回"02.50 」 （SQL_SPEC_MAJOR、 SQL_SPEC_MINOR）。  
  
 SQL_DRIVER_VER 傳回"01.00.0000"。  
  
## <a name="e"></a>E  
 傳回 SQL_EXPRESSIONS_IN_ORDERBY ' N '。  
  
## <a name="f"></a>F  
 SQL_FETCH_DIRECTION 傳回：  
  
-   SQL_FD_FETCH_NEXT  
  
-   SQL_FD_FETCH_FIRST  
  
-   SQL_FD_FETCH_LAST  
  
-   SQL_FD_FETCH_PRIOR  
  
-   SQL_FD_FETCH_ABSOLUTE  
  
-   SQL_FD_FETCH_RELATIVE  
  
-   SQL_FD_FETCH_BOOKMARK。  
  
 SQL_FILE_USAGE 傳回 SQL_FILE_QUALIFIER 這兩個資料庫 （.dbc 檔案），並免費資料表 （.dbf 檔案） 的資料來源。  
  
## <a name="g-h"></a>G-H  
 SQL_GETDATA_EXENSIONS 傳回：  
  
-   SQL_GD_ANY_COLUMN  
  
-   SQL_GD_ANY_BLOCK  
  
-   SQL_GD_ANY_BOUND  
  
-   SQL_GD_ANY_ORDER  
  
 SQL_GROUP_BY 傳回 SQL_GB_NO_RELATION。  
  
## <a name="i-j"></a>我-J  
 SQL_IDENTIFIER_CASE 傳回 SQL_IC_MIXED。  
  
 傳回 SQL_IDENTIFIER_QUOTE_CHAR '。  
  
## <a name="k"></a>K  
 SQL_KEYWORDS 傳回""。  
  
## <a name="l"></a>L  
 傳回 SQL_LIKE_ESCAPE_CLAUSE ' N '。  
  
 SQL_LOCK_TYPES 傳回 SQL_LCK_NO_CHANGE。  
  
## <a name="m"></a>M  
 SQL_MAX_BINARY_LITERAL_LEN 傳回 0。  
  
 SQL_MAX_CHAR_LITERAL_LEN 傳回 254。  
  
 SQL_MAX_COLUMN_NAME_LEN 傳回 128。  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY 傳回 16。  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY 傳回 16。  
  
 SQL_MAX_COLUMNS_IN_INDEX 傳回 0。  
  
 SQL_MAX_COLUMNS_IN_SELECT 傳回 254。  
  
 SQL_MAX_COLUMNS_IN_TABLE 傳回 254。  
  
 SQL_MAX_CURSOR_NAME_LEN 傳回 254。  
  
 SQL_MAX_INDEX_SIZE 傳回 0。  
  
 SQL_MAX_OWNER_NAME_LEN 傳回 0。  
  
 SQL_MAX_PROCEDURE_NAME_LEN 傳回 0。 Visual FoxPro ODBC 驅動程式不允許直接存取 Visual FoxPro 預存程序。  
  
 SQL_MAX_QUALIFIER_NAME_LEN 傳回最高的作業系統路徑長度。  
  
 SQL_MAX_ROW_SIZE 傳回 254 ^2。  
  
 傳回 SQL_MAX_ROW_SIZE_INCLUDES_LONG ' N '。  
  
 SQL_MAX_STATEMENT_LEN 傳回 8192。  
  
 SQL_MAX_TABLE_NAME_LEN 傳回 128。  
  
 SQL_MAX_TABLES_IN_SELECT 傳回 16。  
  
 SQL_MAX_USER_NAME_LEN 傳回 0。  
  
 SQL_MULT_RESULT_SETS 傳回 'Y'。  
  
 SQL_MULTIPLE_ACTIVE_TXN 傳回 'Y'。 多個連接可以有數個同時開啟的交易。  
  
## <a name="n"></a>N  
 傳回 SQL_NEED_LONG_DATA_LEN ' N '。  
  
 SQL_NON_NULLABLE_COLUMNS 傳回 SQL_NNC_NON_NULL。  
  
 SQL_NULL_COLLATION 傳回 SQL_NC_LOW。  
  
 SQL_NUMERIC_FUNCTIONS 傳回除了 SQL_FN_NUM_POWER，Visual FoxPro ODBC 驅動程式不支援的所有函式。 支援下列功能：  
  
-   SQL_FN_NUM_ABS  
  
-   SQL_FN_NUM_ACOS  
  
-   SQL_FN_NUM_ASIN  
  
-   SQL_FN_NUM_ATAN  
  
-   SQL_FN_NUM_ATAN2  
  
-   SQL_FN_NUM_CELING  
  
-   SQL_FN_NUM_COS  
  
-   SQL_FN_NUM_COT  
  
-   SQL_FN_NUM_DEGREES  
  
-   SQL_FN_NUM_EXP  
  
-   SQL_FN_NUM_FLOOR  
  
-   SQL_FN_NUM_LOG  
  
-   SQL_FN_NUM_LOG10  
  
-   SQL_FN_NUM_MOD  
  
-   SQL_FN_NUM_PI  
  
-   SQL_FN_NUM_RADIANS  
  
-   SQL_FN_NUM_RAND  
  
-   SQL_FN_NUM_ROUND  
  
-   SQL_FN_NUM_SIGN  
  
-   SQL_FN_NUM_SIN  
  
-   SQL_FN_NUM_SQRT  
  
-   SQL_FN_NUM_TAN  
  
## <a name="o"></a>O  
 SQL_ODBC_API_CONFORMANCE 傳回 SQL_OAC_LEVEL1。  
  
 SQL_ODBC_SAG_CLI_CONFORMANCE 傳回 SQL_OSCC_COMPLIANT。  
  
 SQL_ODBC_SQL_CONFORMANCE 傳回 SQL_OSC_MINIMUM。 支援最小 SQL 語法。  
  
 SQL_ODBC_SQL_OPT_IEF 傳回"N"。  
  
 SQL_ODBC_VER 被實作由驅動程式管理員。  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT 傳回"N"。  
  
 SQL_OUTER_JOINS 傳回"N"。  
  
 SQL_OWNER_TERM 傳回""。 Visual FoxPro ODBC 驅動程式不支援針對它的物件擁有者。  
  
 SQL_OWNER_USAGE 傳回 0。 Visual FoxPro ODBC 驅動程式不支援針對它的物件擁有者。  
  
## <a name="p"></a>P  
 SQL_POS_OPERATIONS 傳回 SQL_POS_POSITION。  
  
 SQL_POSITIONED_STATEMENTS 傳回 0。  
  
 SQL_PROCEDURE_TERM 傳回""。  
  
 傳回 SQL_PROCEDURES ' N '。  
  
## <a name="q"></a>Q  
 SQL_QUALIFIER_LOCATION 傳回 SQL_QL_START。  
  
 傳回 SQL_QUALIFIER_NAME_SEPARATOR '！' 或 '\\'。 資料庫和資料表之間的分隔符號是 '！' 連接到資料來源的[資料庫](../../odbc/microsoft/visual-foxpro-terminology.md)，和 '\\' 的資料來源的目錄，[釋放資料表](../../odbc/microsoft/visual-foxpro-terminology.md)。  
  
 SQL_QUALIFIER_TERM 傳回 「 資料庫 」 或 「 目錄 」。 限定詞是 「 資料庫 」 的資料來源連接到[資料庫](../../odbc/microsoft/visual-foxpro-terminology.md)，和 「 目錄 」 的資料來源的目錄，[釋放資料表](../../odbc/microsoft/visual-foxpro-terminology.md)。  
  
 SQL_QUALIFIER_USAGE 不支援 SQL_QU_PRIVILEGE_DEFINITION;它會傳回 SQL_QU_DML_STATEMENT 或 SQL_QU_TABLE_DEFINITION。  
  
 SQL_QUOTED_IDENTIFIER_CASE 傳回 SQL_IC_MIXED。  
  
## <a name="r"></a>R  
 SQL_ROW_UPDATES 傳回"N"。 Visual FoxPro ODBC 驅動程式支援只有靜態和向前資料指標。  
  
## <a name="s"></a>S  
 SQL_SCROLL_CONCURRENCY 傳回 SQL_SCCO_READ_ONLY。  
  
 SQL_SCROLL_OPTIONS 傳回 SQL_SO_STATIC 或 SQL_SO_READONLY。  
  
 傳回 SQL_SEARCH_PATTERN_ESCAPE"\\"。  
  
 傳回 <""。  
  
 傳回 SQL_SPECIAL_CHARACTERS"~ @# $%^"。  
  
 SQL_STATIC_SENSITIVITY 傳回 0。 Visual FoxPro ODBC 驅動程式不支援位置的更新。  
  
 SQL_FN_STR_INSERT、 SQL_FN_STR_LOCATE、 SQL_FN_STR_LOCATE_2 或 SQL_FN_STR_SOUNDEX SQL_STRING_FUNCTIONS 不支援。  
  
 它會傳回：  
  
-   SQL_FN_STR_ASCII  
  
-   SQL_FN_STR_CHAR  
  
-   SQL_FN_STR_CONCAT  
  
-   SQL_FN_STR_DIFFERENCE  
  
-   SQL_FN_STR_LCASE  
  
-   SQL_FN_STR_LEFT  
  
-   SQL_FN_STR_LENGTH  
  
-   SQL_FN_STR_LTRIM  
  
-   SQL_FN_STR_REPEAT  
  
-   SQL_FN_STR_REPLACE  
  
-   SQL_FN_STR_RIGHT  
  
-   SQL_FN_STR_RTRIM  
  
-   SQL_FN_STR_SUBSTRING  
  
-   SQL_FN_STR_UCASE  
  
-   SQL_FN_STR_SPACE。  
  
 SQL_SUBQUERIES 傳回：  
  
-   SQL_SQ_CORRELATED_SUBQUERIES  
  
-   SQL_SQ_COMPARISON  
  
-   SQL_SQ_EXISTS  
  
-   SQL_SQ_IN  
  
-   SQL_SQ_QUANTIFIED。  
  
 SQL_SYSTEM_FUNCTIONS 傳回：  
  
-   SQL_FN_SYS_DBNAME  
  
-   SQL_FN_SYS_IFNULL  
  
 但不是：  
  
-   SQL_FN_SYS_USERNAME  
  
## <a name="t"></a>T  
 SQL_TABLE_TERM 傳回"table"。  
  
 SQL_TIMEDATE_ADD_INTERVALS 傳回：  
  
-   SQL_FN_TSI_ 第二個  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 但不是：  
  
-   SQL_FN_TSI_FRAC_SECOND  
  
-   SQL_FN_TSI_WEEK  
  
-   SQL_FN_TSI_QUARTER  
  
 SQL_TIMEDATE_DIFF_INTERVALS 傳回：  
  
-   SQL_FN_TSI_ 第二個  
  
-   SQL_FN_TSI_MINUTE  
  
-   SQL_FN_TSI_HOUR  
  
-   SQL_FN_TSI_DAY  
  
-   SQL_FN_TSI_MONTH  
  
-   SQL_FN_TSI_YEAR  
  
 SQL_FN_TD_QUARTER、 SQL_FN_TD_TIMESTAMPADD、 SQL_FN_TD_DAYOFYEAR 或 SQL_FN_TD_WEEK SQL_TIMEDATE_FUNCTIONS 不支援。  
  
 它會傳回：  
  
-   SQL_FN_TD_CURDATE  
  
-   SQL_FN_TD_CURTIME  
  
-   SQL_FN_TD_DAYNAME  
  
-   SQL_FN_TD_DAYOFMONTH  
  
-   SQL_FN_TD_DAYOFWEEK  
  
-   SQL_FN_TD_HOUR  
  
-   SQL_FN_TD_MINUTE  
  
-   SQL_FN_TD_MONTH  
  
-   SQL_FN_TD_MONTHNAME  
  
-   SQL_FN_TD_NOW  
  
-   SQL_FN_TD_SECOND  
  
-   SQL_FN_TD_TIMESTAMPDIFF  
  
-   SQL_FN_TD_YEAR。  
  
 SQL_TXN_CAPABLE 傳回 SQL_TC_DML。  
  
 SQL_TXN_ISOLATION_OPTION 傳回 SQL_TXN_READ_COMMITTED。  
  
## <a name="u-z"></a>U-Z  
 SQL_UNION 傳回 SQL_U_UNION 或 SQL_U_UNION_ALL。  
  
 傳回 SQL_USER_NAME\<空白 >。

