---
title: 卸除 SQL Server 索引 |Microsoft 文件
description: 卸除 sql server 索引，使用適用於 SQL Server 的 OLE DB 驅動程式
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
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a790633c129fe1cfb3da9a21a9e4fd9fae3513cd
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690151"
---
# <a name="dropping-a-sql-server-index"></a>卸除 SQL Server 索引
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server OLE DB 驅動程式會公開 **:: Dropindex<** 函式。 這可讓取用者移除從索引[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料表。  
  
 SQL Server OLE DB 驅動程式會公開某些[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]PRIMARY KEY 和 UNIQUE 條件約束當做索引。 資料表擁有者、 資料庫擁有者，以及某些系統管理角色成員可以修改[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料表，卸除條件約束。 根據預設，只有資料表擁有者可以卸除現有的索引。 因此， **DropIndex**不是只在應用程式使用者的存取權限，但也在所指出之索引的類型上相依的成功或失敗。  
  
 取用者指定的資料表名稱中的 Unicode 字元字串*pwszName*隸屬*uName*聯集*Createtable*參數。 *EKind*隸屬*Createtable*必須是 DBKIND_NAME。  
  
 取用者索引名稱指定之 Unicode 字元字串*pwszName*隸屬*uName*聯集*pIndexID*參數。 *EKind*隸屬*pIndexID*必須是 DBKIND_NAME。 SQL Server OLE DB 驅動程式不支援資料表上卸除所有索引的 OLE DB 功能時*pIndexID*為 null。 如果*pIndexID*是會傳回 null，E_INVALIDARG。  
  
## <a name="see-also"></a>另請參閱  
 [資料表和索引](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
