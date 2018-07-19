---
title: 擷取書籤 |Microsoft 文件
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
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a78b232a1cdb5564388cdf9b335a5ce06cfcb68
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911913"
---
# <a name="retrieving-bookmarks"></a>擷取書籤
如果應用程式會使用書籤，它必須設 SQL_UB_VARIABLE 之前準備或執行陳述式來 SQL_ATTR_USE_BOOKMARKS 陳述式屬性。 這是必要的因為它們使用的建置與維護的書籤可以昂貴的作業，因此應用程式可以進行良好時，才應該啟用書籤。  
  
 書籤會當做結果集的資料行 0 傳回。 有三種方式，應用程式進行擷取：  
  
-   繫結結果集的資料行 0。 **SQLFetch**或**SQLFetchScroll**傳回書籤資料行的資料列以及其他資料集中的每個資料列繫結。  
  
-   呼叫**SQLSetPos**來定位到資料列集中的資料列，接著呼叫**SQLGetData**資料行 0。 如果驅動程式支援書籤，它必須一律支援能夠呼叫**SQLGetData**資料行 0，即使不允許應用程式呼叫**SQLGetData**上次繫結之前，其他資料行資料行。  
  
-   呼叫**SQLBulkOperations**與*作業*設 SQL_ADD，引數和繫結資料行 0。 資料指標插入資料列，並傳回資料列的書籤中的繫結的緩衝區。
