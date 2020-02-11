---
title: 隱含資料指標轉換（ODBC） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e62604404c83e7780d50438a485910e5af4d4f05
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784381"
---
# <a name="implicit-cursor-conversions-odbc"></a>隱含資料指標轉換 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  應用程式可以透過[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)要求資料指標類型，然後執行要求之類型的伺服器資料指標不支援的 SQL 語句。 呼叫**SQLExecute**或**SQLExecDirect**會傳回 SQL_SUCCESS_WITH_INFO 並傳回**SQLGetDiagRec** ：  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 應用程式可以藉由呼叫**SQLGetStmtOption**設定為 SQL_CURSOR_TYPE，來判斷目前正在使用哪一種類型的資料指標。 資料指標類型轉換只適用於一個陳述式。 下一個**SQLExecDirect**或**SQLExecute**將會使用原始的語句資料指標設定來完成。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC&#41;&#40;的資料指標程式設計詳細資料](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
