---
title: 區塊和可捲動資料指標的相容性 ODBC 3.x |Microsoft 文件
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
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- SQLExtendedFetch function [ODBC], block cursors
- cursors [ODBC], compatibility issues
- SQLFetchScroll function [ODBC], block cursors
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 670c81a8af1ec229a22ad9a8d52c8bab7164fdd1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>區塊資料指標，可捲動資料指標，ODBC 3.x 應用程式的回溯相容性
兩者的存在**SQLFetchScroll**和**SQLExtendedFetch**代表分割 ODBC 之間應用程式設計介面 (API)，這是集合的函式中的第一個清除應用程式呼叫和服務提供者介面 (SPI)，這是集合的函式的驅動程式實作。 這種分割，才能在 ODBC 3 需求之間取得平衡。*x*，它會使用**SQLFetchScroll**，以與標準，並使其相容於 ODBC 2。*x*，它會使用**SQLExtendedFetch**。  
  
 ODBC 3 *.x*應用程式開發介面，這是一組、 函式應用程式會呼叫包含**SQLFetchScroll**和相關的陳述式屬性。 ODBC 3 *.x* SPI，這是集合的函式的驅動程式實作，包括**SQLFetchScroll**， **SQLExtendedFetch**，以及相關的陳述式屬性。 ODBC 不會正式強制此應用程式開發介面和 SPI 之間分割，所以針對 ODBC 3 *.x*應用程式呼叫**SQLExtendedFetch**和相關的陳述式屬性。 不過，沒有理由 ODBC 3 *.x*應用程式，若要這樣做。 如需應用程式開發介面和 Spi 的詳細資訊，請參閱簡介[ODBC 架構](../../../odbc/reference/odbc-architecture.md)。  
  
 如需 ODBC 3。*x*驅動程式管理員將呼叫對應至 ODBC 2。*x*和 ODBC 3。*x*驅動程式，以及哪些函式和陳述式屬性 ODBC 3。*x*驅動程式應該為區塊和可捲動資料指標實作，請參閱[驅動程式的用途](../../../odbc/reference/appendixes/what-the-driver-does.md)中附錄 g： 驅動程式的指導方針回溯相容性。  
  
 下表摘要說明哪些函式和陳述式屬性 ODBC 3。*x*應用程式應該使用區塊與可捲動資料指標。 它也會列出 ODBC 2 之間的變更。*x*和 ODBC 3。*x*此區域中的 ODBC 3。*x*應用程式應該注意可與 ODBC 2 相容。*x*驅動程式。  
  
|函式或<br /><br /> 陳述式屬性|註解|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|指向要使用的書籤**SQLFetchScroll**。<br /><br /> 當應用程式設定在 ODBC 2。*x*驅動程式，這必須指向固定長度的書籤。|  
|SQL_ATTR_ROW_STATUS_PTR 設定|指向資料列狀態陣列填入**SQLFetch**， **SQLFetchScroll**， **SQLBulkOperations**，和**SQLSetPos**。<br /><br /> 如果應用程式會設定此 ODBC 2。*x*驅動程式和呼叫**SQLBulkOperation**與*作業*的呼叫之前 SQL_ADD **SQLFetchScroll**， **SQLFetch**，或**SQLExtendedFetch**，SQLSTATE HY011 （屬性現在無法設定） 會傳回。<br /><br /> 當應用程式呼叫**SQLFetch** ODBC 2。*x*驅動程式， **SQLFetch**對應至**SQLExtendedFetch**並因此傳回值，這個陣列中。|  
|SQL_ATTR_ROWS_FETCHED_PTR|指向的緩衝區**SQLFetch**和**SQLFetchScroll**傳回提取的資料列數目。<br /><br /> 當應用程式呼叫**SQLFetch** ODBC 2。*x*驅動程式， **SQLFetch**對應至**SQLExtendedFetch**並因此傳回值，這個緩衝區中。|  
|SQL_ATTR_ROW_ARRAY_SIZE|設定資料列集大小。<br /><br /> 如果應用程式呼叫**SQLBulkOperations**與*作業*的 ODBC 2 SQL_ADD。*x* SQL_ROWSET_SIZE 驅動程式將用於呼叫，而不是使用 SQL_ATTR_ROW_ARRAY_SIZE，因為在呼叫對應至**SQLSetPos**與*作業*SQL_ADD，使用的SQL_ROWSET_SIZE。<br /><br /> 呼叫**SQLSetPos**與*作業*的 SQL_ADD 或**SQLExtendedFetch** ODBC 2 中。*x*驅動程式會使用 SQL_ROWSET_SIZE。<br /><br /> 呼叫**SQLFetch**或**SQLFetchScroll** ODBC 2 中。*x*驅動程式會使用 SQL_ATTR_ROW_ARRAY_SIZE。|  
|**SQLBulkOperations**|執行 insert 和書籤的作業。 當**SQLBulkOperations**與*作業*SQL_ADD 的呼叫中的 ODBC 2。*x*驅動程式，它會對應到**SQLSetPos**與*作業*SQL_ADD。 以下是實作詳細資料：<br /><br /> -時使用的 ODBC 2。*x*驅動程式，應用程式必須使用只以隱含方式配置的 ARD 聯*StatementHandle*; 它無法在配置另一個 ARD 加入資料列，因為明確描述項作業不支援 ODBC 2。*x*驅動程式。 應用程式必須使用**SQLBindCol**未繫結至 ARD **SQLSetDescField**或**SQLSetDescRec**。<br />-當呼叫 ODBC 3。*x*驅動程式，應用程式可以呼叫**SQLBulkOperations**與*作業*的呼叫之前 SQL_ADD **SQLFetch**或**SQLFetchScroll**。 當呼叫 ODBC 2。*x*驅動程式，應用程式必須呼叫**SQLFetchScroll**之前先呼叫**SQLBulkOperations** SQL_ADD 作業使用。|  
|**SQLFetch**|傳回下一個資料列集。 以下是實作詳細資料：<br /><br /> -當應用程式呼叫**SQLFetch** ODBC 2。*x*驅動程式，它會對應到**SQLExtendedFetch**。<br />-當應用程式呼叫**SQLFetch**在 ODBC 3。*x*驅動程式，它會傳回使用 SQL_ATTR_ROW_ARRAY_SIZE 陳述式屬性指定的資料列數目。|  
|**SQLFetchScroll**|傳回指定的資料列集。 以下是實作詳細資料：<br /><br /> -當應用程式呼叫**SQLFetchScroll** ODBC 2。*x*驅動程式，它會傳回 SQLSTATE 01S01 （資料列中的錯誤） 之前套用至單一資料列的每個錯誤。 這只是因為會 ODBC 3 *.x*驅動程式管理員會將對應為**SQLExtendedFetch**和**SQLExtendedFetch**會傳回此 SQLSTATE。 當應用程式呼叫**SQLFetchScroll**在 ODBC 3。*x*驅動程式，它不會傳回 SQLSTATE 01S01 （資料列中的錯誤）。<br />-當應用程式呼叫**SQLFetchScroll** ODBC 2。*x*驅動程式搭配*Sqlfetchscroll*設定為要使用 SQL_FETCH_BOOKMARK， *FetchOffset*引數必須設定為 0。 SQLSTATE HYC00 如果位移為基礎的書籤提取會嘗試使用 ODBC 2，則會傳回 （未實作的選擇性功能）。*x*驅動程式。|  
  
> [!NOTE]  
>  ODBC 3。*x*應用程式不應該使用**SQLExtendedFetch**或 SQL_ROWSET_SIZE 陳述式屬性。 相反地，它們應該使用**SQLFetchScroll**和 SQL_ATTR_ROW_ARRAY_SIZE 陳述式屬性。 ODBC 3。*x*應用程式不應該使用**SQLSetPos**與*作業*的 SQL_ADD 但是應該使用**SQLBulkOperations**與*作業*SQL_ADD。
