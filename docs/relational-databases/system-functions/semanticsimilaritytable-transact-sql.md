---
title: semanticsimilaritytable （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- semanticsimilaritytable
- semanticsimilaritytable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- semanticsimilaritytable function
ms.assetid: b49d40ab-7552-438b-ad67-6237dcccb75b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 759ac2b464bbdee2a0199afe540f00c7695381a9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764273"
---
# <a name="semanticsimilaritytable-transact-sql"></a>semanticsimilaritytable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回具有零個、一個或多個文件資料列的資料表，而這些文件在指定資料行的內容，與指定文件的語意相似。  
  
 您可以在 SELECT 陳述式的 FROM 子句中參考這個資料列集函數，就像是一般資料表名稱一樣。  

 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```sql  
SEMANTICSIMILARITYTABLE  
    (  
    table,  
    { column | (column_list) | * },  
    source_key  
    )  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>參量  
 **table**  
 這是已啟用全文檢索和語意索引之資料表的名稱。  
  
 這個名稱可以是一到四個部分名稱，但不允許遠端伺服器名稱。  
  
 **column**  
 應傳回結果之索引資料行的名稱。 資料行必須啟用語意索引。  
  
 **column_list**  
 指定以逗號分隔並括以括號的數個資料行。 所有資料行皆必須啟用語意索引。  
  
 **\***  
 指定已包含所有啟用語意索引的資料行。  
  
 **source_key**  
 資料列的唯一索引鍵，可以用於要求特定資料列的結果。  
  
 在可能的情況下，此索引鍵會隱含轉換成來源資料表中的全文檢索唯一索引鍵類型。 索引鍵可以指定成常數或變數，但不可以是運算式或純量子查詢的結果。  
  
## <a name="table-returned"></a>傳回的資料表  
 下表說明此資料列集函數傳回之類似或相關文件的詳細資訊。  
  
 如果結果來自多個資料行，將會以每個資料行為單位傳回相符文件。  
  
|Column_name|類型|描述|  
|------------------|----------|-----------------|  
|**source_column_id**|**int**|用於尋找類似文件之來源文件的資料行識別碼。<br /><br /> 如需如何從 column_id 擷取資料行名稱 (反之亦然) 的詳細資料，請參閱 COL_NAME 及 COLUMNPROPERTY 函數。|  
|**matched_column_id**|**int**|從中找到類似文件之資料行的識別碼。<br /><br /> 如需如何從 column_id 擷取資料行名稱 (反之亦然) 的詳細資料，請參閱 COL_NAME 及 COLUMNPROPERTY 函數。|  
|**matched_document_key**|**\***<br /><br /> 此索引鍵與來源資料表中的唯一索引鍵類型相同。|文件或資料行的全文檢索和語意擷取唯一索引鍵值，在查詢中發現此文件或資料行與指定的文件類似。|  
|**成績**|**即時**|此文件與所有其他類似文件之間關聯性的相似度相對值。<br /><br /> 值是 [0.0, 1.0] 範圍內的小數值，分數愈高代表愈符合的相似度，1.0 是滿分。|  
  
## <a name="general-remarks"></a>一般備註  
 如需詳細資訊，請參閱[使用語義搜尋尋找相似及相關的檔](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)。  
  
## <a name="limitations-and-restrictions"></a>限制事項  
 您不能跨資料行查詢類似文件。 **SEMANTICSIMILARITYTABLE**函數只會從與來源資料行相同的資料行中，抓取類似的檔，這是由**source_key**引數所識別。  
  
## <a name="metadata"></a>中繼資料  
 如需有關語意相似度擷取和母體擴展的詳細資訊和狀態，請查詢下列動態管理檢視：  
  
-   [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>權限  
 需要建立全文檢索和語意索引之基底資料表的 SELECT 權限。  
  
## <a name="examples"></a>範例  
 下列範例會從 AdventureWorks2012 範例資料庫的 HumanResources.JobCandidate 資料表中，擷取類似於指定候選人的前 10 個候選人。  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROMSEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
  
```  
  
  
