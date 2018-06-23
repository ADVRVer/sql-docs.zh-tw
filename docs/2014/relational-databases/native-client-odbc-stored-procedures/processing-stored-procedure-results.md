---
title: 處理預存程序結果 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cfc9756a6c55e4ff894b56ec483e921a1acb6b68
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36030517"
---
# <a name="processing-stored-procedure-results"></a>處理預存程序結果
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序有四個用於傳回資料的機制：  
  
-   程序中的每個 SELECT 陳述式都會產生一個結果集。  
  
-   程序可以透過輸出參數傳回資料。  
  
-   資料指標輸出參數可以傳回 [!INCLUDE[tsql](../../includes/tsql-md.md)] 伺服器資料指標。  
  
-   程序可以有一個整數的傳回碼。  
  
 應用程式必須能夠處理預存程序中的所有這些輸出。 CALL 或 EXECUTE 陳述式應該包含適用於傳回碼和輸出參數的參數標記。 使用[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)來繫結它們做為輸出參數和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式會將輸出值傳送至繫結的變數。 輸出參數和傳回碼是用戶端傳回的最後一個項目[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; 它們不會傳回給應用程式，直到[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)傳回 sql_no_data 為止。  
  
 ODBC 不支援繫結 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料指標參數。 由於所有輸出參數都必須在執行程序之前進行繫結，因此，ODBC 應用程式無法呼叫包含輸出資料指標參數的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [執行預存程序](running-stored-procedures.md)  
  
  