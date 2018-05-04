---
title: SQLSetStmtOption 對應 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5b1fd1295586e69f9db0f4084f74540163f45ed
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetstmtoption-mapping"></a>SQLSetStmtOption 對應
當應用程式呼叫**SQLSetStmtOption**透過 ODBC 3 *.x*驅動程式，會呼叫  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 將會產生，如下所示：  
  
-   如果*fOption*表示為字串時，驅動程式管理員呼叫 ODBC 定義陳述式屬性  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   如果*fOption*指出傳回 32 位元整數值，驅動程式管理員呼叫 ODBC 定義陳述式屬性  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   如果*fOption*表示驅動程式定義陳述式屬性，驅動程式管理員呼叫  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 在前述三個情況下， **StatementHandle**引數設定中的值為*hstmt*、*屬性*引數設定中的值為*fOption*，而*ValuePtr*引數設定為值*vParam*。  
  
 驅動程式管理員不知道驅動程式定義陳述式屬性需要字串或 32 位元整數值，因為它必須傳入有效的值*StringLength*引數的**SQLSetStmtAttr**. 如果驅動程式已定義特殊的驅動程式定義陳述式屬性的語意，而需要使用呼叫**SQLSetStmtOption**，就必須支援**SQLSetStmtOption**。  
  
 如果應用程式呼叫**SQLSetStmtOption**設定驅動程式特有的陳述式選項，在 ODBC 3 *.x* ODBC 2 中所定義的驅動程式和選項。*x*版本的驅動程式時，新的資訊清單常數應該定義在 ODBC 3 選項 *.x*驅動程式。 如果在呼叫中使用舊的資訊清單常數**SQLSetStmtOption**，驅動程式管理員會呼叫**SQLSetStmtAttr**與*StringLength*引數設定為 0。  
  
 當應用程式呼叫**SQLSetStmtAttr** SQL_ATTR_USE_BOOKMARKS 設在 ODBC 3 SQL_UB_ON *.x* SQL_ATTR_USE_BOOKMARKS 陳述式屬性設定為 SQL_UB_FIXED 驅動程式。 SQL_UB_ON 是 SQL_UB_FIXED 為相同的常數。 驅動程式管理員會透過 SQL_UB_FIXED 傳遞至驅動程式。 SQL_UB_FIXED 已被取代，在 ODBC 3 *.x*，而 ODBC 3 *.x*驅動程式必須實作它以搭配 ODBC 2。*x*使用固定長度的書籤的應用程式。  
  
 ODBC 3 *.x*驅動程式，驅動程式管理員不會再檢查，看看是否*選項*之間 SQL_STMT_OPT_MIN 和 SQL_STMT_OPT_MAX，或大於 SQL_CONNECT_OPT_DRVR_START。
