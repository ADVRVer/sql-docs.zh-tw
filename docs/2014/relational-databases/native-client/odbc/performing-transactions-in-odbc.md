---
title: ODBC 中的交易 |Microsoft 文件
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
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b146a3f4a3331ddcfc7606825a0300b986f1a116
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36030999"
---
# <a name="transactions-in-odbc"></a>ODBC 中的交易
  ODBC 中的交易會在連接層級進行管理。 當應用程式完成交易時，它會認可或回復透過該連接之所有陳述式控制代碼完成的所有工作。 若要認可或回復交易，應用程式應該呼叫[SQLEndTran](../../native-client-odbc-api/sqlendtran.md)而非提交 COMMIT 或 ROLLBACK 陳述式。  
  
 應用程式呼叫[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)管理交易的兩個 ODBC 模式之間切換：  
  
-   自動認可模式  
  
     每個陳述式都會在成功完成時自動認可。 當您在自動認可模式下執行時，不需要其他任何交易管理函數。  
  
-   手動認可模式  
  
     所有執行之陳述式包含相同交易中，直到明確停止藉由呼叫**SQLEndTran**。  
  
 自動認可模式是 ODBC 的預設交易模式。 當建立連線時，它處於自動認可模式，直到**SQLSetConnectAttr**呼叫以切換到自動認可模式設定的手動認可模式。 當應用程式關閉自動認可時，傳送到資料庫的下一個陳述式會啟動交易。 接著，交易會維持作用中直到應用程式呼叫**SQLEndTran** SQL_COMMIT 或 SQL_ROLLBACK 選項。 命令傳送至資料庫之後**SQLEndTran**啟動下一個交易。  
  
 如果應用程式從手動認可模式切換到自動認可模式，驅動程式會認可目前在連接上開啟的所有交易。  
  
 ODBC 應用程式不應使用 Transact-SQL 交易陳述式 (例如，BEGIN TRANSACTION、COMMIT TRANSACTION 或 ROLLBACK TRANSACTION)，因為這可能會在驅動程式上造成未定的行為。 ODBC 應用程式應該在自動認可模式下執行並使用任何交易管理函數或陳述式，或在手動認可模式下執行並且使用 ODBC **SQLEndTran**函式，來認可或回復交易。  
  
## <a name="see-also"></a>另請參閱  
 [執行交易&#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  