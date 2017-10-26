---
title: "SQLSetStmtOption （桌面資料庫驅動程式） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d1f51805413056a06c6cee769920e1ad878abe5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption （桌面資料庫驅動程式）
|*fOption*|註解|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|不支援非同步處理。 SQL_ASYNC_ENABLE fOption 會傳回 SQLSTATE S1C00 （驅動程式不支援）。|  
|SQL_KEYSET_SIZE|唯一有效的索引鍵集大小為 0，因為混合而且不支援動態資料指標。 如果此值設定為其他任何數字，會變更為 0，呼叫會傳回 SQL_SUCCESS_WITH_INFO 和 SQLSTATE 01S02 （選項值已變更）。|  
|SQL_MAX_ROWS|唯一有效的資料列集大小為 0，因為桌面資料庫驅動程式不支援限制傳回的資料列數目。 如果此值設定為其他任何數字，會變更為 0，呼叫會傳回 SQL_SUCCESS_WITH_INFO 和 SQLSTATE 01S02 （選項值已變更）。|  
|SQL_QUERY_TIMEOUT|不支援。|  
|SQL_ROW_NUMBER|不支援。|  
|SQL_SIMULATE_CURSOR|不支援。|

