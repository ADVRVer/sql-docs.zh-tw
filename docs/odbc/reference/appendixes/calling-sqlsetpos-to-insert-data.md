---
title: "呼叫 SQLSetPos 將資料插入 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e9d768ea5c16b199dc316726cb425b75d409bf1f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="calling-sqlsetpos-to-insert-data"></a>呼叫 SQLSetPos 插入資料
當 ODBC 2。*x*應用程式使用 ODBC 3*.x*驅動程式呼叫**SQLSetPos**與*作業*SQL_ADD，驅動程式管理員的引數未對應至這個呼叫**SQLBulkOperations**。 如果 ODBC 3*.x*驅動程式應該使用的應用程式，會呼叫**SQLSetPos** SQL_ADD，與驅動程式應該支援這項操作。  
  
 行為中的一項主要差異時**SQLSetPos**呼叫處於 S6 呼叫時，就會發生 SQL_ADD。 在 ODBC 2。*x*，驅動程式傳回 S1010 時**SQLSetPos**處於 S6 SQL_ADD 以叫用 (已被資料指標位於與之後**SQLFetch**)。 在 ODBC 3*.x*， **SQLBulkOperations**與*作業*SQL_ADD 可以處於 S6 呼叫。 行為中的第二個主要差異在於**SQLBulkOperations**與*作業*SQL_ADD 可以是在狀態 S5 呼叫，而**SQLSetPos**與**作業**的 SQL_ADD 無法。 陳述式轉換可以發生在相同的呼叫，在 ODBC 3*.x*，請參閱[附錄 b: ODBC 狀態轉換表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)。

