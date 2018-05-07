---
title: 並行類型 |Microsoft 文件
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
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b5970995d3b8f881b62556b0f12eac96d302760
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="concurrency-types"></a>並行類型
若要解決此問題的資料指標中的並行減少，ODBC 會公開資料指標並行的四種不同的類型：  
  
-   **唯讀**資料指標可以讀取資料，但無法更新或刪除資料。 這是預設的並行類型。 雖然 DBMS，可能會鎖定資料列來強制執行 Repeatable Read 和 Serializable 隔離等級，它可以使用讀取的鎖定，而非寫入鎖定。 這會導致較高的並行存取，因為其他交易至少可讀取的資料。  
  
-   **鎖定**資料指標使用鎖定以確定更新或刪除在結果集中的資料列所需的最低層級。 這通常會導致非常低的並行存取等級，尤其是在 Repeatable Read 和 Serializable 交易隔離等級。  
  
-   **使用資料列版本的開放式並行存取和使用值的開放式並行存取**資料指標使用開放式並行存取： 它會更新或刪除資料列，只有當它們以來未變更上次讀取。 若要偵測的變更，它會比較資料列版本或值。 並不保證資料指標將無法更新或刪除資料列，但並行比當使用鎖定高出許多。 如需詳細資訊，請參閱下一節，[開放式並行存取](../../../odbc/reference/develop-app/optimistic-concurrency.md)。  
  
 應用程式指定它想要的資料指標陳述式屬性 sql_attr_concurrency 設定為使用哪種類型的並行存取。 若要判斷支援哪些類型，它會呼叫**SQLGetInfo** SQL_SCROLL_CONCURRENCY 選項。
