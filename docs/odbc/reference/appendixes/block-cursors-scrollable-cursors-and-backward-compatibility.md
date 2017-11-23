---
title: "區塊資料指標，可捲動的資料指標和回溯相容性 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: d9d271f6-d2d9-49b9-a365-4909ca06caae
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f653ed286aa421f9ac7fe8ae7c29e5eb8cb3348
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility"></a>區塊資料指標，可捲動的資料指標和回溯相容性
兩者的存在**SQLFetchScroll**和**SQLExtendedFetch**代表分割 ODBC 之間應用程式設計介面 (API)，這是集合的函式中的第一個清除應用程式呼叫和服務提供者介面 (SPI)，這是集合的函式的驅動程式實作。 這種分割是必要的讓 ODBC 3。*x*，它會使用**SQLFetchScroll**，bealigned 標準，也必須相容於 ODBC 2。*x*，它會使用**SQLExtendedFetch**。  
  
 ODBC 3*.x*應用程式開發介面，這是一組、 函式應用程式會呼叫包含**SQLFetchScroll**和相關的陳述式屬性。 ODBC 3*.x* SPI，這是集合的函式的驅動程式實作，包括**SQLFetchScroll**， **SQLExtendedFetch**，以及相關的陳述式屬性。 ODBC 不會正式強制此應用程式開發介面和 SPI 之間分割，所以針對 ODBC 3*.x*應用程式呼叫**SQLExtendedFetch**和相關的陳述式屬性。 不過，沒有理由 ODBC 3*.x*應用程式，若要這樣做。 如需應用程式開發介面和 Spi 的詳細資訊，請參閱簡介[ODBC 架構](../../../odbc/reference/odbc-architecture.md)。  
  
 如需哪些函式和陳述式屬性 ODBC 3。*x*應用程式應該使用與區塊和可捲動資料指標，請參閱[區塊資料指標，可捲動資料指標，ODBC 3.x 應用程式的回溯相容性](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)。  
  
 此章節包含下列主題。  
  
-   [驅動程式管理員的作用](../../../odbc/reference/appendixes/what-the-driver-manager-does.md)  
  
-   [驅動程式的用途](../../../odbc/reference/appendixes/what-the-driver-does.md)
