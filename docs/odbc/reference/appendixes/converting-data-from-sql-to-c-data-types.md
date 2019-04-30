---
title: 將資料從 SQL 轉換成 C 資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC]
- data conversions from SQL to C types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- data types [ODBC], SQL data types
- SQL data types [ODBC], converting to C types
- converting data from SQL to c types [ODBC]
- converting data from SQL to c types [ODBC], about converting
- C data types [ODBC], converting from SQL types
ms.assetid: 029727f6-d3f0-499a-911c-bcaf9714e43b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 553596f474cd8e7c4f4c91911b0167d5b1bc0b4a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224468"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>將資料從 SQL 轉換成 C 資料類型
當應用程式呼叫**SQLFetch**， **SQLFetchScroll**，或**SQLGetData**，驅動程式會從資料來源擷取資料。 如果有必要，它會將資料轉換中的驅動程式擷取它所指定之資料類型的資料型別*TargetType*中的引數**SQLBindCol**或**SQLGetData。** 最後，它將資料儲存在所指的位置*TargetValuePtr*中的引數**SQLBindCol**或是**SQLGetData** （和 ARD 的 SQL_DESC_DATA_PTR 欄位）。  
  
 下表顯示從 ODBC SQL 的支援的轉換成 ODBC C 資料類型的資料類型。 填滿的圓形表示預設轉換，SQL 資料類型 (資料會轉換為時的 C 資料類型的值*TargetType*是 SQL_C_DEFAULT)。 空心圓表示支援的轉換。  
  
 適用於 ODBC 3 *.x*應用程式使用 ODBC 2。*x*驅動程式、 驅動程式特定資料類型可能不支援的轉換。  
  
 已轉換的資料格式不會受到 Windows® 國家/地區設定。  
  
 下列各節中的資料表會描述如何在驅動程式或資料來源將轉換從資料來源擷取資料支援所有 ODBC C 資料類型所支援的 ODBC SQL 資料類型的轉換所需的驅動程式。 指定的 ODBC SQL 資料類型，資料表的第一個資料行列出的合法的輸入的值*TargetType*中的引數**SQLBindCol**並**SQLGetData**。 第二個資料行列出經常使用的測試結果*Columnsize*中所指定的引數**SQLBindCol**或**SQLGetData**，若要執行的驅動程式判斷是否可以將轉換的資料。 針對每個結果，第三個和第四個資料行列出值放在所指定的緩衝區*TargetValuePtr*並*StrLen_or_IndPtr*中指定的引數**SQLBindCol**或是**SQLGetData**驅動程式已嘗試將資料轉換之後。 ( *StrLen_or_IndPtr*引數會對應至 ARD 的 SQL_DESC_OCTET_LENGTH_PTR 欄位。)最後一欄會列出每個結果所傳回的 SQLSTATE **SQLFetch**， **SQLFetchScroll**，或**SQLGetData**。  
  
 如果*TargetType*中的引數**SQLBindCol**或是**SQLGetData**包含未顯示在指定的 ODBC SQL 資料類型，資料表中的 ODBC C 資料類型的識別項**SQLFetch**， **SQLFetchScroll**，或**SQLGetData**傳回 SQLSTATE 07006 （受限制的資料類型屬性違規）。 如果*TargetType*引數包含指定的驅動程式專用的 SQL 資料類型轉換至 ODBC C 資料類型的識別項和驅動程式時，不支援這項轉換**SQLFetch**，**SQLFetchScroll**，或**SQLGetData**傳回 SQLSTATE HYC00 （未實作選擇性功能）。  
  
 雖然它未顯示在資料表中，驅動程式會傳回所指定的緩衝區的 SQL_NULL_DATA *StrLen_or_IndPtr*引數時，SQL 資料值為 NULL。 如需使用的說明*StrLen_or_IndPtr*時進行多個呼叫會擷取資料，請參閱[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)函式描述。 在 當 SQL 資料轉換成 C 字元資料時，傳回的字元計數\* *StrLen_or_IndPtr*不包含終止 null 位元組。 如果*TargetValuePtr*為 null 指標， **SQLGetData**會傳回 SQLSTATE HY009 （使用無效的 null 指標），在**SQLBindCol**，這會解除繫結資料行。  
  
 資料表中使用下列術語和慣例：  
  
-   **資料的位元組長度**是可傳回的 C 資料的位元組數目 **TargetValuePtr*，不論是否將截斷資料，再將它傳回應用程式。 針對字串資料，這不包括 null 結束字元的空間。  
  
-   **字元的位元組長度**是以字元格式顯示資料所需的位元組總數。 這是針對每個區段中的 C 資料類型所定義[顯示大小](../../../odbc/reference/appendixes/display-size.md)，不同之處在於字元位元組長度是以位元組為單位，而顯示大小是以字元為單位。  
  
-   中的單字*斜體*代表函式引數或 SQL 文法的項目。 如需語法的文法項目，請參閱[附錄 c:SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)。  
  
 此章節包含下列主題。  
  
-   [SQL 到 c:字元](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [SQL 到 c:Numeric](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [SQL 到 c:Bit](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [SQL 到 c:二進位檔](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [SQL 到 c:日期](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [SQL 到 c:GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [SQL 到 c:時間](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [SQL 到 c:時間戳記](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [SQL 到 c:年月間隔](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [SQL 到 c:日期時間間隔](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [SQL 到 C 資料轉換範例](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
