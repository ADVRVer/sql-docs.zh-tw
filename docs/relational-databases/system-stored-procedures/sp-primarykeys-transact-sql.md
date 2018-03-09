---
title: "sp_primarykeys (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_primarykeys_TSQL
- sp_primarykeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_primarykeys
ms.assetid: 0f76dd31-5b7b-4209-9e2e-b9ed5cac164d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d33444d2c868896717c3fcc9224838233b07c01
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="spprimarykeys-transact-sql"></a>sp_primarykeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回指定的遠端資料表之主索引鍵資料行，每個索引鍵資料行一個資料列。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_primarykeys [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@table_server =** ] **'***table_server'*  
 這是傳回主索引鍵資訊的連結伺服器名稱。 *table_server*是**sysname**，沒有預設值。  
  
 [  **@table_name =** ] **'***table_name***'**  
 這是提供主索引鍵資訊的資料表名稱。 *table_name*是**sysname**，預設值是 NULL。  
  
 [  **@table_schema =** ] **'***table_schema***'**  
 這是資料表結構描述。 *table_schema*是**sysname**，預設值是 NULL。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境中，這相當於資料表擁有者。  
  
 [  **@table_catalog =** ] **'***table_catalog 排列***'**  
 所在的目錄名稱指定*table_name*所在。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境中，這相當於資料庫名稱。 *table_catalog 排列*是**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 無  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|資料表目錄。|  
|**再依據 TABLE_SCHEM 排列**|**sysname**|資料表結構描述。|  
|**TABLE_NAME**|**sysname**|資料表的名稱。|  
|**COLUMN_NAME**|**sysname**|資料行的名稱。|  
|**KEY_SEQ 來排序**|**int**|資料行在多重資料行主索引鍵中的序號。|  
|**PK_NAME**|**sysname**|主索引鍵識別碼。 如果不適用於資料來源，便傳回 NULL。|  
  
## <a name="remarks"></a>備註  
 **sp_primarykeys**執行查詢的 PRIMARY_KEYS 資料列集**IDBSchemaRowset**相對應的 OLE DB 提供者介面*table_server*。 *Table_name*， *table_schema*， *table_catalog 排列*，和*資料行*參數傳遞給這個介面來限制的資料列傳回。  
  
 **sp_primarykeys**傳回空的結果集，如果指定連結伺服器的 OLE DB 提供者不支援的 PRIMARY_KEYS 資料列集**IDBSchemaRowset**介面。  
  
## <a name="permissions"></a>Permissions  
 需要結構描述的 SELECT 權限。  
  
## <a name="examples"></a>範例  
 下列範例會從 `LONDON1` 伺服器，傳回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中 `HumanResources.JobCandidate` 資料表的主索引鍵資料行。  
  
```  
EXEC sp_primarykeys @table_server = N'LONDON1',   
   @table_name = N'JobCandidate',  
   @table_catalog = N'AdventureWorks2012',   
   @table_schema = N'HumanResources';  
```  
  
## <a name="see-also"></a>請參閱  
 [分散式的查詢預存程序 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [< sp_indexes &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
