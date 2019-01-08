---
title: 陳述式控制代碼 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f249bb13ece6382e96dfe953b1d3c1d96c7bf65
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52523695"
---
# <a name="statement-handles"></a>陳述式控制代碼
A*陳述式*最容易想像成 SQL 陳述式，例如**選取\*從員工**。 不過，在陳述式是不只是 SQL 陳述式-它包含所有與該 SQL 陳述式，例如任何結果集的陳述式所建立和執行陳述式中使用的參數相關聯的資訊。 陳述式甚至不必有應用程式定義的 SQL 陳述式。 例如，當目錄函數這類**SQLTables**執行上一個陳述式，它會執行預先定義的 SQL 陳述式會傳回一份資料表的名稱。  
  
 陳述式控制代碼識別每個陳述式。 陳述式是單一連線，與相關聯，而且可以有多個陳述式，在該連接上。 有些驅動程式限制支援; 作用中陳述式的數目選項 SQL_MAX_CONCURRENT_ACTIVITIES **SQLGetInfo**指定驅動程式支援在單一連接的幾個作用中陳述式。 陳述式會定義為*active*如果有暫止的結果，而結果是結果集還是受影響的資料列計數**插入**， **UPDATE**，或**刪除**陳述式或資料傳送至多個呼叫**SQLPutData**。  
  
 在一段程式碼來實作 ODBC （驅動程式管理員或驅動程式），陳述式控制代碼會識別包含陳述式的詳細資訊，例如結構：  
  
-   陳述式的狀態  
  
-   目前的陳述式層級診斷  
  
-   應用程式變數的位址繫結至陳述式的參數和結果集資料行  
  
-   目前的設定，每個陳述式屬性  
  
 陳述式控制代碼可用於大部分的 ODBC 函式。 值得注意的是，它們用在函式來繫結參數和結果集資料行 (**SQLBindParameter**並**SQLBindCol**)、 準備和執行陳述式 (**SQLPrepare****SQLExecute**，並**SQLExecDirect**)，擷取中繼資料 (**SQLColAttribute**並**SQLDescribeCol**)，擷取結果 (**SQLFetch**)，並擷取診斷 (**SQLGetDiagField**並**SQLGetDiagRec**)。 它們也會使用目錄函式中 (**SQLColumns**， **SQLTables**等等) 和一些其他功能。  
  
 陳述式控制代碼被配置**SQLAllocHandle**和與釋放**SQLFreeHandle**。
