---
title: SQL 到 C：字元 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3486c0fcf5cefc39c4b85af814d7d3c1d609b4e3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296668"
---
# <a name="sql-to-c-character"></a>SQL 到 C：字元

字元 ODBC SQL 資料類型的識別碼如下：

- SQL_CHAR
- SQL_VARCHAR
- SQL_LONGVARCHAR
- SQL_WCHAR
- SQL_WVARCHAR
- SQL_WLONGVARCHAR

下表顯示字元 SQL 資料可能轉換成的 ODBC C 資料類型。 如需資料表中的資料行和詞彙的說明，請參閱將[資料從 SQL 轉換成 C 資料類型](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  

|C 類型識別碼|測試|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|
|:----------------|:---|:-------------|:---------------|:-------|
|SQL_C_CHAR|資料 < *BufferLength*的位元組長度<br /><br /> 資料 >的位元組長度 = *BufferLength*|資料<br /><br /> 截斷的資料|資料長度（以位元組為單位）<br /><br /> 資料長度（以位元組為單位）|n/a<br /><br /> 01004|  
|SQL_C_WCHAR|資料 < *BufferLength*的字元長度<br /><br /> 資料 >= *BufferLength*的字元長度|資料<br /><br /> 截斷的資料|資料長度（以字元為單位）<br /><br /> 資料長度（以字元為單位）|n/a<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|不截斷而轉換的資料 [b]<br /><br /> 以截斷小數數位 [a] 轉換的資料<br /><br /> 資料的轉換會導致整體遺失（相對於小數）數位 [a]<br /><br /> 資料不是*數值常*值 [b]|資料<br /><br /> 截斷的資料<br /><br /> 未定義<br /><br /> 未定義|C 資料類型的位元組數目<br /><br /> C 資料類型的位元組數目<br /><br /> 未定義<br /><br /> 未定義|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|資料位於要轉換數位的資料類型範圍內 [a]<br /><br /> 資料超出要轉換數位的資料類型範圍 [a]<br /><br /> 資料不是*數值常*值 [b]|資料<br /><br /> 未定義<br /><br /> 未定義|C 資料類型的大小<br /><br /> 未定義<br /><br /> 未定義|n/a<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BIT|資料為0或1<br /><br /> 資料大於0、小於2，且不等於1<br /><br /> 資料小於0或大於或等於2<br /><br /> 資料不是*數值常*值|資料<br /><br /> 截斷的資料<br /><br /> 未定義<br /><br /> 未定義|1 [b]<br /><br /> 1 [b]<br /><br /> 未定義<br /><br /> 未定義|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|資料 <的位元組長度 = *BufferLength*<br /><br /> 資料 > *BufferLength*的位元組長度|資料<br /><br /> 截斷的資料|資料長度（以位元組為單位）<br /><br /> 資料的長度|n/a<br /><br /> 01004|  
|SQL_C_TYPE_DATE|資料值是有效的*日期值*[a]<br /><br /> 資料值是有效的*時間戳記-值*;時間部分為零 [a]<br /><br /> 資料值是有效的*時間戳記-值*;時間部分是非零的 [a]、[c]<br /><br /> 資料值不是有效的*日期值*或*時間戳記-值*[a]|資料<br /><br /> 資料<br /><br /> 截斷的資料<br /><br /> 未定義|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> 未定義|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|資料值是有效的*時間值，小數秒數值為 0*[a]<br /><br /> 資料值是有效的時間*戳值或有效的時間值*;小數秒數部分為零 [a]、[d]<br /><br /> 資料值是有效的*時間戳記-值*;小數秒部分是非零的 [a]、[d]、[e]<br /><br /> 資料值不是有效的*時間值*或*時間戳記-值*[a]|資料<br /><br /> 資料<br /><br /> 截斷的資料<br /><br /> 未定義|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> 未定義|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIMESTAMP|資料值是有效的時間*戳值或有效的時間值*;小數秒部分未截斷 [a]<br /><br /> 資料值是有效的時間*戳值或有效的時間值*;小數秒數部分截斷 [a]<br /><br /> 資料值是有效的*日期值*[a]<br /><br /> 資料值是有效的*時間值*[a]<br /><br /> 資料值不是有效的*日期值*、*時間值*或*時間戳記-值*[a]|資料<br /><br /> 截斷的資料<br /><br /> 資料 [f]<br /><br /> 資料 [g]<br /><br /> 未定義|16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> 未定義|n/a<br /><br /> 01S07<br /><br /> n/a<br /><br /> n/a<br /><br /> 22018|  
|所有 C 間隔類型|資料值是有效的*間隔值*。不截斷<br /><br /> 資料值是有效的*間隔值*。截斷一或多個尾端欄位<br /><br /> 資料是有效的間隔;前導欄位明顯有效位數已遺失<br /><br /> 資料值不是有效的間隔值|資料<br /><br /> 截斷的資料<br /><br /> 未定義<br /><br /> 未定義|資料長度（以位元組為單位）<br /><br /> 資料長度（以位元組為單位）<br /><br /> 未定義<br /><br /> 未定義|n/a<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|

 [a] 這項轉換會忽略*BufferLength*的值。 驅動程式假設 **TargetValuePtr*的大小是 C 資料類型的大小。  
  
 [b] 這是對應 C 資料類型的大小。  
  
 [c]*時間戳記值*的時間部分會被截斷。  
  
 [d] 已忽略*timestamp 值*的日期部分。  
  
 [e] 時間戳記的小數秒部分已截斷。  
  
 [f] 時間戳記結構的時間欄位會設定為零。  
  
 [g] 時間戳記結構的日期欄位設定為目前的日期。  

**多餘空格**

當 SQL 字元資料轉換成下列任何一種類型時，會忽略開頭和尾端空格：

- date
- NUMERIC
- time
- timestamp
- 間隔 C 資料
