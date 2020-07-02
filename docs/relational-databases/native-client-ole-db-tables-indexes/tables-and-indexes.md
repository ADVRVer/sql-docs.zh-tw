---
title: 資料表與索引 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cc28a9df9b5f065314a8cd2f96a54457fa3c4b14
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85658520"
---
# <a name="tables-and-indexes"></a>資料表和索引
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**IIndexDefinition**和**ITableDefinition**介面，讓取用者建立、改變和卸載 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表和索引。 有效的資料表和索引定義是取決於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本。  
  
 建立或卸除資料表和索引的能力，取決於取用者應用程式使用者的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取權限。 卸除資料表可藉由宣告式參考完整性條件約束或其他因數的存在，而受進一步的條件約束。  
  
 大部分的應用程式目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 都使用 sql-dmo，而不是這些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者介面。 SQL-DMO 是 OLE Automation 物件的集合，可支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所有的管理功能。 以多個 OLE DB 提供者為目標的應用程式會使用這些受多個 OLE DB 提供者支援的一般 OLE DB 介面。  
  
 在提供者特定屬性集 DBPROPSET_SQLSERVERCOLUMN 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會定義下列屬性。  
  
|屬性識別碼|描述|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|輸入：VT_BSTR<br /><br /> R/W：寫入<br /><br /> 預設值：Null<br /><br /> 描述：此屬性只能用於 **ITableDefinition**。 在建立 [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) 時會使用這個屬性指定的字串<br /><br /> 陳述式。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [建立 SQL Server 資料表](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [將資料行新增至 SQL Server 資料表](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [從 SQL Server 資料表中移除資料行](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [卸除 SQL Server 資料表](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [建立 SQL Server 索引](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [卸除 SQL Server 索引](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
