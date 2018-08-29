---
title: 使用陳述式與 JDBC 驅動程式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f8f3e8f-841e-4449-9154-b5366870121f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 983cf2bcbdbfd91f10331310dbf4318cd5b3fb5e
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786087"
---
# <a name="using-statements-with-the-jdbc-driver"></a>搭配 JDBC Driver 使用陳述式

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 可用許多不同的方式來處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料。 利用輸入和輸出參數，JDBC 驅動程式可用來針對資料庫執行 SQL 陳述式，或用於資料庫中呼叫預存程序。 JDBC 驅動程式也支援使用 SQL 逸出序列、更新計數、自動產生的金鑰，以及在批次作業內執行更新。  
  
JDBC 驅動程式提供三種類別來擷取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料：  
  
1. [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) - 用於執行不含參數的 SQL 陳述式。  
  
2. [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) - (繼承自 SQLServerStatement)，用於執行可能包含 IN 參數的已編譯 SQL 陳述式。  
  
3. [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) - (繼承自 SQLServerPreparedStatement)，用於執行可能包含 IN 參數、OUT 參數或這兩者的預存程序。  
  
 本節中的主題討論如何使用這三個陳述式類別來處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料。  
  
## <a name="in-this-section"></a>本節內容  

| 主題                                                                                                    | Description                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [搭配使用陳述式與 SQL](../../connect/jdbc/using-statements-with-sql.md)                             | 描述如何搭配 JDBC 驅動程式來使用 SQL 陳述式，以處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料。    |
| [搭配使用陳述式與預存程序](../../connect/jdbc/using-statements-with-stored-procedures.md) | 描述如何搭配 JDBC 驅動程式來使用預存程序，以處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料。 |
| [使用多個結果集](../../connect/jdbc/using-multiple-result-sets.md)                           | 描述如何使用 JDBC 驅動程式來擷取多個結果集的資料。                                                                       |
| [使用 SQL 逸出序列](../../connect/jdbc/using-sql-escape-sequences.md)                           | 描述如何使用 SQL 逸出序列，例如日期和時間常值及函數。                                                               |
| [使用自動產生的金鑰](../../connect/jdbc/using-auto-generated-keys.md)                             | 描述如何使用自動產生的金鑰。                                                                                                     |
| [執行批次作業](../../connect/jdbc/performing-batch-operations.md)                         | 描述如何使用 JDBC 驅動程式來執行批次作業。                                                                                      |
| [處理複雜陳述式](../../connect/jdbc/handling-complex-statements.md)                         | 描述如何使用 JDBC 驅動程式來執行複雜陳述式，這類陳述式可執行各種不同的工作，並可能傳回不同類型的資料。               |
  
## <a name="see-also"></a>另請參閱

[JDBC Driver 概觀](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
