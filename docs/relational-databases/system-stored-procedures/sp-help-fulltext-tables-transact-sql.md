---
title: sp_help_fulltext_tables (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_tables
- sp_help_fulltext_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_tables
ms.assetid: 86e24a5f-a869-43f6-b83e-c52b7b01b5ff
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 855a9a5bde98703909a01b44721c5972c1eefff2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpfulltexttables-transact-sql"></a>sp_help_fulltext_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回登錄了全文檢索索引的資料表清單。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用**sys.fulltext_indexes**目錄檢視。 如需詳細資訊，請參閱[sys.fulltext_indexes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_fulltext_tables [ [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@fulltext_catalog_name=**] **'***fulltext_catalog_name***'**  
 這是全文檢索目錄的名稱。 *fulltext_catalog_name*是**sysname**，預設值是 NULL。 如果*fulltext_catalog_name*省略或為 NULL，就會傳回所有與資料庫相關聯的全文檢索索引的資料表。 如果*fulltext_catalog_name*指定，但*table_name*省略或為 NULL，擷取這個目錄相關聯的每個全文檢索索引資料表的全文檢索索引資訊。 如果兩個*fulltext_catalog_name*和*table_name*指定，會傳回一個資料列，如果*table_name*聯*fulltext_catalog_name*;否則，就會引發錯誤。  
  
 [ **@table_name=**] **'***table_name***'**  
 這是所要求之全文檢索中繼資料一或兩部分的資料表名稱。 *table_name*是**nvarchar （517)**，預設值是 NULL。 如果只有*table_name*指定時，只適用於列*table_name*傳回。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|資料表擁有者。 這是建立資料表之資料庫使用者的名稱。|  
|**TABLE_NAME**|**sysname**|資料表名稱。|  
|**FULLTEXT_KEY_INDEX_NAME**|**sysname**|在指定為唯一索引鍵資料行的資料行上賦予 UNIQUE 條件約束的索引。|  
|**FULLTEXT_KEY_COLID**|**int**|FULLTEXT_KEY_NAME 所識別之唯一索引的資料行識別碼。|  
|**FULLTEXT_INDEX_ACTIVE**|**int**|指定此資料表中標示為全文檢索索引的資料行是否適合查詢：<br /><br /> 0 = 非使用中<br /><br /> 1 = 使用中|  
|**FULLTEXT_CATALOG_NAME**|**sysname**|全文檢索索引資料所在的全文檢索目錄。|  
  
## <a name="permissions"></a>Permissions  
 預設執行權限的成員**公用**角色。  
  
## <a name="examples"></a>範例  
 下列範例會傳回與 `Cat_Desc` 全文檢索目錄相關聯之全文檢索索引資料表的名稱。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help_fulltext_tables 'Cat_Desc';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables_cursor &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
