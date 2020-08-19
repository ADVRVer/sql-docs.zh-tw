---
description: SQLGetPoolID 函式
title: SQLGetPoolID 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2cd38008b90a1299bdd78c4a56d7394f85876ab0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421252"
---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID 函式
**一致性**  
 引進的版本： ODBC 3.81 標準合規性： ODBC  
  
 **總結**  
 **SQLGetPoolID** 會捕獲集區識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>引數  
 *hDbcInfoToken*  
 輸出包含所有連接資訊的權杖控制碼。  
  
 *pPoolID*  
 出集區識別碼，用來識別一組可以交換使用的連接 (可能需要額外的重設) 。  
  
## <a name="returns"></a>傳回  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR 或 SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLGetPoolID**傳回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO 時，驅動程式管理員會使用 SQL_HANDLE_DBC_INFO_TOKEN 的**HandleType**和*hDbcInfoToken*的**控制碼**。  
  
## <a name="remarks"></a>備註  
 **SQLGetPoolID** 是用來取得集區識別碼，指定了一組從 **SQLSetConnectAttrForDbcInfo**、 **SQLSetDriverConnectInfo**和 **SQLSetConnectInfo**)  (的連接資訊。 此集區識別碼是用來識別一組可以交換使用的連接， (可能需要額外的重設) 。 集區識別碼將用來識別該連接群組的連接集區。  
  
 每當驅動程式傳回 SQL_ERROR 或 SQL_INVALID_HANDLE 時，驅動程式管理員就會將錯誤傳回至 [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) 或 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)) 中的應用程式 (。  
  
 只要驅動程式傳回 SQL_SUCCESS_WITH_INFO，驅動程式管理員就會從 *hDbcInfoToken*取得診斷資訊，並將 SQL_SUCCESS_WITH_INFO 傳回給應用程式的 [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) 和 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)。  
  
 應用程式不應該直接呼叫此函數。 支援驅動程式感知連接共用的 ODBC 驅動程式必須執行此函數。  
  
 包含用於 ODBC 驅動程式開發的 sqlspi .h。  
  
## <a name="see-also"></a>另請參閱  
 [開發 ODBC 驅動程式](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [驅動程式感知連接共用](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [在 ODBC 驅動程式中開發連接集區覺察](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
