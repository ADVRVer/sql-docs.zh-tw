---
title: 處理預存程序結果 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 588316b5fd9cc3fa9f5cc5dc2ecefadb3ae248ef
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43060521"
---
# <a name="processing-stored-procedure-results"></a>處理預存程序結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序有四個用於傳回資料的機制：  
  
-   程序中的每個 SELECT 陳述式都會產生一個結果集。  
  
-   程序可以透過輸出參數傳回資料。  
  
-   資料指標輸出參數可以傳回 [!INCLUDE[tsql](../../includes/tsql-md.md)] 伺服器資料指標。  
  
-   程序可以有一個整數的傳回碼。  
  
 應用程式必須能夠處理預存程序中的所有這些輸出。 CALL 或 EXECUTE 陳述式應該包含適用於傳回碼和輸出參數的參數標記。 使用[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)來繫結它們做為輸出參數和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式就會將輸出值傳送到繫結的變數。 輸出參數和傳回碼為傳回給用戶端的最後一個項目[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; 它們不會傳回給應用程式，直到[SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)傳回 sql_no_data 為止。  
  
 ODBC 不支援繫結 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料指標參數。 由於所有輸出參數都必須在執行程序之前進行繫結，因此，ODBC 應用程式無法呼叫包含輸出資料指標參數的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [執行預存程序](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
