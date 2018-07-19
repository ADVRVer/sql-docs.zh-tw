---
title: SQL 到 c： 時間 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b66aeca41cd705a21e7d6aa6d306a9032e86bba9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908593"
---
# <a name="sql-to-c-time"></a>SQL 到 c： 時間
ODBC SQL 資料類型是次識別碼：  
  
 SQL_TYPE_TIME  
  
 下表顯示 ODBC C 資料類型可能會轉換時間 SQL 資料。 如需的資料行和資料表中的詞彙說明，請參閱[轉換資料從 SQL 到 C 資料類型](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 類型識別碼|測試|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*Columnsize* > 字元位元組長度<br /><br /> *9* <= *Columnsize* < = 字元位元組長度<br /><br /> *Columnsize* < 9|資料<br /><br /> 截斷的資料 [a]<br /><br /> 未定義|以位元組為單位的資料長度<br /><br /> 以位元組為單位的資料長度<br /><br /> 未定義|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*Columnsize* > 字元長度<br /><br /> *9* <= *Columnsize* < = 字元長度<br /><br /> *Columnsize* < 9|資料<br /><br /> 截斷的資料 [a]<br /><br /> 未定義|以字元為單位的資料長度<br /><br /> 以字元為單位的資料長度<br /><br /> 未定義|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|資料的位元組長度 < = *Columnsize*<br /><br /> 資料的位元組長度 > *Columnsize*|資料<br /><br /> 未定義|以位元組為單位的資料長度<br /><br /> 未定義|n/a<br /><br /> 22003|  
|SQL_C_TYPE_TIME|無 [b]|資料|6 [d]|n/a|  
|SQL_C_TYPE_TIMESTAMP|無 [b]|資料 [c]|16 [d]|n/a|  
  
 [a] 會被截斷的小數秒數的時間。  
  
 [b] 的值*Columnsize*會忽略這項轉換。 驅動程式假設大小 **TargetValuePtr*是 C 資料類型的大小。  
  
 [時間戳記結構 c] 的日期欄位設定為目前的日期和時間戳記結構的小數秒欄位設為零。  
  
 [d] 這是對應的 C 資料類型的大小。  
  
 當時間 SQL 資料轉換成 C 字元資料時，產生的字串就會處於 「*hh*:*公釐*:*ss*」 格式。 此格式不受 Windows® 國家/地區設定。
