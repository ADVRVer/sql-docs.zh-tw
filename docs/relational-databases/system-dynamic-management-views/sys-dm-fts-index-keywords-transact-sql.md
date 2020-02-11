---
title: sys.databases dm_fts_index_keywords （Transact-sql） |Microsoft Docs
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
ms.openlocfilehash: e2b5631443603ea111c3ba154726ec3e6b39e0df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67900942"
---
# <a name="sysdm_fts_index_keywords-transact-sql"></a>sys.dm_fts_index_keywords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對指定的資料表傳回全文檢索索引之內容的相關資訊。  
  
 **dm_fts_index_keywords**是動態管理函數。  
  
> [!NOTE]  
>  若要查看較低層級的全文檢索索引資訊，請在檔層級使用[sys.databases dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)動態管理函數。  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.dm_fts_index_keywords( DB_ID('database_name'), OBJECT_ID('table_name') )  
```  
  
## <a name="arguments"></a>引數  
 db_id （'*database_name*'）  
 [DB_ID （）](../../t-sql/functions/db-id-transact-sql.md)函數的呼叫。 此函式會接受資料庫名稱，並傳回資料庫識別碼， **dm_fts_index_keywords**用來尋找指定的資料庫。 如果省略 *database_name*，則會傳回目前的資料庫識別碼。  
  
 object_id （'*table_name*'）  
 [OBJECT_ID （）](../../t-sql/functions/object-id-transact-sql.md)函數的呼叫。 此函數會接受資料表名稱並傳回資料表的資料表識別碼 (包含所要檢查的全文檢索索引)。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**關鍵字**|**nvarchar(4000)**|儲存在全文檢索索引內部之關鍵字的十六進位表示法。<br /><br /> 注意： OxFF 代表表示檔或資料集結尾的特殊字元。|  
|**display_term**|**nvarchar(4000)**|關鍵字的人們可讀取格式。 這個格式衍生自十六進位格式。<br /><br /> 注意： OxFF 的**display_term**值為「檔案結尾」。|  
|**column_id**|**int**|從中針對目前關鍵字進行全文檢索索引之資料行的識別碼。|  
|**document_count**|**int**|包含目前詞彙的文件或資料列數目。|  
  
## <a name="remarks"></a>備註  
 **Sys. dm_fts_index_keywords**所傳回的資訊可用於找出下列各項：  
  
-   關鍵字是否屬於全文檢索索引的一部分。  
  
-   包含給定關鍵字的文件或資料列數目。  
  
-   全文檢索索引中的最常見關鍵字：  
  
    -   每個*keyword_value*的**document_count** ，相較于總**document_count**（0xff 的檔計數）。  
  
    -   一般而言，常見的關鍵字可能可以用於宣告成停用字詞。  
  
> [!NOTE]  
>  **Sys. dm_fts_index_keywords**所傳回的**document_count** ，對於特定檔而言，可能會比**sys. dm_fts_index_keywords_by_document**或**CONTAINS**查詢所傳回的計數較不精確。 據估計，這類潛在錯誤應不到 1%。 這項誤差可能會發生，因為**document_id**在索引片段中的多個資料列之間繼續計算兩次，或在相同的資料列中出現多次時。 若要為特定檔取得更精確的計數，請使用**sys.databases dm_fts_index_keywords_by_document**或**包含**查詢。  
  
## <a name="permissions"></a>權限  
 需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-displaying-high-level-full-text-index-content"></a>A. 顯示概略的全文檢索索引內容  
 下列範例會在 `HumanResources.JobCandidate` 資料表中顯示全文檢索索引之高層級內容的相關資訊。  
  
```  
SELECT * FROM sys.dm_fts_index_keywords(db_id('AdventureWorks2012'), object_id('HumanResources.JobCandidate'))  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [全文檢索搜尋和語義搜尋動態管理檢視和函數 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [全文檢索搜尋](../../relational-databases/search/full-text-search.md)   
 [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
  
