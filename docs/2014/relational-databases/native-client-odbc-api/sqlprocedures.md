---
title: SQLProcedures |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0001f1d6e45e855b884028a595a2b61263c2e58
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046675"
---
# <a name="sqlprocedures"></a>SQLProcedures
  所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序都會傳回值。 **SQLProcedures** PROCEDURE_TYPE 結果集資料行的報表 SQL_PT_FUNCTION。  
  
 **SQLProcedures**會傳回 SQL_SUCCESS *CatalogName、SchemaName*或*ProcName*參數的值是否存在。 當這些參數中使用了不正確值時， **SQLFetch**會傳回 SQL_NO_DATA。  
  
 **SQLProcedures**可以在靜態伺服器資料指標上執行。 嘗試在可更新的（動態或索引鍵集）資料指標上執行**SQLProcedures**時，將會傳回 SQL_SUCCESS_WITH_INFO，表示資料指標類型已變更。  
  
 **SQLProcedures**會傳回名稱符合*ProcName*且可由目前使用者執行，或是目前使用者已被授與 VIEW DEFINITION 許可權之任何程式的相關資訊。  
  
## <a name="see-also"></a>另請參閱  
 [SQLProcedures 函式](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API 實作詳細資料](odbc-api-implementation-details.md)  
  
  
