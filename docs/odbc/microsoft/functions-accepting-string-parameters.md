---
title: 接受字串參數的函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], string parameters
- ODBC desktop database drivers [ODBC], string parameters
- Jet-based ODBC drivers [ODBC], string parameters
- functions [ODBC], string parameters
- string parameters [ODBC]
ms.assetid: 869b8421-f71e-4dfd-adce-691bd3012b16
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4165dd51437f143351835bc1739ffb8279bd04ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952488"
---
# <a name="functions-accepting-string-parameters"></a>接受字串參數的函式
所有接受字串參數的函式都會轉換成 Unicode。 （將會匯出函數的 "W" 形式）。位元組計數會轉換成這些適用 ODBC Api 的字元計數。 這適用于下列函數：  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLColAttributes**  
  
-   **SQLDescribeCol**  
  
-   **SQLError** （由**SQLGetDiagField**取代）  
  
-   **SQLExecDirect**  
  
-   **SQLGetCursorName**  
  
-   **SQLSetCursorName**  
  
-   **SQLGetStmtAttr**  
  
-   **SQLGetInfo**  
  
-   **SQLGetStmtOption** （變成**SQLGetStmtAttr**）  
  
-   **SQLSetStmtOption** （變成**SQLSetStmtAttr**）  
  
-   **SQLGetConnectOption**  
  
-   **SQLSetConnectOption**  
  
-   **SQLGetTypeInfo**  
  
-   **SQLStatistics**  
  
-   **SQLTables**  
  
-   **SQLNativeSQL**  
  
-   **SQLSpecialColumns**  
  
-   **ConfigDSNEx**  
  
-   **ConfigDSN**
