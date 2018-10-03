---
title: 繫結參數標記 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c71967bd72f7f13a725d47517cb9e66eee7da87f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645986"
---
# <a name="binding-parameter-markers"></a>繫結參數標記
藉由呼叫應用程式繫結的參數**SQLBindParameter**。 **SQLBindParameter**將一個參數繫結一次。 有了它，應用程式則指定下列項目：  
  
-   參數數目。 參數會以遞增的參數順序，在 SQL 陳述式，從數字 1 開始編號。 法律指定較高的參數號碼時比 SQL 陳述式中的參數數目，參數值時，會忽略執行的陳述式。  
  
-   參數類型 （輸入、 輸入/輸出或輸出）。 除了程序呼叫中的參數，所有參數都是輸入的參數。 如需詳細資訊，請參閱 <<c0> [ 程序參數](../../../odbc/reference/develop-app/procedure-parameters.md)稍後這一節。  
  
-   C 資料類型、 位址和位元組長度的變數繫結至參數。 驅動程式必須能夠將 C 資料類型的資料轉換成 SQL 資料類型或傳回錯誤。 如需支援的轉換，請參閱[轉換將資料從 C 到 SQL 資料類型](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)附錄 d： 資料型別中。  
  
-   SQL 資料類型、 有效位數和小數位數參數本身。  
  
-   長度/指標緩衝區的位址。 它提供二進位或字元資料的位元組長度、 指定資料為 NULL，或指定的資料將會傳送具有**SQLPutData**。 如需詳細資訊，請參閱 <<c0> [ 使用長度/指標值](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)。  
  
 例如，下列程式碼繫結*業務員*並*CustID*的銷售人員及 CustID 資料行的參數。 因為*SalesPerson*包含字元資料，也就是可變長度，程式碼會指定的位元組長度*銷售人員*(11) 並繫結*SalesPersonLenOrInd*至包含資料的位元組長度*業務員*。 這項資訊不需要*CustID*因為它包含固定長度的整數資料。  
  
```  
SQLCHAR       SalesPerson[11];  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLUINTEGER   CustID;  
  
// Bind SalesPerson to the parameter for the SalesPerson column and  
// CustID to the parameter for the CustID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 10, 0,  
                  SalesPerson, sizeof(SalesPerson), &SalesPersonLenOrInd);  
SQLBindParameter(hstmt1, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &CustID, 0, &CustIDInd);  
  
// Set values of salesperson and customer ID and length/indicators.  
strcpy_s((char*)SalesPerson, _countof(SalesPerson), "Garcia");  
SalesPersonLenOrInd = SQL_NTS;  
CustID = 1331;  
CustIDInd = 0;  
  
// Execute a statement to get data for all orders made to the specified  
// customer by the specified salesperson.  
SQLExecDirect(hstmt1,"SELECT * FROM Orders WHERE SalesPerson=? AND CustID=?",SQL_NTS);  
```  
  
 當**SQLBindParameter**是呼叫，驅動程式將此資訊儲存在結構中，陳述式。 執行陳述式時，它會使用擷取的參數資料，並將它傳送至資料來源的資訊。  
  
> [!NOTE]  
>  在 ODBC 1.0 參數已繫結與**SQLSetParam**。 對應呼叫之間的驅動程式管理員**SQLSetParam**並**SQLBindParameter**，取決於應用程式和驅動程式所使用的 ODBC 版本。
