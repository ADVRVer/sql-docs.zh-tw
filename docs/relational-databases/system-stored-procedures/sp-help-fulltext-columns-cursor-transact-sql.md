---
title: "sp_help_fulltext_columns_cursor (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_columns_cursor
- sp_help_fulltext_columns_cursor_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_fulltext_columns_cursor
ms.assetid: 26054e76-53b7-4004-8d48-92ba3435e9d7
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eebd461b11ccd375968ada1dd6a8d7f6cb6dbcf2
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpfulltextcolumnscursor-transact-sql"></a>sp_help_fulltext_columns_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  利用資料指標來傳回指定給全文檢索索引的資料行。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用[sys.fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)目錄檢視。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_fulltext_columns_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@cursor_return =**]  *@cursor_variable* 輸出  
 這類型的輸出變數**游標**。 產生的資料指標是可捲動的唯讀動態資料指標。  
  
 [  **@table_name =**] **'***table_name***'**  
 這是所要求之全文檢索索引資訊的一或兩部分資料表名稱。 *table_name*是**nvarchar （517)**，預設值是 NULL。 如果*table_name*省略，每個全文檢索索引的資料表擷取全文檢索索引資料行資訊。  
  
 [  **@column_name =**] **'***column_name***'**  
 這是需要全文檢索索引中繼資料的資料行名稱。 *column_name*是**sysname**預設值是 NULL。 如果*column_name*省略或為 NULL，就會傳回每個全文檢索索引資料行的全文檢索資料行資訊*table_name*。 如果*table_name*也省略或為 NULL，就會傳回每個全文檢索索引資料行在資料庫中的所有資料表的全文檢索索引資料行資訊。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|資料表擁有者。 這是建立資料表之資料庫使用者的名稱。|  
|**TABLE_ID**|**int**|資料表的識別碼。|  
|**TABLE_NAME**|**sysname**|資料表名稱。|  
|**FULLTEXT_COLUMN_NAME**|**sysname**|在全文檢索索引資料表中，指定給索引作業的資料行。|  
|**FULLTEXT_COLID**|**int**|全文檢索索引資料行的資料行識別碼。|  
|**FULLTEXT_BLOBTP_COLNAME**|**sysname**|在全文檢索索引資料表中，指定全文檢索索引資料行之文件類型的資料行。 全文檢索索引資料行時，才適用此值**varbinary （max)**或**映像**資料行。|  
|**FULLTEXT_BLOBTP_COLID**|**int**|文件類型資料行的資料行識別碼。 全文檢索索引資料行時，才適用此值**varbinary （max)**或**映像**資料行。|  
|**FULLTEXT_LANGUAGE**|**sysname**|資料行的全文檢索搜尋所用的語言。|  
  
## <a name="permissions"></a>Permissions  
 預設執行權限的成員**公用**角色。  
  
## <a name="examples"></a>範例  
 下列範例會傳回資料庫的所有資料表中，指定要編製全文檢索索引之資料行的相關資訊。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_columns_cursor @mycursor OUTPUT  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>請參閱  
 [COLUMNPROPERTY &#40;TRANSACT-SQL &#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [sp_fulltext_column &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)   
 [sp_help_fulltext_columns &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
