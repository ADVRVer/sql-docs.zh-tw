---
title: sys.dm_fts_index_keywords (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords
- sys.dm_fts_index_keywords
- sys.dm_fts_index_keywords_TSQL
- dm_fts_index_keywords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_index_keywords dynamic management function
- full-text search [SQL Server], viewing keywords
- troubleshooting [SQL Server], full-text search
ms.assetid: fce7b2a1-7e74-4769-86a8-c77c7628decd
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: de956e2dffebd801205bf4ac46a7f503e1acbe8f
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65944272"
---
# <a name="sysdmftsindexkeywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對指定的資料表傳回全文檢索索引之內容的相關資訊。  
  
 **sys.dm_fts_index_keywords**是動態管理函數。  
  
> [!NOTE]  
>  若要檢視較低層級的全文檢索索引資訊，請使用[sys.dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)文件層級的動態管理函數。  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>引數  
 db_id('*database_name*')  
 呼叫[db_id （)](../../t-sql/functions/db-id-transact-sql.md)函式。 此函式會接受資料庫名稱，並傳回資料庫識別碼，這**sys.dm_fts_index_keywords**用來尋找指定的資料庫。 如果省略 *database_name*，則會傳回目前的資料庫識別碼。  
  
 object_id('*table_name*')  
 呼叫[object_id （)](../../t-sql/functions/object-id-transact-sql.md)函式。 此函數會接受資料表名稱並傳回資料表的資料表識別碼 (包含所要檢查的全文檢索索引)。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**keyword**|**nvarchar(4000)**|儲存在全文檢索索引內部之關鍵字的十六進位表示法。<br /><br /> 注意:OxFF 代表指出檔案或資料集的結尾的特殊字元。|  
|**display_term**|**nvarchar(4000)**|關鍵字的人們可讀取格式。 這個格式衍生自十六進位格式。<br /><br /> 注意:**Display_term**值 OxFF 是"END OF FILE"。|  
|**column_id**|**int**|從中針對目前關鍵字進行全文檢索索引之資料行的識別碼。|  
|**document_count**|**int**|包含目前詞彙的文件或資料列數目。|  
  
## <a name="remarks"></a>備註  
 所傳回的資訊**sys.dm_fts_index_keywords**適合用來找出下列項目，以及其他項目：  
  
-   關鍵字是否屬於全文檢索索引的一部分。  
  
-   包含給定關鍵字的文件或資料列數目。  
  
-   全文檢索索引中的最常見關鍵字：  
  
    -   **document_count**每個*keyword_value*相較於總**document_count**，文件計數為 0xFF。  
  
    -   一般而言，常見的關鍵字可能可以用於宣告成停用字詞。  
  
> [!NOTE]  
>  **Document_count**由**sys.dm_fts_index_keywords**可能是較不精確的特定文件所傳回的計數**sys.dm_fts_index_keywords_by_document**或是**CONTAINS**查詢。 據估計，這類潛在錯誤應不到 1%。 這類錯誤可能是因為**document_id**兩次時它會繼續在索引片段中，或出現一次以上相同的資料列中的多個資料列時，才可能會被計算。 若要取得更精確的計數，特定文件，請使用**sys.dm_fts_index_keywords_by_document**或是**CONTAINS**查詢。  
  
## <a name="permissions"></a>Permissions  
 需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-displaying-high-level-full-text-index-content"></a>A. 顯示概略的全文檢索索引內容  
 下列範例會在 `HumanResources.JobCandidate` 資料表中顯示全文檢索索引之高層級內容的相關資訊。  
  
```  
SELECT * FROM sys.dm_fts_index_keywords(db_id('AdventureWorks2012'), object_id('HumanResources.JobCandidate'))  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [全文檢索搜尋和語意搜尋動態管理檢視和函式&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [全文檢索搜尋](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
