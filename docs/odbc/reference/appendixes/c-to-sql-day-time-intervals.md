---
title: C 到 SQL： 日期時間間隔 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb41d658637258c6d60b5adb4e0d7abb9ae81d91
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47757656"
---
# <a name="c-to-sql-day-time-intervals"></a>C 到 SQL：日期時間間隔
日期時間間隔的 ODBC C 資料類型的識別項是：  
  
 SQL_C_INTERVAL_DAY  
  
 SQL_C_INTERVAL_HOUR  
  
 SQL_C_INTERVAL_MINUTE  
  
 SQL_C_INTERVAL_SECOND  
  
 SQL_C_INTERVAL_DAY_TO_HOUR  
  
 SQL_C_INTERVAL_DAY_TO_MINUTE  
  
 SQL_C_INTERVAL_DAY_TO_SECOND  
  
 SQL_C_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_C_INTERVAL_HOUR_TO_SECOND  
  
 SQL_C_INTERVAL_MINUTE_TO_SECOND  
  
 下表顯示 ODBC SQL 間隔 C 資料可能會轉換成的資料類型。 如需資料行和資料表中的詞彙說明，請參閱 <<c0> [ 轉換將資料從 C 到 SQL 資料類型](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)。  
  
|SQL 型別識別項|測試|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> [A] SQL_VARCHAR<br /><br /> [A] SQL_LONGVARCHAR|資料行的位元組長度 > = 字元位元組長度<br /><br /> 資料行的位元組長度 < 字元位元組長度 [a]<br /><br /> 資料值不是常值的有效間隔|n/a<br /><br /> 22001<br /><br /> 22015|  
|[A] SQL_WCHAR<br /><br /> SQL_WVARCHAR [a]<br /><br /> [A] SQL_WLONGVARCHAR|資料行的字元長度 > = 字元長度的資料<br /><br /> 資料行的字元長度 < 字元長度的資料，[a]<br /><br /> 資料值不是常值的有效間隔|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b] SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b] SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|將單一欄位間隔轉換不會造成整個的位數截斷<br /><br /> 轉換導致截斷的整數|n/a<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|已轉換資料值，而不會截斷的任何欄位<br /><br /> 資料值的一個或多個欄位已在轉換期間截斷|n/a<br /><br /> 22015|  
  
 [a] 的所有 C 間隔資料類型可以轉換成字元資料類型。  
  
 [C 類型的間隔 b] 如果間隔是 （SQL_DAY、 SQL_HOUR、 SQL_MINUTE，還是 SQL_SECOND） 的單一欄位間隔結構中的 [類型] 欄位，可以轉換成任何的確切數值 (SQL_TINYINT，SQL_SMALLINT，SQL_INTEGER，SQL_BIGINTSQL_DECIMAL 或 SQL_NUMERIC)。  
  
 預設間隔 C 類型轉換為對應的日期時間間隔的 SQL 類型。  
  
 驅動程式將資料從間隔 C 資料類型轉換時，會忽略長度/指標值，並假設資料緩衝區的大小是間隔 C 資料類型的大小。 傳入的長度/指標值無效*Strlen_or_ind&lt*中的引數**SQLPutData**並使用指定的緩衝區中*StrLen_or_IndPtr*引數中**SQLBindParameter**。 使用指定的資料緩衝區*DataPtr*中的引數**SQLPutData**並*ParameterValuePtr*中的引數**SQLBindParameter**.  
  
 下列範例示範如何將傳送至資料庫資料行 SQL_INTERVAL_STRUCT 結構中儲存資料的間隔 C。 間隔結構包含 DAY_TO_SECOND 間隔時間。它會儲存在類型 SQL_INTERVAL_DAY_TO_MINUTE 的資料庫資料行。  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER cbValue;  
  
// Initialize the interval struct to contain the DAY_TO_SECOND  
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"  
is.intval.day_second.day      = 154;  
is.intval.day_second.hour     = 22;  
is.intval.day_second.minute   = 44;  
is.intval.day_second.second   = 10;  
is.interval_sign              = SQL_FALSE;  
  
// Bind the dynamic parameter  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,  
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &is,  
                  sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Execute an insert statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);  
```
