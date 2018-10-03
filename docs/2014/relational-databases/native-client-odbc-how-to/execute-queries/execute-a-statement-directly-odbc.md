---
title: 執行陳述式直接 (連接 ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4b0333fea0588911274846b05ffc90bc2145309
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48109558"
---
# <a name="execute-a-statement-directly-odbc"></a>直接執行陳述式 (ODBC)
    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>直接並且僅一次執行陳述式  
  
1.  如果陳述式有參數標記，使用[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)繫結至程式變數的每個參數。 使用資料值填入程式變數，然後設定任何資料執行中 (data-at-execution) 參數。  
  
2.  呼叫[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)執行陳述式。  
  
3.  如果資料在執行中輸入的參數， [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)會傳回 SQL_NEED_DATA。 使用區塊傳送資料[SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405)並[SQLPutData](../../native-client-odbc-api/sqlputdata.md)。  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>使用資料行取向的參數繫結多次執行陳述式  
  
1.  呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)設定下列屬性：  
  
     將 SQL_ATTR_PARAMSET_SIZE 設定為參數集 (S) 的數目。  
  
     將 SQL_ATTR_PARAM_BIND_TYPE 設定為 SQL_PARAMETER_BIND_BY_COLUMN。  
  
     將 SQL_ATTR_PARAMS_PROCESSED_PTR 屬性設定為指向 SQLUINTEGER 變數，以保存已處理的參數數目。  
  
     將 SQL_ATTR_PARAMS_STATUS_PTR 設定為指向 SQLUSSMALLINT 變數的陣列[S]，以保存參數狀態指標。  
  
2.  針對每個參數標記：  
  
     配置 S 個參數緩衝區的陣列來儲存資料值。  
  
     配置 S 個參數緩衝區的陣列來儲存資料長度。  
  
     呼叫[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)來將參數資料值和資料長度陣列繫結至陳述式參數。  
  
     設定任何資料執行中的 text 或 image 參數。  
  
     將 S 資料值和 S 資料長度放在繫結參數陣列中。  
  
3.  呼叫[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)執行陳述式。 驅動程式會有效率地執行陳述式 S 次，針對每個參數集執行一次。  
  
4.  如果資料在執行中輸入的參數， [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)會傳回 SQL_NEED_DATA。 使用區塊傳送資料[SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405)並[SQLPutData](../../native-client-odbc-api/sqlputdata.md)。  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>使用資料列取向的參數繫結多次執行陳述式  
  
1.  配置結構的陣列[S]，其中 S 是參數集的數目。 結構中每個參數都具有一個元素，而每個元素則具有兩部分：  
  
     第一個部分是適當資料類型的變數，可保存參數資料。  
  
     第二個部分是 SQLINTEGER 變數，可保存狀態指標。  
  
2.  呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)設定下列屬性：  
  
     將 SQL_ATTR_PARAMSET_SIZE 設定為參數集 (S) 的數目。  
  
     將 SQL_ATTR_PARAM_BIND_TYPE 設定為步驟 1 中配置的結構大小。  
  
     將 SQL_ATTR_PARAMS_PROCESSED_PTR 屬性設定為指向 SQLUINTEGER 變數，以保存已處理的參數數目。  
  
     將 SQL_ATTR_PARAMS_STATUS_PTR 設定為指向 SQLUSSMALLINT 變數的陣列[S]，以保存參數狀態指標。  
  
3.  針對每個參數標記呼叫[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)以參數的資料值和資料長度指標指向它們在步驟 1 中所配置之結構陣列的第一個項目中的變數。 如果參數是資料執行中參數，請設定此參數。  
  
4.  將資料值填入繫結參數緩衝區陣列。  
  
5.  呼叫[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)執行陳述式。 驅動程式會有效率地執行陳述式 S 次，針對每個參數集執行一次。  
  
6.  如果資料在執行中輸入的參數， [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)會傳回 SQL_NEED_DATA。 使用區塊傳送資料[SQLParamData](http://go.microsoft.com/fwlink/?LinkId=58405)並[SQLPutData](../../native-client-odbc-api/sqlputdata.md)。  
  
 **附註**資料行取向和資料列取向的繫結通常比較常搭配[SQLPrepare 函數](http://go.microsoft.com/fwlink/?LinkId=59360)並[SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400)比使用[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399).  
  
## <a name="see-also"></a>另請參閱  
 [執行查詢使用說明主題&#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
