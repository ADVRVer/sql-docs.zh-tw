---
title: sys.databases dm_fts_index_keywords_by_property （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_index_keywords_by_property
- dm_fts_index_keywords_by_property_TSQL
- sys.dm_fts_index_keywords_by_property
- sys.dm_fts_index_keywords_by_property_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], troubleshooting
- search property lists [SQL Server], viewing keywords by property
- full-text search [SQL Server], viewing keywords
- sys.dm_fts_index_keywords_by_property dynamic management view
ms.assetid: fa41e052-a79a-4194-9b1a-2885f7828500
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 82f433d18ff0940c9283f93cfa5e3f87179d31ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68078547"
---
# <a name="sysdm_fts_index_keywords_by_property-transact-sql"></a>sys.dm_fts_index_keywords_by_property (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  傳回給定資料表之全文檢索索引中的所有屬性相關內容。 這包括與該全文檢索索引相關聯的搜尋屬性清單所註冊之任何屬性的一切所屬資料。  
  
 dm_fts_index_keywords_by_property 是動態管理函數，可讓您查看 Ifilter 在索引時間發出哪些已註冊的屬性，以及每個已編制索引檔中每個屬性的確切內容。  
  
 **若要檢視所有文件層級內容 (包括屬性相關內容)**  
  
-   [sys.dm_fts_index_keywords_by_document &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)  
  
 **若要檢視較高層級的全文檢索索引資訊**  
  
-   [sys.dm_fts_index_keywords &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)  
  
> [!NOTE]  
>  如需搜尋屬性清單的詳細資訊，請參閱[使用搜尋屬性清單搜尋文件屬性](../../relational-databases/search/search-document-properties-with-search-property-lists.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.dm_fts_index_keywords_by_property  
(   
    DB_ID('database_name'),   
OBJECT_ID('table_name')   
)  
```  
  
## <a name="arguments"></a>引數  
 db_id （'*database_name*'）  
 [DB_ID （）](../../t-sql/functions/db-id-transact-sql.md)函數的呼叫。 此函式會接受資料庫名稱，並傳回資料庫識別碼，dm_fts_index_keywords_by_property 用來尋找指定的資料庫。 如果省略 *database_name*，則會傳回目前的資料庫識別碼。  
  
 object_id （'*table_name*'）  
 [OBJECT_ID （）](../../t-sql/functions/object-id-transact-sql.md)函數的呼叫。 此函數會接受資料表名稱並傳回資料表的資料表識別碼 (包含所要檢查的全文檢索索引)。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行|資料類型|描述|  
|------------|---------------|-----------------|  
|關鍵字 (keyword)|**nvarchar(4000)**|儲存在全文檢索索引內部之關鍵字的十六進位表示法。<br /><br /> 注意： OxFF 代表表示檔或資料集結尾的特殊字元。|  
|display_term|**nvarchar(4000)**|關鍵字的人們可讀取格式。 這個格式衍生自儲存在全文檢索索引中的內部格式。<br /><br /> 注意： OxFF 代表表示檔或資料集結尾的特殊字元。|  
|column_id|**int**|從中針對目前關鍵字進行全文檢索索引之資料行的識別碼。|  
|document_id|**int**|從中針對目前詞彙進行全文檢索索引之文件或資料列的識別碼。 這個識別碼會對應至該文件或資料列的全文檢索索引鍵值。|  
|property_id|**int**|在您于 OBJECT_ID （'*table_name*'）參數中指定之資料表的全文檢索索引內，搜尋屬性的內部屬性識別碼。<br /><br /> 當給定的屬性新增到搜尋屬性清單時，全文檢索引擎會註冊屬性，並為它指派該屬性清單特有的內部屬性識別碼。 對於給定的搜尋屬性清單來說，內部屬性識別碼 (本身為整數) 是唯一的。 如果給定屬性已在多個搜尋屬性清單中註冊，可能會為每個搜尋屬性清單指定不同的內部屬性識別碼。<br /><br /> 注意：內部屬性識別碼與將屬性加入至搜尋屬性清單時所指定的屬性整數識別碼不同。 如需詳細資訊，請參閱 [使用搜索屬性清單搜索文件屬性](../../relational-databases/search/search-document-properties-with-search-property-lists.md)。<br /><br /> 若要查看 property_id 與屬性名稱之間的關聯：<br />                    [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)|  
  
## <a name="remarks"></a>備註  
 這個動態管理檢視可以回答類似下列的問題：  
  
-   給定 DocID 的給定屬性中會儲存何種內容？  
  
-   已索引文件之間的給定屬性，其常見程度為何？  
  
-   哪些文件會實際包含給定屬性？ 如果查詢給定搜尋屬性無法傳回您預期想要尋找的文件，這便顯得相當有用。  
  
 當全文檢索索引鍵資料行為整數資料類型時，建議您將 document_id 直接對應到基底資料表內的全文檢索索引鍵值。  
  
 相反地，當全文檢索索引鍵資料行使用非整數資料類型時，document_id 就不表示基底資料表內的全文檢索索引鍵。 在此情況下，若要識別 dm_fts_index_keywords_by_property 所傳回之基表中的資料列，您需要將此視圖與[sp_fulltext_keymappings](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)所傳回的結果聯結。 在您可以聯結之前，必須先將預存程序的輸出儲存到暫存資料表。 然後您可以聯結 dm_fts_index_keywords_by_property 的 document_id 資料行與此預存程式所傳回的 DocId 資料行。 請注意，**時間戳記**資料行無法在插入時接收值，因為它們是由自動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]產生的。 因此，**時間戳記**資料行必須轉換成**Varbinary （8）** 資料行。 下列範例會示範這些步驟。 在此範例中， *table_id*是資料表的識別碼， *database_name*是您的資料庫名稱，而*table_name*則是資料表的名稱。  
  
```  
USE database_name;  
GO  
CREATE TABLE #MyTempTable   
   (  
      docid INT PRIMARY KEY ,  
      [key] INT NOT NULL  
   );  
DECLARE @db_id int = db_id(N'database_name');  
DECLARE @table_id int = OBJECT_ID(N'table_name');  
INSERT INTO #MyTempTable EXEC sp_fulltext_keymappings @table_id;  
SELECT * FROM sys.dm_fts_index_keywords_by_property   
   ( @db_id, @table_id ) kbd  
   INNER JOIN #MyTempTable tt ON tt.[docid]=kbd.document_id;  
GO  
  
```  
  
## <a name="permissions"></a>權限  
 需要全文檢索索引和 CREATE FULLTEXT CATALOG 權限所涵蓋之資料行的 SELECT 權限。  
  
## <a name="examples"></a>範例  
 下列範例會從 `Author` 範例資料庫之 `Production.Document` 資料表傳回全文檢索索引中的 `AdventureWorks` 屬性。 此範例會使用 sys.databases `KWBPOP`所傳回之資料表的別名**dm_fts_index_keywords_by_property**。 此範例使用內部聯結來結合 sys.databases 的資料行[registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)和[sys.databases。 fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)。  
  
```  
-- Once the full-text index is configured to support property searching  
-- on the Author property, return any keywords indexed for this property.  
USE AdventureWorks2012;  
GO   
SELECT KWBPOP.* FROM   
   sys.dm_fts_index_keywords_by_property( DB_ID(),   
   object_id('Production.Document') ) AS KWBPOP  
   INNER JOIN  
      sys.registered_search_properties AS RSP ON(   
         (KWBPOP.property_id = RSP.property_id)   
         AND (RSP.property_name = 'Author') )  
   INNER JOIN  
      sys.fulltext_indexes AS FTI ON(   
         (FTI.[object_id] = object_id('Production.Document'))   
         AND (RSP.property_list_id = FTI.property_list_id) );  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [全文檢索搜尋](../../relational-databases/search/full-text-search.md)   
 [改善全文檢索索引的效能](../../relational-databases/search/improve-the-performance-of-full-text-indexes.md)   
 [sp_fulltext_keymappings &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-keymappings-transact-sql.md)   
 [dm_fts_index_keywords_by_document &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)   
 [dm_fts_index_keywords &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)   
 [registered_search_properties &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [registered_search_property_lists &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [使用搜索屬性清單搜索文件屬性](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
