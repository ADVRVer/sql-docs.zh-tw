---
title: 呼叫層級介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], CLI
- CLI [ODBC], using CLI
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], CLI
- call-level interface [ODBC], using call-level interface
ms.assetid: 42257bb6-0bf1-4533-a4ef-4a6dd2aecb18
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6094e97d73dc11ec4c6507b6d5018353e2e345e2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907473"
---
# <a name="call-level-interfaces"></a>呼叫層級介面
將 SQL 陳述式傳送至 DBMS 的最後一個技巧是透過呼叫層級介面 (CLI)。 呼叫層級介面提供的應用程式可以呼叫的 DBMS 函式的程式庫。 因此，而不是嘗試另一種程式設計語言與混合 SQL，則呼叫層級介面便是類似於大部分的程式設計人員會習慣使用，例如字串、 I/O 或 C.便箋支援內嵌式的 SQL 的 Dbms 中的數學程式庫常式的程式庫已經呼叫層級介面，先行編譯器所產生的呼叫。 不過，這些呼叫都未記載並可能有所變更，恕不另行通知。  
  
 在用戶端/伺服器架構中，在其中一部電腦上位於應用程式 （用戶端） 和 DBMS （伺服器） 位於不同的電腦上常用呼叫層級介面。 應用程式呼叫 CLI 函式在本機系統上，且這些呼叫會透過網路傳送至 DBMS 進行處理。  
  
 呼叫層級介面是類似於動態 SQL，SQL 陳述式傳遞至 DBMS 進行執行階段處理，但它不同於內嵌的 SQL 整個，沒有任何內嵌的 SQL 陳述式，而且沒有先行編譯器需要。  
  
 使用呼叫層級介面通常需要執行下列步驟：  
  
1.  應用程式呼叫連線到 DBMS CLI 函式。  
  
2.  應用程式建置的 SQL 陳述式，並將它放在緩衝區中。 接著，它會呼叫一或多個 CLI 函式，將陳述式準備和執行 DBMS。  
  
3.  如果陳述式的 SELECT 陳述式，則應用程式會呼叫 CLI 函式傳回結果的應用程式緩衝區中。 一般而言，此函式會傳回一個資料列或一個資料行一次。  
  
4.  應用程式呼叫中斷 DBMS CLI 函式。
