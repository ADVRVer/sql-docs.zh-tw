---
description: sp_tables_ex (Transact-SQL)
title: sp_tables_ex (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables_ex
- sp_tables_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables_ex
ms.assetid: 33755c33-7e1e-4ef7-af14-a9cebb1e2ed4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c195e3fa5e932bd1eb844ca5231d67747bc67486
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480978"
---
# <a name="sp_tables_ex-transact-sql"></a>sp_tables_ex (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回指定之連結伺服器中資料表的資料表相關資訊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_tables_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]  
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @table_type = ] 'table_type' ]   
     [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @table_server = ] 'table_server'` 這是傳回資料表資訊之連結伺服器的名稱。 *table_server* 是 **sysname**，沒有預設值。  
  
``[ , [ @table_name = ] 'table_name']`` 這是傳回資料類型資訊的資料表名稱。 *table_name*是 **sysname**，預設值是 Null。  
  
`[ @table_schema = ] 'table_schema']` 這是資料表架構。 *table_schema*是 **sysname**，預設值是 Null。  
  
`[ @table_catalog = ] 'table_catalog'` 這是指定之 *table_name* 所在的資料庫名稱。 *table_catalog* 是 **sysname**，預設值是 Null。  
  
`[ @table_type = ] 'table_type'` 這是要傳回的資料表類型。 *table_type* 是 **sysname**，預設值是 Null，且可以有下列其中一個值。  
  
|值|描述|  
|-----------|-----------------|  
|**別名**|別名的名稱。|  
|**GLOBAL TEMPORARY**|全系統所能使用之暫存資料表的名稱。|  
|**LOCAL TEMPORARY**|只供目前作業使用之暫存資料表的名稱。|  
|**同義字**|同義字的名稱。|  
|**系統資料表**|系統資料表的名稱。|  
|**系統檢視**|系統檢視表的名稱。|  
|**表**|使用者資料表的名稱。|  
|**視圖**|檢視表的名稱。|  
  
`[ @fUsePattern = ] 'fUsePattern'` 判斷是否將 **_**、 **%** 、 **[** 和 **]** 字元視為萬用字元。 有效值是 0 (關閉模式比對) 和 1 (開啟模式比對)。 *fUsePattern* 是 **bit**，預設值是1。  
  
## <a name="return-code-values"></a>傳回碼值  
 None  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|資料表限定詞名稱。 各種 DBMS 產品都支援資料表 (辨識_符號_的三部分命名 **。**_擁有_者 **。**) _名稱_。 在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，這個資料行代表資料庫名稱。 在某些其他產品中，它代表資料表之資料庫環境的伺服器名稱。 這個欄位可以是 NULL。|  
|**TABLE_SCHEM**|**sysname**|資料表擁有者名稱。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，這個資料行代表建立資料表的資料庫使用者名稱。 這個欄位一律會傳回值。|  
|**TABLE_NAME**|**sysname**|資料表名稱。 這個欄位一律會傳回值。|  
|**TABLE_TYPE**|**varchar(32)**|資料表、系統資料表或檢視表。|  
|**備註**|**Varchar (254) **|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會傳回這個資料行的值。|  
  
## <a name="remarks"></a>備註  
 **sp_tables_ex**是藉由查詢對應至*table_server*之 OLE DB 提供者之**IDBSchemaRowset**介面的資料表資料列集來執行。 *Table_name*、 *table_schema*、 *table_catalog*和資料行參數會傳遞至這個介面，以限制傳回的資料*列*。  
  
 如果指定之連結伺服器的 OLE DB 提供者不支援**IDBSchemaRowset**介面的資料表資料列集， **sp_tables_ex**會傳回空的結果集。  
  
## <a name="permissions"></a>權限  
 需要結構描述的 SELECT 權限。  
  
## <a name="examples"></a>範例  
 下列範例會傳回 `HumanResources` 連結伺服器 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中的 `LONDON2` 結構描述所包含之資料表的相關資訊。  
  
```  
EXEC sp_tables_ex @table_server = 'LONDON2',   
@table_catalog = 'AdventureWorks2012',   
@table_schema = 'HumanResources',   
@table_type = 'TABLE';  
```  
  
## <a name="see-also"></a>另請參閱  
 [分散式查詢預存程式 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_columns_ex &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_table_privileges &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
