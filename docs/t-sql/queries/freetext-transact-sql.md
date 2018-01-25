---
title: "FREETEXT (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 10/23/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREETEXT
- FREETEXT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- full-text search [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXT predicate (Transact-SQL)
- words in predicate [full-text search]
- column searches [full-text search]
ms.assetid: 2f199d3c-440e-4bcf-bdb5-82bb3994005d
caps.latest.revision: "44"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6687946e13dd6c801fcd256a0e463bdacb3779f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="freetext-transact-sql"></a>FREETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  是用於述詞[!INCLUDE[tsql](../../includes/tsql-md.md)] [WHERE 子句](../../t-sql/queries/where-transact-sql.md)的[!INCLUDE[tsql](../../includes/tsql-md.md)]SELECT 陳述式來執行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]全文檢索搜尋的全文檢索索引資料行包含以字元為基礎的資料類型。 這個述詞會搜尋意義與搜尋條件的文字符合但用字不完全相同的值。 使用 FREETEXT 時，全文檢索查詢引擎內部會執行下列動作上*freetext_string*，每個詞彙指派加權，然後尋找相符項目：  
  
-   依據文字界限將字串分隔成單字 (斷詞)。  
  
-   產生字組的字形變化 (詞幹分析)。  
  
-   依據同義字中的相符項目識別詞彙的展開或取代清單。  
  
> [!NOTE]  
>  如需所支援的全文檢索搜尋形式的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請參閱[使用全文檢索搜尋進行查詢](../../relational-databases/search/query-with-full-text-search.md)。  
  
**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))。
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
FREETEXT ( { column_name | (column_list) | * }   
          , 'freetext_string' [ , LANGUAGE language_term ] )  
```  
  
## <a name="arguments"></a>引數  
 *column_name*  
 這是在 FROM 子句中指定之資料表一個或多個全文檢索索引資料行的名稱。 資料行可以是類型**char**， **varchar**， **nchar**， **nvarchar**，**文字**， **ntext**，**映像**， **xml**， **varbinary**，或**varbinary （max)**。  
  
 *column_list*  
 指出您可以指定多個資料行，各資料行用逗號分隔。 *column_list*必須括在括號。 除非*language_term*指定，則所有資料行的語言*column_list*必須相同。  
  
 \*  
 指定全文檢索搜尋已註冊的所有資料行，應該用來搜尋指定*freetext_string*。 如果一個以上的資料表是在 FROM 子句中，\*必須以資料表名稱加以限定。 除非*language_term*指定，則資料表的所有資料行的語言必須相同。  
  
 *freetext_string*  
 是要搜尋的文字*column_name*。 您可以輸入任何文字，其中包括單字、片語或句子。 在全文檢索索引中找到任何詞彙或任何詞彙的各種形式，都會產生相符項目。  
  
 不同於在 CONTAINS 和 CONTAINSTABLE 搜尋條件中，AND 是關鍵字，用於時*freetext_string* word '和' 被視為非搜尋字或[停用字詞](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)，將會被捨棄。  
  
 不允許使用 WEIGHT、FORMSOF、萬用字元、NEAR 和其他語法。 *freetext_string*是這裡，詞幹分析和同義字傳遞。  
  
 *freetext_string*是**nvarchar**。 當使用另一個字元資料類型當做輸入時，會發生隱含轉換。 不能使用大型的字串資料類型 nvarchar （max） 和 varchar （max）。 在下列範例中，定義為 `@SearchWord` 的 `varchar(30)` 變數會造成 `FREETEXT` 述詞中的隱含轉換。  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 「 參數探測 」 不適用於跨越轉換，因為使用**nvarchar**以提升效能。 在範例中，宣告`@SearchWord`為`nvarchar(30)`。  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 當產生的並非最佳計畫時，也可以使用 OPTIMIZE FOR 查詢提示。  
  
 語言*language_term*  
 這是查詢利用其資源來斷詞、分析詞幹，以及移除同義字和停用字詞的語言。 這個參數是選擇性的，可以指定成對應於語言地區設定識別碼 (LCID) 的字串、整數或十六進位值。 如果*language_term*指定時，它代表的語言會套用至搜尋條件的所有項目。 如果未指定任何值，就會使用資料行全文檢索語言。  
  
 如果不同語言的文件當做二進位大型物件 (BLOB) 一起儲存在單一資料行中，給定文件的地區設定識別碼 (LCID) 會判斷要建立其內容索引所使用的語言。 當查詢這類資料行，指定*語言 * * language_term*可以增加完全相符的機率。  
  
 當指定為字串， *language_term*對應至**別名**在他的資料行值[sys.syslanguages &#40;TRANSACT-SQL &#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)相容性檢視。  字串必須括在單引號括住，如 '*language_term*'。 當指定為整數， *language_term*是識別之語言的實際 LCID。 當指定為十六進位值， *language_term* 0x 後面接著 LCID 的十六進位值。 十六進位值不能超出 8 位數，開頭的零也包括在內。  
  
 如果值是雙位元組字集 (DBCS) 格式， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]會將它轉換成 Unicode。  
  
 如果指定的語言不是有效的或是沒有安裝資源，對應於這個語言中， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]會傳回錯誤。 若要使用的中性語言資源，指定 0x0 *language_term*。  
  
## <a name="general-remarks"></a>一般備註  
 全文檢索述詞與函數會在 FROM 述詞中隱含的單一資料表上處理。 若要在多個資料表上進行搜尋，請使用 FROM 子句中聯結的資料表，在兩個或多個資料表之產品的結果集上進行搜尋。  
  
使用 FREETEXT 來進行全文檢索查詢比使用 CONTAINS 來進行全文檢索查詢較為不精確。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索搜尋引擎可找出重要的單字和片語。 沒有特殊意義給予任何保留的關鍵字或萬用字元，通常具有意義，在指定的\<contains_search_condition > CONTAINS 述詞的參數。
  
 全文檢索述詞中不允許[OUTPUT 子句](../../t-sql/queries/output-clause-transact-sql.md)當資料庫相容性層級設定為 100。  
  
> [!NOTE]  
>  FREETEXTTABLE 函數適用的比對種類與 FREETEXT 述詞相同。 您可以參考這個函數中的一般資料表名稱[FROM 子句](../../t-sql/queries/from-transact-sql.md)SELECT 陳述式。 如需詳細資訊，請參閱[FREETEXTTABLE &#40;TRANSACT-SQL &#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md).  
  
## <a name="querying-remote-servers"></a>查詢遠端伺服器  
 您可以使用四部分名稱在[CONTAINS](../../t-sql/queries/contains-transact-sql.md)或 FREETEXT 述詞來查詢全文檢索索引連結的伺服器上的目標資料表資料行。 若要準備遠端伺服器來接收全文檢索查詢，請針對遠端伺服器上的目標資料表與資料行建立全文檢索索引，然後加入遠端伺服器成為連結的伺服器。  
  
## <a name="comparison-of-like-to-full-text-search"></a>LIKE 與全文檢索搜尋的比較  
 相較於全文檢索搜尋，[LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] 述詞只能針對字元模式運作。 您也無法使用 LIKE 述詞來查詢格式化的二進位資料。 此外，針對大量非結構化文字資料執行 LIKE 查詢的速度會比針對相同資料執行對等全文檢索查詢的速度要慢很多。 對於數百萬列的資料，使用 LIKE 查詢時可能要好幾分鐘才能傳回搜尋結果，但是使用全文檢索查詢時可能只要幾秒鐘的時間 (視傳回的資料列數目而定)。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-freetext-to-search-for-words-containing-specified-character-values"></a>A. 使用 FREETEXT 搜尋含有所指定字元值的單字  
 下列範例會搜尋包含 vital、safety 和 components 相關單字的所有文件。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components' );  
GO  
```  
  
### <a name="b-using-freetext-with-variables"></a>B. 搭配變數來使用 FREETEXT  
 下列範例會利用變數來取代特定搜尋詞彙。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30);  
SET @SearchWord = N'high-performance';  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [全文檢索搜尋使用者入門](../../relational-databases/search/get-started-with-full-text-search.md)   
 [建立及管理全文檢索目錄](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [建立全文檢索目錄 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [建立及管理全文檢索索引](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [使用全文檢索搜尋進行查詢](../../relational-databases/search/query-with-full-text-search.md)   
 [建立全文檢索搜尋查詢 &#40;Visual Database Tools&#41;](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
