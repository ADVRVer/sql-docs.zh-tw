---
title: "column_definition (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_definition
- column_definition_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column_definition
- ALTER TABLE statement
- column properties [SQL Server]
- column definitions [SQL Server]
ms.assetid: a1742649-ca29-4d9b-9975-661cdbf18f78
caps.latest.revision: 78
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c63dcea3473198ded46ebf84053fa9d8b36330f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="alter-table-columndefinition-transact-sql"></a>ALTER TABLE column_definition (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定利用加入至資料表的資料行屬性[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
column_name <data_type>  
[ FILESTREAM ]  
[ COLLATE collation_name ]   
[ NULL | NOT NULL ]  
[   
    [ CONSTRAINT constraint_name ] DEFAULT constant_expression [ WITH VALUES ]   
    | IDENTITY [ ( seed , increment ) ] [ NOT FOR REPLICATION ]   
]  
[ ROWGUIDCOL ]   
[ SPARSE ]   
[ ENCRYPTED WITH  
  ( COLUMN_ENCRYPTION_KEY = key_name ,  
      ENCRYPTION_TYPE = { DETERMINISTIC | RANDOMIZED } ,   
      ALGORITHM =  'AEAD_AES_256_CBC_HMAC_SHA_256'   
  ) ]  
[ MASKED WITH ( FUNCTION = ' mask_function ') ]  
[ <column_constraint> [ ...n ] ]  
  
<data type> ::=   
[ type_schema_name . ] type_name   
    [ ( precision [ , scale ] | max |   
        [ { CONTENT | DOCUMENT } ] xml_schema_collection ) ]   
  
<column_constraint> ::=   
[ CONSTRAINT constraint_name ]   
{     { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [   
            WITH FILLFACTOR = fillfactor    
          | WITH ( < index_option > [ , ...n ] )   
        ]   
        [ ON { partition_scheme_name ( partition_column_name )   
            | filegroup | "default" } ]  
  | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
  | CHECK [ NOT FOR REPLICATION ] ( logical_expression )   
}  
```  
  
## <a name="arguments"></a>引數  
 *column_name*  
 要改變、加入或卸除的資料欄名稱。 *column_name*可以包含 1 到 128 個字元。 新的資料行，建立具有時間戳記資料類型、 *column_name*可以省略。 如果沒有*column_name*指定**時間戳記**資料類型資料行、 名稱**時間戳記**用。  
  
 [ *type_schema_name***。** ] *type_name*  
 這是加入的資料行之資料類型及它所屬的結構描述。  
  
 *type_name*可以是：  
  
-   A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]系統資料類型。  
  
-   基於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料類型的別名資料類型。 別名資料類型必須先利用 CREATE TYPE 建立，之後，才能在資料表定義中使用它們。  
  
-   A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]使用者定義型別及它所屬的結構描述。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 使用者自訂類型必須先利用 CREATE TYPE 建立，之後，才能在資料表定義中使用它。  
  
 如果*type_schema_name*未指定， [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]參考*type_name*順序如下：  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料類型。  
  
-   目前資料庫中之目前使用者的預設結構描述。  
  
-   目前資料庫中的 **dbo** 結構描述。  
  
*有效位數*  
 這是指定之資料類型的有效位數。 如需有關有效位數值的詳細資訊，請參閱[有效位數、 小數位數及長度 &#40;TRANSACT-SQL &#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
*scale*  
 這是指定資料類型的小數位數。 如需有關有效小數位數值的詳細資訊，請參閱[有效位數、 小數位數及長度 &#40;TRANSACT-SQL &#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
**最大值**  
 僅適用於**varchar**， **nvarchar**，和**varbinary**資料型別。 這些資料類型用來儲存 2^31 位元組的字元和二進位資料，以及 2^30 位元組的 Unicode 資料。  
  
**內容**  
 指定的每個執行個體**xml**中的資料類型*column_name*可以包含多個最上層元素。 CONTENT 只適用於**xml**資料類型，而且可以是只有當*xml_schema_collection*同時指定。 如果未指定這個項目，CONTENT 便是預設行為。  
  
DOCUMENT  
 指定的每個執行個體**xml**中的資料類型*column_name*可以包含只有一個最上層元素。 DOCUMENT 只適用於**xml**資料類型，而且可以是只有當*xml_schema_collection*同時指定。  
  
 *xml_schema_collection*  
 **適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 僅適用於**xml**將 XML 結構描述集合與型別產生關聯的資料類型。 之前輸入**xml**結構描述資料行中的，結構描述必須先建立資料庫中使用[CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)。  
  
FILESTREAM  
 （選擇性） 指定 FILESTREAM 儲存屬性具有資料行*type_name*的**varbinary （max)**。  
  
 當資料行指定 FILESTREAM 時，資料表也必須有的資料行**uniqueidentifier**具有 ROWGUIDCOL 屬性的資料類型。 這個資料行不能允許 null 值，且必須具有 UNIQUE 或 PRIMARY KEY 單一資料行條件約束。 資料行的 GUID 值必須在插入資料時由應用程式提供，或是由使用 NEWID () 函數的 DEFAULT 條件約束所提供。  
  
 ROWGUIDCOL 資料行無法卸除，而且當資料表有定義 FILESTREAM 資料行時，無法變更相關的條件約束。 只有當最後一個 FILESTREAM 資料行卸除之後，才可卸除 ROWGUIDCOL 資料行。  
  
 當有針對資料行指定 FILESTREAM 儲存屬性時，該資料行的所有值都會儲存在檔案系統的 FILESTREAM 資料容器內。  
  
 如需示範如何使用資料行定義的範例，請參閱[FILESTREAM &#40;SQL Server &#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
COLLATE *sys.databases*  
 指定資料行的定序。 若未指定，就會將資料庫的預設定序指派給資料行。 定序名稱可以是 Windows 定序名稱，也可以是 SQL 定序名稱。 如需清單和詳細資訊，請參閱[Windows 定序名稱 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/windows-collation-name-transact-sql.md)和[SQL Server 定序名稱 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 COLLATE 子句可以用來指定的資料行的定序**char**， **varchar**， **nchar**，和**nvarchar**資料類型.  
  
 如需有關 COLLATE 子句的詳細資訊，請參閱[COLLATE &#40;TRANSACT-SQL &#41;](~/t-sql/statements/collations.md).  
  
 NULL | NOT NULL  
 判斷資料行中是否允許 Null 值。 嚴格來說，NULL 並不算是條件約束，但是您可以如同指定 NOT NULL 一樣加以指定。  
  
[條件約束*constraint_name* ]  
 指定開始定義 DEFAULT 值。 若要維護與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的相容性，您可以將條件約束名稱指派給 DEFAULT。 *constraint_name*必須遵循的規則[識別碼](../../relational-databases/databases/database-identifiers.md)，不同之處在於名稱開頭不能是數字符號 （#）。 如果*constraint_name*未指定，將系統產生的名稱指派給 DEFAULT 定義。  
  
DEFAULT  
 這是指定資料行預設值的關鍵字。 您可以利用 DEFAULT 定義來提供現有資料列之新資料行的值。 無法套用 DEFAULT 定義**時間戳記**資料行或含 IDENTITY 屬性的資料行。 如果使用者定義型別資料行指定預設值，類型必須支援的隱含轉換*constant_expression*使用者定義型別。  
  
*constant_expression*  
 這是用來作為資料行預設值的常值、NULL 或系統函數。 如果是定義的資料行搭配使用[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]使用者定義型別之型別的實作必須支援的隱含轉換*constant_expression*使用者定義型別。  
  
WITH VALUES  
 在預設提供的值會指定*constant_expression*會儲存在新的資料行加入至現有的資料列。 如果加入的資料行允許 NULL 值，且指定了 WITH VALUES，就會將預設值儲存在加入現有資料列的新資料行中。 如果允許 NULL 的資料行沒有指定 WITH VALUES，就會將 NULL 值儲存在現有資料列的新資料行中。 如果新資料行不允許 NULL，就會將預設值儲存在新資料列中，不論是否指定了 WITH VALUES，都是如此。  
  
IDENTITY  
 指定新資料行是識別欄位。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會提供資料行的唯一累加值。 將識別碼資料行加入現有資料表時，識別碼便會加入至資料表中含有初始值和遞增值的現有資料列。 但是，無法保證資料列的更新順序。 任何加入的新資料列也都會產生識別碼。  
  
 識別欄位通常用來結合 PRIMARY KEY 條件約束一起使用，當做資料表的唯一資料列識別碼。 IDENTITY 屬性可以指派給**tinyint**， **smallint**， **int**， **bigint**， **decimal(p,0)**，或**numeric(p,0)**資料行。 每份資料表都只能建立一個識別欄位。 DEFAULT 關鍵字和繫結的預設值無法搭配識別欄位來使用。 您必須同時指定種子和遞增，或同時不指定這兩者。 如果同時不指定這兩者，預設值便是 (1,1)。  
  
> [!NOTE]  
>  您不能修改現有的資料表資料行來加入 IDENTITY 屬性。  
  
 不支援將識別欄位加入已發行的資料表中，因為當資料行複寫到訂閱者時，它可能造成非聚合。 簽發者端識別欄位中的值，隨著受影響的資料表之資料列的實際儲存順序而不同。 訂閱者端可能會用不同的方式來儲存這些資料列；因此，相同資料列可能會有不同的識別欄位值。  
  
 若要允許明確插入值來停用資料行的 IDENTITY 屬性，請使用[SET IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md)。  
  
*種子*  
 這是載入資料表的第一個資料列所用的值。  
  
*遞增*  
 這是加入先前載入的資料列之識別值的累加值。  
  
NOT FOR REPLICATION  
 **適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 可以指定給 IDENTITY 屬性。 如果 IDENTITY 屬性指定了這個子句，當複寫代理程式執行插入作業時，值不會在識別欄位中累加。  
  
ROWGUIDCOL  
 **適用於**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 指定資料行是一個資料列全域唯一識別碼資料行。 ROWGUIDCOL 只能指派給**uniqueidentifier**資料行，而且只有一**uniqueidentifier**每個資料表的資料行可以指定為 ROWGUIDCOL 資料行。 ROWGUIDCOL 不能指派給使用者自訂資料類型的資料行。  
  
 ROWGUIDCOL 不會強制執行資料行所儲存之值的唯一性。 另外，ROWGUIDCOL 也不會自動產生插入資料表之新資料列的值。 若要產生每個資料行的唯一值，請在 INSERT 陳述式上使用 NEWID 函數，或將 NEWID 函數指定為資料行的預設值。 如需詳細資訊，請參閱[NEWID &#40;TRANSACT-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)和[INSERT &#40;TRANSACT-SQL &#41;](../../t-sql/statements/insert-transact-sql.md).  
  
SPARSE  
 指出此資料行是疏鬆資料行。 疏鬆資料行的儲存體會針對 Null 值最佳化。 疏鬆資料行無法指定為 NOT NULL。 如需其他限制和疏鬆資料行的詳細資訊，請參閱[使用疏鬆資料行](../../relational-databases/tables/use-sparse-columns.md)。  
  
\<column_constraint >  
 如需資料行條件約束引數的定義，請參閱[column_constraint &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-table-column-constraint-transact-sql.md).  
  
 使用加密  
 指定加密的資料行使用[永遠加密](../../relational-databases/security/encryption/always-encrypted-database-engine.md)功能。  
  
 COLUMN_ENCRYPTION_KEY = *key_name*  
 指定資料行加密金鑰。 如需詳細資訊，請參閱[CREATE COLUMN ENCRYPTION KEY &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md).  
  
ENCRYPTION_TYPE = {決定性 |隨機}  
 **確定性加密** 使用的方法一律會針對任何指定純文字值產生相同加密值。 使用確定性加密允許搜尋使用相等比較，群組及聯結資料表使用等號比較聯結根據加密值，但也可讓未經授權的使用者透過檢視中的模式，猜測加密值資訊加密的資料行。 決定性加密資料行上聯結兩個資料表時才可能會使用相同的資料行加密金鑰加密兩個資料行。 確定性加密必須針對字元資料行使用 binary2 排序次序的資料行定序。  
  
 **隨機加密** 使用的方法會以更難預測的方式來加密資料。 隨機的加密較為安全，但會防止等號比較搜尋、 分組和聯結加密的資料行。 使用隨機的加密資料行無法編製索引。  
  
 將會搜尋或分組參數，例如政府識別碼數字的資料行，請使用決定性加密。 使用隨機的加密，例如信用卡號碼的資料，其中未利用其它記錄，或用來聯結資料表，以及因為您用來尋找包含加密的資料列的其他資料行 （例如，交易號碼），這不會針對搜尋感興趣的資料行。  
  
 資料行必須為合格的資料類型。  
  
演算法  
**適用於**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]透過[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]， [!INCLUDE[ssSDS](../../includes/sssds-md.md)]。  
必須是**'AEAD_AES_256_CBC_HMAC_SHA_256'**。  
  
 如需詳細資訊，包括功能條件約束，請參閱[永遠加密 &#40; Database engine&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)。  
  
   
新增遮罩與 (函式 = ' *mask_function* ')  
 **適用於**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]透過[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]， [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。  
  
 指定動態資料遮罩。 *mask_function*的遮罩函數，以適當的參數名稱。 下列函數可：  
  
-   default （)  
  
-   email()  
  
-   partial()  
  
-   random()  
  
 函式參數，請參閱[動態資料遮罩](../../relational-databases/security/dynamic-data-masking.md)。  
  
## <a name="remarks"></a>備註  
 如果資料行加入具有**uniqueidentifier**資料類型，它可以定義預設值使用 newid （） 函數來提供新的資料行的資料表中每個現有資料列中的唯一識別碼值。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 不會強制在資料行定義中指定 DEFAULT、IDENTITY、ROWGUIDCOL 或資料行條件約束的順序。  
  
 如果加入資料行會造成資料列大小超過 8060 位元組，則 ALTER TABLE 陳述式會失敗。  
  
## <a name="examples"></a>範例  
 如需範例，請參閱[ALTER TABLE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="see-also"></a>另請參閱  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  

