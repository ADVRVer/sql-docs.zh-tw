---
title: SQLTables |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3a7ccecb3923dc46ebf8442e3c006ee88564749b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130977"
---
# <a name="sqltables"></a>SQLTables
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQLTables 可以在靜態伺服器資料指標上執行。 嘗試在可更新的 （動態或索引鍵集） 資料指標上執行 SQLTables 會傳回 SQL_SUCCESS_WITH_INFO，指出資料指標類型已變更。  
  
 SQLTables 報告所有的資料表資料庫的時機*CatalogName*參數為 SQL_ALL_CATALOGS，而且所有其他參數包含預設值 （NULL 指標）。  
  
 若要報告可用的目錄、 結構描述和資料表類型，SQLTables 會會特別使用空字串 （長度為零的位元組指標）。 空字串不是預設值 (NULL 指標)。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式支援的報告資訊的連結伺服器上的資料表所接受的兩部分名稱*CatalogName*參數：*Linked_Server_Name.Catalog_Name*。  
  
 SQLTables 傳回資料表的名稱相符的任何相關資訊*TableName*和目前的使用者所擁有。  
  
## <a name="sqltables-and-table-valued-parameters"></a>SQLTables 和資料表值參數  
 當 SQL_SOPT_SS_NAME_SCOPE 陳述式屬性具有值為 SQL_SS_NAME_SCOPE_TABLE_TYPE，而非 SQL_SS_NAME_SCOPE_TABLE 的預設值時，SQLTables 就會傳回資料表類型的相關資訊。 SQLTables 所傳回之結果集的資料行 4 中的資料表類型傳回的 TABLE_TYPE 值是資料表類型。 如需有關 SQL_SOPT_SS_NAME_SCOPE 的詳細資訊，請參閱 < [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)。  
  
 資料表、檢視與同義字共用與資料表類型所使用之命名空間不同的一般命名空間。 雖然不可能擁有具有相同名稱的資料表和檢視，但是在相同的目錄和結構描述中，可能擁有具有相同名稱的資料表和資料表類型。  
  
 如需有關資料表值參數的詳細資訊，請參閱 < [Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。  
  
## <a name="example"></a>範例  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQLTables 函數](https://go.microsoft.com/fwlink/?LinkId=59374)   
 [ODBC API 實作詳細資料](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
