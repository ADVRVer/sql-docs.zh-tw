---
title: SQLProcedures |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 14ff76504c9a36657be60ba4855cf252474071d7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302356"
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序都會傳回值。 **SQLProcedures** PROCEDURE_TYPE 結果集資料行的報表 SQL_PT_FUNCTION。  
  
 **SQLProcedures**會傳回 SQL_SUCCESS *CatalogName、SchemaName*或*ProcName*參數的值是否存在。 當這些參數中使用了不正確值時， **SQLFetch**會傳回 SQL_NO_DATA。  
  
 **SQLProcedures**可以在靜態伺服器資料指標上執行。 嘗試在可更新的（動態或索引鍵集）資料指標上執行**SQLProcedures**時，將會傳回 SQL_SUCCESS_WITH_INFO，表示資料指標類型已變更。  
  
 **SQLProcedures**會傳回名稱符合*ProcName*且可由目前使用者執行，或是目前使用者已被授與 VIEW DEFINITION 許可權之任何程式的相關資訊。  
  
## <a name="see-also"></a>另請參閱  
 [SQLProcedures 函式](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API 實作詳細資料](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
