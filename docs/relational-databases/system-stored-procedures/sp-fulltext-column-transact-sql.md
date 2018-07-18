---
title: sp_fulltext_column (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_column_TSQL
- sp_fulltext_column
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_column
ms.assetid: a84cc45d-1b50-44af-85df-2ea033b8a6a9
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6c1a53e05eef89584526846c3f3d3c6324164a94
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38018402"
---
# <a name="spfulltextcolumn-transact-sql"></a>sp_fulltext_column (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  指定資料表的特定資料行是否參與全文檢索索引。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md)改。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_fulltext_column [ @tabname= ] 'qualified_table_name' ,   
     [ @colname= ] 'column_name' ,   
     [ @action= ] 'action'   
     [ , [ @language= ] 'language_term' ]   
     [ , [ @type_colname= ] 'type_column_name' ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@tabname=** ] **'***qualified_table_name***'**  
 這是一或兩部分的資料表名稱。 資料表必須在目前的資料庫中。 資料表必須具有全文檢索索引。 *qualified_table_name&lt*已**nvarchar(517)**，沒有預設值。  
  
 [ **@colname=** ] **'***column_name***'**  
 中的資料行名稱*qualified_table_name&lt*。 這個資料行必須是 character **varbinary （max)** 或是**映像**資料行，不能是計算資料行。 *column_name*已**sysname**，沒有預設值。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以建立全文檢索索引中的資料行所儲存之文字資料**varbinary （max)** 或是**映像**資料型別。 影像和圖片沒有索引。  
  
 [  **@action=** ] **'***動作***'**  
 這是要執行的動作。 *動作*已**varchar （20)**，沒有預設值，它可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**add**|新增*column_name*的*qualified_table_name&lt*資料表的非使用中全文檢索索引。 這個動作會啟用全文檢索索引的資料行。|  
|**卸除**|移除*column_name*的*qualified_table_name&lt*從資料表的非使用中全文檢索索引。|  
  
 [ **@language=** ] **'***language_term***'**  
 這是資料行所儲存之資料的語言。 如需清單，包含的語言[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請參閱 < [sys.fulltext_languages &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)。  
  
> [!NOTE]  
>  當資料行包含的資料有多種語言或不受支援的語言時，請使用「中性」語言。 [預設全文檢索語言] 組態選項指定這個預設值。  
  
 [ **@type_colname =** ] **'***type_column_name***'**  
 中的資料行名稱*qualified_table_name&lt*之資料行文件類型的*column_name*。 此資料行必須是**char**， **nchar**， **varchar**，或**nvarchar**。 它時才會使用的資料類型*column_name*別的**varbinary （max)** 或是**映像**。 *type_column_name*已**sysname**，沒有預設值。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 無  
  
## <a name="remarks"></a>備註  
 如果全文檢索索引在使用中，任何進行中的擴展都會停止。 此外，如果含有使用中的全文檢索索引之資料表啟用了變更追蹤，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會確保這是目前的索引。 例如，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會停止資料表任何目前的擴展動作、卸除現有的索引，再啟動新的擴展動作。  
  
 如果已開啟變更追蹤，且既要保留索引，又必須在全文檢索索引中加入或卸除資料行，就應該停用資料表，再加入或卸除必要的資料行。 這些動作會凍結索引。 稍後，當開始擴展確實可行時，您可以再啟動這份資料表。  
  
## <a name="permissions"></a>Permissions  
 使用者必須隸屬**db_ddladmin**固定資料庫角色或隸屬**db_owner**固定資料庫角色或資料表的擁有者。  
  
## <a name="examples"></a>範例  
 下列範例將 `DocumentSummary` 資料表的 `Document` 資料行加入資料表的全文檢索索引中。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_column 'Production.Document', DocumentSummary, 'add';  
GO  
```  
  
 下列範例假設您在名稱為 `spanishTbl` 的資料表上，建立了全文檢索索引。 若要將 `spanishCol` 資料行加入全文檢索索引中，請執行下列預存程序：  
  
```  
EXEC sp_fulltext_column 'spanishTbl', 'spanishCol', 'add', 0xC0A;  
GO  
```  
  
 當您執行這個查詢時：  
  
```  
SELECT *   
FROM spanishTbl   
WHERE CONTAINS(spanishCol, 'formsof(inflectional, trabajar)')  
```  
  
 結果集會包括含有不同形式的 `trabajar` (如 `trabajo`、`trabajamos` 和 `trabajan`) 的資料列 (才能運作)。  
  
> [!NOTE]  
>  單一全文檢索查詢函數子句中所列出的所有資料行，都必須使用相同的語言。  
  
## <a name="see-also"></a>另請參閱  
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [遇到 sp_help_fulltext_columns &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [遇到 sp_help_fulltext_columns_cursor &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-cursor-transact-sql.md)   
 [遇到 sp_help_fulltext_tables &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [遇到 sp_help_fulltext_tables_cursor &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-cursor-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [全文檢索搜尋和語意搜尋預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
