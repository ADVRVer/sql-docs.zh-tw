---
title: 使用資料指標 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc53253c93f5f52c6bbe00941eadbf14b65d5f64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206817"
---
# <a name="using-cursors-odbc"></a>使用資料指標 (ODBC)
  ODBC 支援的資料指標模型允許：  
  
-   數種資料指標類型。  
  
-   在資料指標內捲動和定位。  
  
-   多個並行選項。  
  
-   定位更新。  
  
 ODBC 應用程式很少會宣告及開啟資料指標，或使用任何與資料指標相關的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。 ODBC 會針對每個從 SQL 陳述式傳回的結果集而自動開啟資料指標。 資料指標的特性會以陳述式屬性設定為受[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)之前使用了 SQL 陳述式。 用來處理結果集的 ODBC API 函數支援完整的資料指標功能，包括提取、捲動和定位更新等。  
  
 這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼和 ODBC 應用程式如何搭配資料指標使用的比較。  
  
|Action|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|定義資料指標行為|指定透過 DECLARE CURSOR 參數|使用設定資料指標屬性[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)|  
|開啟資料指標|宣告資料指標開啟*cursor_name*|**SQLExecDirect**或**SQLExecute**|  
|提取資料列|FETCH|**SQLFetch**或[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)|  
|定點更新|UPDATE 或 DELETE 上的 WHERE CURRENT OF 子句|**SQLSetPos**|  
|關閉資料指標|關閉*cursor_name* DEALLOCATE|[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)|  
  
 實作於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的伺服器資料指標支援 ODBC 資料指標模型的功能。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 驅動程式使用伺服器資料指標支援 ODBC API 的資料指標功能。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何實作資料指標](implementation/how-cursors-are-implemented.md)  
  
-   [資料指標類型](cursor-types.md)  
  
-   [資料指標行為](cursor-behaviors.md)  
  
-   [資料指標屬性](properties/cursor-properties.md)  
  
-   [資料指標程式設計詳細資料&#40;ODBC&#41;](programming/cursor-programming-details-odbc.md)  
  
-   [捲動與擷取資料列](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [定位更新&#40;ODBC&#41;](positioned-updates-odbc.md)  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [CLOSE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/close-transact-sql)   
 [資料指標](../../relational-databases/cursors.md)   
 [DEALLOCATE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/deallocate-transact-sql)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql)   
 [FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql)   
 [OPEN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/open-transact-sql)  
  
  
