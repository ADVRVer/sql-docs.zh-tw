---
title: 處理結果 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3c929008c4be8a14bf5233d8d41b3349ba735b7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412951"
---
# <a name="process-results-odbc"></a>處理結果 (ODBC)
    
### <a name="to-process-results"></a>處理結果  
  
1.  擷取結果集資訊。  
  
2.  如果使用繫結資料行，則針對您要繫結到的每個資料行呼叫 [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)，將程式緩衝區繫結到該資料行。  
  
3.  針對結果集中的每個資料列：  
  
    -   呼叫 [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) 以取得下一個資料列。  
  
    -   如果是使用繫結資料行，請使用繫結資料行緩衝區中目前可用的資料。  
  
    -   如果是使用未繫結資料行，請呼叫 [SQLGetData](../native-client-odbc-api/sqlgetdata.md) 一或多次，以取得最後一個繫結資料行之後未繫結資料行的資料。 對 `SQLGetData` 的呼叫應該以資料行號碼的遞增順序進行。  
  
    -   呼叫 `SQLGetData` 多次，以便從 text 或 image 資料行取得資料。  
  
4.  當 [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) 藉由傳回 SQL_NO_DATA 來表示達到結果集的結尾時，請呼叫 [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) 來判斷是否仍有其他的結果集可以使用。  
  
    -   如果該函數傳回 SQL_SUCCESS，表示有其他可用的結果集。  
  
    -   如果該函數傳回 SQL_NO_DATA，表示沒有其他可用的結果集。  
  
    -   如果該函數傳回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR，請呼叫 [SQLGetDiagRec](http://go.microsoft.com/fwlink/?LinkId=58402) 來判斷是否可以使用來自 PRINT 或 RAISERROR 陳述式的輸出。  
  
         如果繫結陳述式參數用於預存程序的輸出參數或傳回值，請使用繫結參數緩衝區中目前可用的資料。 此外，在使用繫結參數時，每個 [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) 或 [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) 呼叫都會執行 SQL 陳述式 *S* 次，其中 *S* 是繫結參數陣列中的元素數。 這代表將要處理 *S* 個結果集，其中每個結果集都是由 SQL 陳述式的單一執行通常會傳回的結果集、輸出參數和傳回碼等所有項目而組成。  
  
    > [!NOTE]  
    >  當結果集包含計算資料列時，每個計算資料列都可以提供為個別的結果集。 這些計算結果集會散佈在一般的資料列內，將一般的資料列分隔成多個結果集。  
  
5.  或者也可以使用 SQL_UNBIND 呼叫 [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)，以釋放任何繫結的資料行緩衝區。  
  
6.  如果有其他可用的結果集，請到步驟 1。  
  
> [!NOTE]  
>  若要在 [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) 傳回 SQL_NO_DATA 之前取消結果集的處理，請呼叫 [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)。  
  
## <a name="see-also"></a>另請參閱  
 [處理結果使用說明主題&#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
