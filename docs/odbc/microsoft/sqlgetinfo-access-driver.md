---
title: SQLGetInfo (Access Driver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Access Driver
- Access driver [ODBC], SQLGetInfo
ms.assetid: c226aba7-a2f4-4b32-b640-92654b40e5a7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 626ee1de57fdcecdf53d20263b1717df25480c40
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313426"
---
# <a name="sqlgetinfo-access-driver"></a>SQLGetInfo (Access 驅動程式)
> [!NOTE]  
>  本主題提供存取驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 **SQLGetInfo**支援 SQL_FILE_USAGE 資訊類型。 傳回的值是 16 位元整數，指出如何驅動程式直接處理資料來源中的檔案：  
  
-   SQL_FILE_NOT_SUPPORTED-驅動程式不是單層式架構的驅動程式。  
  
-   SQL_FILE_TABLE-單層式架構的驅動程式將資料來源中的檔案視為資料表。  
  
-   SQL_FILE_QUALIFIER-單層式架構的驅動程式將資料來源中的檔案視為限定詞。  
  
 ODBC 驅動程式會傳回 SQL_FILE_QUALIFIER，因為每個檔案是完整的資料庫。  
  
## <a name="sqlbookmarkpersistence"></a>SQL_BOOKMARK_PERSISTENCE  
 SQL_BP_SCROLL &#124;  SQL_BP_UPDATE[1]  
  
 [1] 的書籤在認可後持續，而不是會保存在復原之後。  
  
## <a name="sqlconvertbinary"></a>SQL_CONVERT_BINARY  
 SQL_CVT_DOUBLE &#124;  SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertchar"></a>SQL_CONVERT_CHAR  
 SQL_CVT_DOUBLE &#124;  SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertdate"></a>SQL_CONVERT_DATE  
 SQL_CVT_DOUBLE &#124;  SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertdouble"></a>SQL_CONVERT_DOUBLE  
 SQL_CVT_DOUBLE &#124;  SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertfloat"></a>SQL_CONVERT_FLOAT  
 SQL_CVT_DOUBLE &#124;  SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertinteger"></a>SQL_CONVERT_INTEGER  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertlongvarbinary"></a>SQL_CONVERT_LONGVARBINARY  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertlongvarchar"></a>SQL_CONVERT_LONGVARCHAR  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertnumeric"></a>SQL_CONVERT_NUMERIC  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertreal"></a>SQL_CONVERT_REAL  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertsmallint"></a>SQL_CONVERT_SMALLINT  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconverttime"></a>SQL_CONVERT_TIME  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconverttimestamp"></a>SQL_CONVERT_TIMESTAMP  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconverttinyint"></a>SQL_CONVERT_TINYINT  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertvarbinary"></a>SQL_CONVERT_VARBINARY  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlconvertvarchar"></a>SQL_CONVERT_VARCHAR  
 SQL_CVT_DOUBLE &#124; SQL_CVT_FLOAT &#124;  SQL_CVT_INTEGER &#124;  SQL_CVT_NUMERIC &#124;  SQL_CVT_REAL &#124;  SQL_CVT_SMALLINT &#124;  SQL_CVT_VARCHAR &#124; SQL_CVT_WVARCHAR  
  
## <a name="sqlunion"></a>SQL_UNION  
 SQL_U_UNION_ALL &#124; SQL_U_UNION  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|版本|版本號碼的格式|  
|----------|-------------|-------------------------------|  
|Microsoft Access|2.0|02.00.0000|  
||3.0|03.00.0000|  
||3.5|03.50.0000|  
||4.0|04.00.0000|  
  
> [!NOTE]  
>  不支援 1.0 和 1.1 版。 另外，還有在 Microsoft Access 版本 3.0、 7.0 和 97 中的資料格式沒有差異。  
  
## <a name="sqlddlindex"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sqlgetdataextensions"></a>SQL_GETDATA_EXTENSIONS  
 SQL_GD_ANY_ORDER &#124; SQL_GD_ANY_COLUMN &#124; SQL_GD_BLOCK &#124; SQL_GD_BOUND  
  
## <a name="sqlkeywords"></a>SQL_KEYWORDS  
 英數字元  
  
 自動遞增  
  
 BINARY  
  
 Boolean  
  
 BYTE  
  
 計數器  
  
 CURRENCY  
  
 DATABASE  
  
 DATABASENAME  
  
 DATETIME  
  
 不允許  
  
 DISTINCTROW  
  
 DOUBLEFLOAT  
  
 FLOAT4  
  
 FLOAT8  
  
 GENERAL  
  
 IEEEDOUBLE  
  
 IEEESINGLE  
  
 IGNORE  
  
 IMAGE  
  
 INTEGER1  
  
 INTEGER2  
  
 INTEGER4  
  
 邏輯  
  
 LOGICAL1  
  
 LONG  
  
 LONGBINARY  
  
 LONGCHAR  
  
 長文字  
  
 附註  
  
 MONEY  
  
 附註  
  
 NUMBER  
  
 OLEOBJECT  
  
 OWNERACCESS  
  
 PARAMETERS  
  
 PERCENT  
  
 PIVOT  
  
 簡短  
  
 單一  
  
 SINGLEFLOAT  
  
 STDEV  
  
 STDEVP  
  
 字串  
  
 TABLEID  
  
 TEXT  
  
 頂端  
  
 轉換  
  
 UNSIGNEDBYTE  
  
 VAR  
  
 VARBINARY  
  
 VARP  
  
 YESNO  
  
## <a name="sqlnumericfunctions"></a>SQL_NUMERIC_FUNCTIONS  
 SQL_FN_NUM_ABS &AMP;#124; SQL_FN_NUM_ATAN &AMP;#124; SQL_FN_NUM_CEILING &AMP;#124; SQL_FN_NUM_COS &AMP;#124; SQL_FN_NUM_EXP &AMP;#124; SQL_FN_NUM_FLOOR &AMP;#124; SQL_FN_NUM_LOG &AMP;#124; SQL_FN_NUM_MOD &AMP;#124; SQL_FN_NUM_POWER &AMP;#124; SQL_FN_NUM_RAND &AMP;#124; SQL_FN_NUM_SIGN &AMP;#124; SQL_FN_NUM_SIN &AMP;#124; SQL_FN_NUM_SQRT &AMP;#124; SQL_FN_NUM_TAN  
  
## <a name="sqlojcapabilities"></a>SQL_OJ_CAPABILITIES  
 SQL_OJ_LEFT SQL_OJ_RIGHT SQL_OJ_NOT_ORDERED SQL_OJ_INNER SQL_OJ_ALL_COMPARISON_OPS  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION &#124; SQL_QU_INDEX_DEFINITION &#124; SQL_QU_PROCEDURE_INVOCATION  
  
## <a name="sqlscrolloptions"></a>SQL_SCROLL_OPTIONS  
 SQL_SO_FORWARD_ONLY &#124; SQL_SO_STATIC &#124; SQL_SO_KEYSET_DRIVEN  
  
## <a name="sqlstringfunctions"></a>SQL_STRING_FUNCTIONS  
 SQL_FN_STR_ASCII &AMP;#124; SQL_FN_STR_CHAR &AMP;#124; SQL_FN_STR_CONCAT &AMP;#124; SQL_FN_STR_LCASE &AMP;#124; SQL_FN_STR_LEFT &AMP;#124; SQL_FN_STR_LENGTH &AMP;#124; SQL_FN_STR_LOCATE &AMP;#124; SQL_FN_STR_LOCATE_2 SQL_FN_STR_LTRIM &AMP;#124; SQL_FN_STR_RIGHT &AMP;#124; SQL_FN_STR_RTRIM &AMP;#124; SQL_FN_STR_SPACE &AMP;#124; SQL_FN_STR_SUBSTRING &AMP;#124; SQL_FN_STR_UCASE  
  
## <a name="sqlsubqueries"></a>SQL_SUBQUERIES  
 SQL_SQ_COMPARISON &#124; SQL_SQ_EXISTS &#124; SQL_SQ_IN &#124; SQL_SQ_QUANTIFIED &#124; SQL_SQ_CORRELATED_SUBQUERIES  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &AMP;#124; SQL_FN_TD_CURTIME &AMP;#124; SQL_FN_TD_DAYOFMONTH &AMP;#124; SQL_FN_TD_DAYOFWEEK &AMP;#124; SQL_FN_TD_DAYOFYEAR &AMP;#124; SQL_FN_TD_HOUR &AMP;#124; SQL_FN_TD_MINUTE &AMP;#124; SQL_FN_TD_MONTH &AMP;#124; SQL_FN_TD_NOW&AMP;#124; SQL_FN_TD_SECOND &AMP;#124; SQL_FN_TD_WEEK &AMP;#124; SQL_FN_TD_YEAR
