---
title: SQL 到 c： 字元 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], character
- character data type [ODBC]
- data conversions from SQL to C types [ODBC], character
ms.assetid: 7fdb7f38-b64d-48f2-bcb4-1ca96b2bbdb6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0d6ce8e1f961851f74f3ae5b6bdad30904bd18d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646031"
---
# <a name="sql-to-c-character"></a>SQL 到 C：字元
字元的 ODBC SQL 資料類型的識別項是：  
  
 SQL_CHAR  
  
 SQL_VARCHAR  
  
 SQL_LONGVARCHAR  
  
 SQL_WCHAR  
  
 SQL_WVARCHAR  
  
 SQL_WLONGVARCHAR  
  
 下表顯示 ODBC C 資料類型可能會轉換字元的 SQL 資料。 如需資料行和資料表中的詞彙說明，請參閱 <<c0> [ 轉換將資料從 SQL 到 C 資料類型](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 類型識別碼|測試|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|資料的位元組長度 < *Columnsize*<br /><br /> 資料的位元組長度 > = *Columnsize*|data<br /><br /> 截斷的資料|以位元組為單位的資料長度<br /><br /> 以位元組為單位的資料長度|n/a<br /><br /> 01004|  
|SQL_C_WCHAR|字元資料的長度 < *Columnsize*<br /><br /> 字元資料的長度 > = *Columnsize*|data<br /><br /> 截斷的資料|以字元為單位的資料長度<br /><br /> 以字元為單位的資料長度|n/a<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|資料轉換，而不會截斷 [b]<br /><br /> 資料轉換與截斷的小數數字 [a]<br /><br /> 資料轉換會導致遺失的 （相對於小數） 的整數位數 [a]<br /><br /> 資料不是*數值常值*[b]。|data<br /><br /> 截斷的資料<br /><br /> 未定義<br /><br /> 未定義|C 資料類型的位元組數<br /><br /> C 資料類型的位元組數<br /><br /> 未定義<br /><br /> 未定義|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|資料範圍內的數值轉換的資料類型是 [a]<br /><br /> 資料超出範圍的數值轉換的資料類型是 [a]<br /><br /> 資料不是*數值常值*[b]。|data<br /><br /> 未定義<br /><br /> 未定義|C 資料類型的大小<br /><br /> 未定義<br /><br /> 未定義|n/a<br /><br /> 22003<br /><br /> 22018|  
_C_BIT|資料是 0 或 1<br /><br /> 資料是大於 0，小於 2，且不等於 1<br /><br /> 小於 0 或大於或等於 2，資料是<br /><br /> 資料不是*數值常值*|data<br /><br /> 截斷的資料<br /><br /> 未定義<br /><br /> 未定義|1 [b]<br /><br /> 1 [b]<br /><br /> 未定義<br /><br /> 未定義|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|資料的位元組長度 < = *Columnsize*<br /><br /> 資料的位元組長度 > *Columnsize*|data<br /><br /> 截斷的資料|以位元組為單位的資料長度<br /><br /> 資料長度|n/a<br /><br /> 01004|  
|SQL_C_TYPE_DATE|資料值是有效*日期值*[a]<br /><br /> 資料值是有效*時間戳記值*; 時間部分為零 [a]<br /><br /> 資料值是有效*時間戳記值*; 時間部分為非零值 [a]、 [c]<br /><br /> 資料值不是有效*日期值*或是*時間戳記值*[a]|data<br /><br /> data<br /><br /> 截斷的資料<br /><br /> 未定義|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> 未定義|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|資料值是有效*時間值，以及值為 0 的小數秒*[a]<br /><br /> 資料值是有效*時間戳記值或有效的時間值*; 小數秒數部分為零 [a]、 [d]<br /><br /> 資料值是有效*時間戳記值*; 小數秒數部分為非零值 [a]、 [d] [e]<br /><br /> 資料值不是有效*時間值*或是*時間戳記值*[a]|data<br /><br /> data<br /><br /> 截斷的資料<br /><br /> 未定義|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> 未定義|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
_C_TYPE_TIMESTAMP|資料值是有效*時間戳記值或有效的時間值*; 小數秒部分不會被截斷 [a]<br /><br /> 資料值是有效*時間戳記值或有效的時間值*; 小數秒部分截斷 [a]<br /><br /> 資料值是有效*日期值*[a]<br /><br /> 資料值是有效*時間值*[a]<br /><br /> 資料值不是有效*日期值*，*時間值*，或*時間戳記值*[a]|data<br /><br /> 截斷的資料<br /><br /> 資料 [f]<br /><br /> 資料 [g]<br /><br /> 未定義|16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> 未定義|n/a<br /><br /> 01S07<br /><br /> n/a<br /><br /> n/a<br /><br /> 22018|  
|所有 C 間隔類型|資料值是有效*間隔值*; 未截斷<br /><br /> 資料值是有效*間隔值*; 的一個或多個結尾欄位的截斷<br /><br /> 資料是有效的間隔時間。遺漏開頭欄位重大的有效位數<br /><br /> 資料值不是有效的間隔值|data<br /><br /> 截斷的資料<br /><br /> 未定義<br /><br /> 未定義|以位元組為單位的資料長度<br /><br /> 以位元組為單位的資料長度<br /><br /> 未定義<br /><br /> 未定義|n/a<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
  
 [a] 的值*Columnsize*會忽略這項轉換。 驅動程式會假設大小 **TargetValuePtr*是 C 資料類型的大小。  
  
 [b] 這是對應的 C 資料類型的大小。  
  
 [c] 的時間部份*時間戳記值*會被截斷。  
  
 [d] 的日期部份*時間戳記值*會被忽略。  
  
 [截斷時間戳記 e] 的小數秒數部分。  
  
 [時間戳記結構 f] 時間欄位會設定為零。  
  
 [時間戳記結構 g] 的日期欄位設定為目前的日期。  
  
 當字元的 SQL 資料轉換成數值時，會忽略日期、 時間、 時間戳記或時間間隔 C 資料開頭和尾端空白。
