---
title: 從 SQL Server 資料表移除資料行 (OLD DB 驅動程式)
description: OLE DB Driver for SQL Server 會公開 ITableDefinition::DropColumn 函式，讓取用者能夠從 SQL Server 資料表中移除資料行。
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0672669e6d724e7dfcb5338c76694473f078da10
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859467"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>從 SQL Server 資料表中移除資料行
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server 會公開 **ITableDefinition::DropColumn** 函式。 如此可讓取用者從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表中移除資料行。  
  
 取用者會在 *pTableID* 參數中，將資料表名稱指定為 *uName* 聯集 *pwszName* 成員中的 Unicode 字元字串。 *pTableID* 的 *eKind* 成員必須是 DBKIND_NAME。  
  
 此取用者會在 *pColumnID* 參數內指示 *uName* 聯集之 *pwszName* 成員內的資料行名稱。 資料行名稱是一個 Unicode 字元字串。 *pColumnID* 的 *eKind* 成員必須是 DBKIND_NAME。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料表和索引](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
