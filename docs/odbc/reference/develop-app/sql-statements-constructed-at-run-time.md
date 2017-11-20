---
title: "在執行階段建構 SQL 陳述式 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8ccd79048c250c73867752ebaf0b2b7060a6c19b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sql-statements-constructed-at-run-time"></a>在執行階段建構 SQL 陳述式
通常執行臨機操作分析的應用程式在執行階段建立 SQL 陳述式。 例如，試算表可能會允許使用者選取要從中擷取資料的資料行：  
  
```  
// SQL_Statements_Constructed_at_Run_Time.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <sqltypes.h>  
  
int main() {  
   SQLCHAR *Statement = 0, *TableName = 0;  
   SQLCHAR **TableNamesArray, **ColumnNamesArray = 0;  
   BOOL *ColumnSelectedArray = 0;  
   BOOL  CommaNeeded;  
   SQLSMALLINT i = 0, NumColumns = 0;  
  
   // Use SQLTables to build a list of tables (TableNamesArray[]). Let the  
   // user select a table and store the selected table in TableName.  
  
   // Use SQLColumns to build a list of the columns in the selected table  
   // (ColumnNamesArray). Set NumColumns to the number of columns in the  
   // table. Let the user select one or more columns and flag these columns  
   // in ColumnSelectedArray[].  
  
   // Build a SELECT statement from the selected columns.  
   CommaNeeded = FALSE;  
   Statement = (SQLCHAR*)malloc(8);  
   strcpy_s((char*)Statement, 8, "SELECT ");  
  
   for (i = 0 ; i = NumColumns ; i++) {  
      if (ColumnSelectedArray[i]) {  
         if (CommaNeeded)  
            strcat_s((char*)Statement, sizeof(Statement), ",");  
         else  
            CommaNeeded = TRUE;  
         strcat_s((char*)Statement, sizeof(Statement), (char*)ColumnNamesArray[i]);  
      }  
   }  
  
   strcat_s((char*)Statement, 15, " FROM ");  
   // strcat_s((char*)Statement, 100, (char*)TableName);  
  
   // Execute the statement . It will be executed once, do not prepare it.  
   // SQLExecDirect(hstmt, Statement, SQL_NTS);  
}  
```  
  
 應用程式通常在執行階段建構 SQL 陳述式的另一個類別是應用程式開發環境。 不過，在建構陳述式是硬式編碼它們正在建置，其中它們可以通常最佳化和測試應用程式中。  
  
 在執行階段建構 SQL 陳述式的應用程式可以向使用者提供極大的彈性。 可以從上述的範例中，即使不支援這類常見的作業為看出**其中**子句， **ORDER BY**子句，或是聯結，在執行階段建構 SQL 陳述式是相當複雜比硬式編碼的陳述式。 此外，測試這類應用程式會有問題因為它們可以建立任意數目的 SQL 陳述式。  
  
 在執行階段建構 SQL 陳述式的潛在缺點是，花費更多的時間比使用硬式編碼的陳述式建構的陳述式。 幸運的是，這是很少的問題。 這類應用程式通常是大量的使用者介面資源，以及應用程式花的時間建構 SQL 陳述式是通常只有少量相較於使用者耗費輸入準則的時間。

