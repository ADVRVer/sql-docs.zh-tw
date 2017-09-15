---
title: "SQLTransact 函式 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1af98fb53aadf7ea6bb2253041c951481a019027
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqltransact-function"></a>SQLTransact 函式
**一致性**  
 版本引進了： ODBC 1.0 標準相容性： 已被取代  
  
 **摘要**  
 在 ODBC 3。*x*，ODBC 2*.x*函式**SQLTransact**已被取代**SQLEndTran**。 如需詳細資訊，請參閱[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)。  
  
> [!NOTE]  
>  不支援屬性 SQL_ASYNC_DBC_FUNCTION_ENABLE 所導入 ODBC 3.8， **SQLTransact**。 使用連接控制代碼上的非同步作業的應用程式必須使用**SQLEndTran**。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 應用程式開發介面參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
