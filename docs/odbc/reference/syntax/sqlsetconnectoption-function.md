---
description: SQLSetConnectOption 函式
title: SQLSetConnectOption 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebe9166ea52971812e8905399da4ea0e6347361a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499530"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption 函式
**一致性**  
 引進的版本： ODBC 1.0 標準合規性：已淘汰  
  
 **總結**  
 在 ODBC 3.x*中，odbc*2.0 函數 **SQLSetConnectOption** 已被 **SQLSetConnectAttr**取代。 如需詳細資訊，請參閱 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)。  
  
> [!NOTE]
>  如需當 ODBC 2.x 應用程式與 ODBC 3.x*驅動程式搭配*使用時，驅動程式管理員會將此函式對應 *.x*到什麼的詳細資訊，請參閱[對應已淘汰](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)的函式。  
  
## <a name="remarks"></a>備註  
 如果您的應用程式將在64位作業系統上執行，請參閱 [ODBC 64 位資訊](../../../odbc/reference/odbc-64-bit-information.md)。  
  
> [!NOTE]  
>  **SQLSetConnectOption**不支援 ODBC 3.8 中引進的屬性 SQL_ASYNC_DBC_FUNCTION_ENABLE。 在連接控制碼上使用非同步作業的應用程式必須使用 **SQLSetConnectAttr**。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC API 參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
