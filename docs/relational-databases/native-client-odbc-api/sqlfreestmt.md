---
title: SQLFreeStmt |Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b985db3cb58a7029a3b5ec489d2e23b0c1292919
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73786735"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  常見   
      在 ODBC 3.0 和更新版本中不建議使用**SQLFreeStmt** 。 不過，如果應用程式需要重複使用語句，您仍然應該使用**SQLFreeStmt**搭配**SQL_RESET_PARAMS**和**SQL_UNBIND**選項）。 您也可以使用[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)、 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)、 [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)、 [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)和[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)來取代或複製**SQLFreeStmt**的函式，並應該改用這些函數。  
  
 一般來說，重複使用語句比卸載它們並配置新的更有效率。 不過，在某些情況下，例如重複使用語句，仍然必須使用 SQLFreeStmt。  
  
## <a name="see-also"></a>另請參閱  
 [SQLFreeStmt 函式](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API 實作詳細資料](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
