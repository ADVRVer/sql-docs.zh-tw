---
title: "卸除 SQL Server 索引 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-tables-indexes
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6ea14c79c046a63d51dd5f9587d36150bd95f494
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dropping-a-sql-server-index"></a>卸除 SQL Server 索引
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會公開**:: Dropindex<**函式。 這可讓取用者移除從索引[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料表。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會公開某些[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PRIMARY KEY 和 UNIQUE 條件約束當做索引。 資料表擁有者、 資料庫擁有者，以及某些系統管理角色成員可以修改[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料表，卸除條件約束。 根據預設，只有資料表擁有者可以卸除現有的索引。 因此， **DropIndex**不是只在應用程式使用者的存取權限，但也在所指出之索引的類型上相依的成功或失敗。  
  
 取用者指定的資料表名稱中的 Unicode 字元字串*pwszName*隸屬*uName*聯集*Createtable*參數。 *EKind*隸屬*Createtable*必須是 DBKIND_NAME。  
  
 取用者索引名稱指定之 Unicode 字元字串*pwszName*隸屬*uName*聯集*pIndexID*參數。 *EKind*隸屬*pIndexID*必須是 DBKIND_NAME。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者不支援資料表上卸除所有索引的 OLE DB 功能時*pIndexID*為 null。 如果*pIndexID*是會傳回 null，E_INVALIDARG。  
  
## <a name="see-also"></a>請參閱  
 [資料表和索引](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
