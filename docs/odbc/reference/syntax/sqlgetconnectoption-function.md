---
title: SQLGetConnectOption 函式 |Microsoft 文件
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
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 91cf0a45d148a2a14c35626f8ca720c5d57279cc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetconnectoption-function"></a>SQLGetConnectOption 函式
**一致性**  
 版本引進了： ODBC 1.0 標準相容性： 已被取代  
  
 **摘要**  
 在 ODBC 3*.x*，ODBC 2*.x*函式**SQLGetConnectOption**已被取代**SQLGetConnectAttr**。 如需詳細資訊，請參閱[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)。  
  
> [!NOTE]  
>  如需有關什麼驅動程式管理員會對應到此函式時 ODBC 2*.x*應用程式使用 ODBC 3*.x*驅動程式，請參閱[對應已被取代的函式](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)中附錄 g： 驅動程式的指導方針回溯相容性。  
  
> [!NOTE]  
>  不支援屬性 SQL_ASYNC_DBC_FUNCTION_ENABLE ODBC 3.8 中導入**SQLGetConnectOption**。 使用連接控制代碼上的非同步作業的應用程式必須使用**SQLGetConnectAttr**。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 應用程式開發介面參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
