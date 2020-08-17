---
description: 驅動程式管理員的用途
title: 驅動程式管理員的功能 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], backward compatibility
- compatibility [ODBC], driver manager
- ODBC driver manager [ODBC]
- backward compatibility [ODBC], driver manager
ms.assetid: 57f65c38-d9ee-46c8-9051-128224a582c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 399dec39e18c9e31ce4a93172d0597c333fb40cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386164"
---
# <a name="what-the-driver-manager-does"></a>驅動程式管理員的用途
下表摘要 *說明 odbc 3.X* 驅動程式管理員如何將呼叫對應至 odbc 2.X *和 odbc* *3.x 驅動程式* 。  
  
|函數或<br /><br /> 陳述式屬性|註解|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|指向要搭配 **SQLFetchScroll**使用的書簽。 以下是執行詳細資料：<br /><br /> -當應用程式在 ODBC 2.x*驅動程式*中設定此項時，odbc *3.X 驅動程式*管理員就會快取它。 當應用程式稍後呼叫**SQLFetchScroll**時，它會對指標進行取值，並將此值傳遞至**SQLExtendedFetch**的*FETCHOFFSET*引數中的 ODBC 2.x 驅動*程式。*<br />-當應用程式 *在 odbc 3.x 驅動程式中* 設定此項時 *，odbc 3.X 驅動程式管理員* 會將呼叫傳遞給驅動程式。|  
|SQL_ATTR_ROW_STATUS_PTR|指向以 **SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**和 **SQLSetPos**填滿的資料列狀態陣列。 以下是執行詳細資料：<br /><br /> -當應用程式在 ODBC 2.x*驅動程式*中設定此項時，odbc *3.X 驅動程式*管理員就會快取它的值。 當呼叫**SQLFetchScroll**或**SQLFetch**時，它會在**SQLExtendedFetch**的*RowStatusArray*引數中，將此值傳遞給 ODBC 2.x 驅動*程式。*<br />-當應用程式 *在 odbc 3.x 驅動程式中* 設定此項時 *，odbc 3.X 驅動程式管理員* 會將呼叫傳遞給驅動程式。<br />-在狀態 S6 中，如果應用程式設定 SQL_ATTR_ROW_STATUS_PTR，然後在未先呼叫**SQLFetch**或**SQLFetchScroll**的情況下，使用 SQL_ADD) 或**SQLSetPos**的*作業來呼叫* **SQLBulkOperations** (，就無法立即設定 SQLSTATE HY011 (屬性) 會傳回。|  
|SQL_ATTR_ROWS_FETCHED_PTR|指向緩衝區，其中 **SQLFetch** 和 **SQLFetchScroll** 會傳回所提取的資料列數目。 以下是執行詳細資料：<br /><br /> -當應用程式在 ODBC 2.x*驅動程式*中設定此項時，odbc *3.X 驅動程式*管理員就會快取它的值。 當應用程式呼叫**SQLFetch**或**SQLFetchScroll**時，它會在**SQLExtendedFetch**的*RowCountPtr*引數中，將此值傳遞*至 ODBC 2.x 驅動程式。*<br />-當應用程式 *在 odbc 3.x 驅動程式中* 設定此項時 *，odbc 3.X 驅動程式管理員* 會將呼叫傳遞給驅動程式。|  
|SQL_ATTR_ROW_ARRAY_SIZE|設定資料列集大小。 以下是執行詳細資料：<br /><br /> -當應用程式在 ODBC 2.x 驅動程式中設定此項時 *，odbc 3.X* *驅動程式管理員*會將它對應到 SQL_ROWSET_SIZE 的語句屬性。<br />-當應用程式 *在 odbc 3.x 驅動程式中* 設定此項時 *，odbc 3.X 驅動程式管理員* 會將呼叫傳遞給驅動程式。<br />-當*使用 ODBC 3.x 驅動程式的*應用程式呼叫**SQLSetScrollOptions**時，如果基礎驅動程式不支援**SQLSetScrollOptions**，SQL_ROWSET_SIZE 會設定為*RowsetSize*引數中的值。|  
|SQL_ROWSET_SIZE|設定*當 ODBC 2.x*應用程式呼叫**SQLExtendedFetch**時， **SQLExtendedFetch**所使用的資料列集大小。 以下是執行詳細資料：<br /><br /> -當應用程式設定此項時，不論驅動程式版本為何 *，ODBC 3.X 驅動程式管理員* 都會將呼叫傳遞給驅動程式。<br />-當 *使用 ODBC 2.x 驅動程式的* 應用程式呼叫 **SQLSetScrollOptions**時，SQL_ROWSET_SIZE 會設定為 **RowsetSize** 引數中的值。|  
|**SQLBulkOperations**|執行插入作業，或透過書簽作業來更新、刪除或提取。 以下是執行詳細資料：<br /><br /> -當應用程式以 ODBC 2.x 驅動程式*中的 SQL_ADD*作業呼叫**SQLBULKOPERATIONS**時 *，odbc 3.x* *驅動程式管理員*會將其對應至具有 SQL_ADD*作業的* **SQLSetPos** 。<br />-使用不支援**SQLSetPos**作業 SQL_ADD 的 odbc 2.x 驅動程式時，odbc 3.x 驅動*Operation* *程式管理員*不*會將* **SQLSetPos** SQL_ADD 的作業對應到具有*SQL_ADD 作業的* **SQLBulkOperations** 。 *3.x* 這是因為 **SQLBulkOperations** 無法在狀態 S7 中呼叫，在 ODBC 2.x 中， *它是唯一* 可呼叫 **SQLSetPos** 的狀態。<br />-如果在呼叫**SQLFetchScroll**之前，應用*程式以 ODBC* 2.x 驅動程式 SQL_ADD 呼叫**SQLBulkOperations** ，*則 odbc* *3.x 驅動程式*管理員會傳回錯誤。|  
|**SQLExtendedFetch**|傳回指定的資料列集。 除了剛才注明的限制以外 *，ODBC 3.X 驅動程式管理員* 會將 **SQLExtendedFetch** 的呼叫傳遞至驅動程式，而不論驅動程式版本為何。|  
|**SQLFetch**|傳回下一個資料列集。 以下是執行詳細資料：<br /><br /> -當應用程式呼叫 ODBC 2.x 驅動程式中的**SQLFetch**時 *，odbc 3.X* *驅動程式管理員*會將其對應至**SQLExtendedFetch**。 **SQLExtendedFetch**的*FetchOrientation*引數設定為 SQL_FETCH_NEXT。 驅動程式管理員會針對 *RowStatusArray* 引數使用 SQL_ATTR_ROW_STATUS_PTR 語句屬性的快取值，並針對 *RowCountPtr* 引數使用 SQL_ATTR_ROWS_FETCHED_PTR 語句屬性的快取值。<br />-ODBC 3.x*應用程式*可以將呼叫混合*到 odbc 2.x*驅動程式中的**SQLFetch**和**SQLFETCHSCROLL** ，因為當應用程式在 ODBC 2.X 驅動程式中呼叫它時 *，odbc 3.X*驅動程式管理員會將*2.x* **SQLFetch**對應至**SQLExtendedFetch** 。<br />-如果 ODBC 2.x 驅動程式不支援**SQLExtendedFetch**，則當應用程式在該驅動程式中呼叫**SQLFetch**或**SQLFetchScroll**時 *，odbc* *3.x 驅動程式*管理員不會將其對應至**SQLExtendedFetch** 。 如果應用程式嘗試將 SQL_ATTR_ROW_ARRAY_SIZE 設定為大於1的值，則會傳回未實) 的 SQLSTATE HYC00 (選用功能。<br />-除了剛才注明的限制以外 *，ODBC 3.X 驅動程式管理員* 會將 **SQLFetch** 的呼叫傳遞至驅動程式，而不論驅動程式版本為何。|  
|**SQLFetchScroll**|傳回指定的資料列集。 以下是執行詳細資料：<br /><br /> -當應用程式呼叫 ODBC 2.x 驅動程式中的**SQLFetchScroll**時 *，odbc 3.X* *驅動程式管理員*會將其對應至**SQLExtendedFetch**。 它會針對 *RowStatusArray* 引數使用 SQL_ATTR_ROW_STATUS_PTR 語句屬性的快取值，並針對 *RowCountPtr* 引數使用 SQL_ATTR_ROWS_FETCHED_PTR 語句屬性的快取值。 如果已 SQL_FETCH_BOOKMARK **SQLFetchScroll**中的*FetchOrientation*引數，它會針對*FetchOffset*引數使用 SQL_ATTR_FETCH_BOOKMARK_PTR 語句屬性的快取值，如果**SQLFetchScroll**的*FetchOffset*引數不是0，則會傳回錯誤。<br />-當應用程式在 ODBC 3.x*驅動程式*中呼叫這個時，odbc *3.X 驅動程式*管理員會將呼叫傳遞給驅動程式。|  
|**SQLSetPos**|執行各種定位作業。 不論驅動 *程式版本為何，ODBC 3.X* 驅動程式管理員都會將 **SQLSetPos** 的呼叫傳遞至驅動程式。|  
|**SQLSetScrollOptions**|當驅動程式管理員針對使用不支援**SQLSetScrollOptions***之 ODBC 3.x 驅動程式的*應用程式對應**SQLSetScrollOptions**時，驅動程式管理員會將 SQL_ROWSET_SIZE 語句選項（而非 SQL_ATTR_ROW_ARRAY_SIZE 語句屬性）設定為**SQLSetScrollOption**中的*RowsetSize*引數。 因此，應用程式在呼叫**SQLFetch**或**SQLFetchScroll**時，無法使用**SQLSetScrollOptions**來提取多個資料列。 只有在透過呼叫 **SQLExtendedFetch**來提取多個資料列時，才可以使用它。|
