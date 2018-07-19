---
title: SQLPrimaryKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d141beac8e581764ff5466dce343ad6335747a4e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407138"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一個資料表可能有的資料行或資料行可以做為唯一資料列識別碼，建立不含主索引鍵條件約束的資料表傳回空的結果設為 SQLPrimaryKeys。 ODBC 函數[SQLSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md)報告資料列識別碼候選資料表沒有主索引鍵。  
  
 SQLPrimaryKeys 或是否有值存在都會傳回 SQL_SUCCESS *CatalogName*， *SchemaName*，或*TableName*參數。 SQLFetch 這些參數中使用無效的值時，傳回 sql_no_data 為止。  
  
 SQLPrimaryKeys 可以在靜態伺服器資料指標上執行。 嘗試在可更新的 （動態或索引鍵集） 資料指標上執行 SQLPrimaryKeys 會傳回 SQL_SUCCESS_WITH_INFO，指出資料指標類型已變更。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式支援的報告資訊的連結伺服器上的資料表所接受的兩部分名稱*CatalogName*參數： *Linked_Server_Name.Catalog_Name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys 和資料表值參數  
 如果陳述式屬性 SQL_SOPT_SS_NAME_SCOPE 的值為 SQL_SS_NAME_SCOPE_TABLE_TYPE，而非 SQL_SS_NAME_SCOPE_TABLE 的預設值，SQLPrimaryKeys 會傳回資料表類型的主索引鍵資料行的相關資訊。 如需有關 SQL_SOPT_SS_NAME_SCOPE 的詳細資訊，請參閱 < [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)。  
  
 如需有關資料表值參數的詳細資訊，請參閱 < [Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLPrimaryKeys 函數](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API 實作詳細資料](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
