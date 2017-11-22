---
title: "執行陳述式 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e617e4550766b7952961c3dae6830eaebdd2686a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="executing-statements-odbc"></a>執行陳述式 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會提供各種不同的方法可執行的 SQL 陳述式[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料庫：  
  
-   直接執行  
  
-   準備執行  
  
 直接執行包括建立字元字串，包含[!INCLUDE[tsql](../../../includes/tsql-md.md)]陳述式，並提交執行使用**SQLExecDirect**函式。 準備執行則包括建立含有 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的字元字串，然後在兩個階段中執行此字串。 第一個階段會使用[SQLPrepare 函數](http://go.microsoft.com/fwlink/?LinkId=59360)函式來剖析並編譯中的陳述式的執行計畫[!INCLUDE[ssDE](../../../includes/ssde-md.md)]。 第二個階段會使用**SQLExecute**函式可執行先前已備妥的執行計畫。 這樣會省下每次執行時的剖析和編譯負擔。 應用程式通常會使用備妥的執行來重複執行相同且參數化的 SQL 陳述式。  
  
 直接和準備執行都可以執行單一 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式或 SQL 陳述式批次，也可以呼叫預存程序。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [直接執行](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [備妥的執行](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [程序](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [陳述式的批次](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [ISO 選項的作用](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>請參閱＜  
 [執行查詢 &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
