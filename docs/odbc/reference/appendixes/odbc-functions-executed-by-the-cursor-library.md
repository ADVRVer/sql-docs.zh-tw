---
title: 資料指標程式庫所執行的 ODBC 函數 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: 2f1d3386-7e59-4d55-a5b4-3440b61343a3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 789aae8023a5c4d48b14b6cb91a8d11a41403cac
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-functions-executed-by-the-cursor-library"></a>資料指標程式庫所執行的 ODBC 函數
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 Microsoft 建議使用驅動程式的資料指標功能。  
  
 資料指標程式庫執行下列函數。 當應用程式呼叫函式，這份清單中時，驅動程式管理員會叫用資料指標程式庫，而不是驅動程式。 請注意，資料指標程式庫，可能會執行函式呼叫驅動程式。  
  
|||  
|-|-|  
|**SQLBindCol**|**SQLGetStmtOption**|  
|**SQLBindParam**|**SQLNativeSql**|  
|**SQLBindParameter**|**SQLNumParams**|  
|**SQLCloseCursor**|**SQLParamOptions**|  
|**SQLEndTran**|**SQLRowCount**|  
|**SQLExtendedFetch**|**SQLSetConnectAttr**|  
|**SQLFetchScroll**|**SQLSetConnectOption**|  
|**SQLFreeHandle**|**SQLSetDescField**|  
|**SQLFreeStmt**|**SQLSetDescRec**|  
|**SQLGetData**|**SQLSetPos**|  
|**SQLGetDescField**|**SQLSetScrollOptions**|  
|**SQLGetDescRec**|**SQLSetStmtAttr**|  
|**SQLGetFunctions**|**SQLSetStmtOption**|  
|**SQLGetInfo**|**SQLTransact**|  
|**SQLGetStmtAttr**||
