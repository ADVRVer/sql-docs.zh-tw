---
title: 從 SQL Server 資料表中移除資料行 |Microsoft Docs
description: 從使用 OLE DB Driver for SQL Server 的 SQL Server 資料表中移除資料行
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4ff9e5872f74b86f6ac5dafb34bd8cfc4d322b74
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43033327"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>從 SQL Server 資料表中移除資料行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server 會公開**itabledefinition:: Dropcolumn**函式。 如此可讓取用者從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表中移除資料行。  
  
 取用者會在 *pTableID* 參數中，將資料表名稱指定為 *uName* 聯集之 *pwszName* 成員中的 Unicode 字元字串。 *pTableID* 的 *eKind* 成員必須是 DBKIND_NAME。  
  
 取用者表示中的資料行名稱*pwszName*隸屬*uName*聯集*Ekind*參數。 資料行名稱是一個 Unicode 字元字串。 *pTableID* 的 *eKind* 成員必須是 DBKIND_NAME。  
  
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
  
  
