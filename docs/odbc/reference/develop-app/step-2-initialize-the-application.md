---
title: "步驟 2： 初始化應用程式 |Microsoft 文件"
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
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4b14b5374cedece38295bac840a72acae5895ca8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="step-2-initialize-the-application"></a>步驟 2： 初始化應用程式
第二個步驟是初始化應用程式，如下圖所示。 完全所完成的作業這裡會隨著應用程式。  
  
 ![初始化 ODBC 應用程式會顯示](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 此時，它會使用**SQLGetInfo**探索驅動程式的功能。 如需詳細資訊，請參閱[考慮要使用的資料庫功能](../../../odbc/reference/develop-app/considering-database-features-to-use.md)。  
  
 所有應用程式必須配置陳述式控制代碼與**SQLAllocHandle**，且使用的許多應用程式設定陳述式屬性，資料指標類型，例如**SQLSetStmtAttr**。 如需詳細資訊，請參閱[配置陳述式控制代碼](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)和[陳述式屬性](../../../odbc/reference/develop-app/statement-attributes.md)。

