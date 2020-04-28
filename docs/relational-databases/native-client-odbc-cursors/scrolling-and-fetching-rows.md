---
title: 滾動和提取資料列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ae9f1079f329951045d4b3f61b39c12efc153fb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302484"
---
# <a name="scrolling-and-fetching-rows"></a>捲動與提取資料列
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  若要使用可捲動的資料指標，ODBC 應用程式必須：  
  
-   使用[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)設定資料指標功能。  
  
-   使用**SQLExecute**或**SQLExecDirect**開啟資料指標。  
  
-   使用**SQLFetch**或[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)來滾動和提取資料列。  
  
 **SQLFetch**和**SQLFetchSroll**都可以一次提取資料列區塊。 傳回的資料列數目是藉由使用**SQLSetStmtAttr**來設定 SQL_ATTR_ROW_ARRAY_SIZE 參數所指定。  
  
 ODBC 應用程式可以使用**SQLFetch** ，透過順向資料指標來提取。  
  
 **SQLFetchScroll**是用來在資料指標周圍進行滾動。 除了相對提取以外， **SQLFetchScroll**支援提取下一個、先前的第一個和最後一個資料列集（從目前資料列集的開頭提取資料列集*n*個數據列）和絕對提取（提取從第*n*行開始的資料列集）。 如果*n*在絕對提取中為負數，則會從結果集的結尾計算資料列。 資料列的絕對提取 -1 表示提取從結果集的最後一個資料列開始的資料列集。  
  
 僅針對其區塊資料指標功能使用**SQLFetchScroll**的應用程式（例如報表）可能會通過單一時間的結果集，而只會使用提取下一個資料列集的選項。 另一方面，以螢幕為基礎的應用程式可以利用**SQLFetchScroll**的所有功能。 如果應用程式將資料列集大小設定為螢幕上顯示的資料列數目，並將螢幕緩衝區系結至結果集，則可以直接將捲軸作業轉譯為呼叫**SQLFetchScroll**。  
  
|捲軸作業|SQLFetchScroll 捲動選項|  
|--------------------------|-------------------------------------|  
|向上捲動一頁|SQL_FETCH_PRIOR|  
|向下捲動一頁|SQL_FETCH_NEXT|  
|向上捲動一行|FetchOffset 等於-1 的 SQL_FETCH_RELATIVE|  
|向下捲動一行|包含 FetchOffset 的 SQL_FETCH_RELATIVE 等於 1|  
|捲動方塊到頂端|SQL_FETCH_FIRST|  
|捲動方塊到底部|SQL_FETCH_LAST|  
|隨機捲動方塊位置|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [在 ODBC 中的資料列上加上書籤](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>另請參閱  
 [&#40;ODBC&#41;使用資料指標](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
