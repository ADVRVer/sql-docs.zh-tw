---
title: sp_describe_undeclared_parameters （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_undeclared_parameters
- sp_describe_undeclared_parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_undeclared_parameters
ms.assetid: 6f016da6-dfee-4228-8b0d-7cd8e7d5a354
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1205572235b141709cd463476182d9b405446188
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72908332"
---
# <a name="sp_describe_undeclared_parameters-transact-sql"></a>sp_describe_undeclared_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  傳回結果集，其中包含有關 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次中未宣告之參數的中繼資料。 會考慮 **\@tsql**批次中使用的每個參數，但不會在 **\@params**中宣告。 傳回的結果集中，針對每一個這類參數包含一個資料列，內含該參數的推算類型資訊。 如果 **\@tsql**輸入批次沒有參數（在 **\@params**中宣告），則此程式會傳回空的結果集。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [transact-sql 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```sql
  
sp_describe_undeclared_parameters   
    [ @tsql = ] 'Transact-SQL_batch'   
    [ , [ @params = ] N'parameters' data type ] [, ...n]  
```  
  
## <a name="arguments"></a>引數  
`[ \@tsql = ] 'Transact-SQL\_batch'` 一個或多個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句。 *SQL_batch*可以是**Nvarchar （** _n_ **）** 或**Nvarchar （max）** 。  
  
`[ \@params = ] N'parameters'` \@params 提供 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次參數的宣告字串，類似于 sp_executesql 的運作方式。 *參數*可以是**Nvarchar （** _n_ **）** 或**Nvarchar （max）** 。  
  
 這是一個字串，其中包含已內嵌在*SQL_batch*中之所有參數的定義。 此字串必須是 Unicode 常數或 Unicode 變數。 每個參數定義都由參數名稱和資料類型組成。 n 是指出其他參數定義的預留位置。 如果語句中的 Transact-sql 語句或批次不包含參數，則不需要 \@params。 這個參數的預設值是 NULL。  
  
 資料類型  
 參數的資料類型。  
  
## <a name="return-code-values"></a>傳回碼值  
 在成功時， **sp_describe_undeclared_parameters**一律會傳回零的傳回狀態。 如果程式擲回錯誤，並將程式稱為 RPC，則傳回狀態會填入 _exec_describe_first_result_set 的 error_type 資料行中所述的錯誤類型。 如果程序是從 [!INCLUDE[tsql](../../includes/tsql-md.md)] 所呼叫，即使發生錯誤，傳回值也永遠是零。  
  
## <a name="result-sets"></a>結果集  
 **sp_describe_undeclared_parameters**會傳回下列結果集。  
  
|資料行名稱|[名稱]|[描述]|  
|-----------------|---------------|-----------------|  
|**parameter_ordinal**|**int NOT Null**|包含結果集中的參數序數位置。 第一個參數的位置將會指定為 1。|  
|**name**|**sysname 不是 Null**|包含參數的名稱。|  
|**suggested_system_type_id**|**int NOT Null**|包含在 sys.databases 中指定之參數資料類型的**system_type_id** 。<br /><br /> 針對 CLR 類型，即使**system_type_name**資料行將傳回 Null，這個資料行會傳回值240。|  
|**suggested_system_type_name**|**Nvarchar （256） Null**|包含資料類型名稱。 包含指定給參數之資料類型的引數 (例如長度、有效位數、小數位數)。 如果資料類型是使用者定義的別名類型，這裡就會指定基礎系統類型。 如果它是 CLR 使用者定義資料類型，這個資料行就會傳回 NULL。 如果無法推算參數的類型，則傳回 NULL。|  
|**suggested_max_length**|**Smallint NOT Null**|請參閱 sys.databases。 適用于**max_length**資料行描述。|  
|**suggested_precision**|**Tinyint NOT Null**|請參閱 sys.databases。 以查看 precision 資料行的說明。|  
|**suggested_scale**|**Tinyint NOT Null**|請參閱 sys.databases。 以查看 scale 資料行的說明。|  
|**suggested_user_type_id**|**int Null**|針對 CLR 和別名類型，會如同 sys.types 中所指定，包含資料行資料類型的 user_type_id。 否則，便為 NULL。|  
|**suggested_user_type_database**|**sysname Null**|針對 CLR 和別名類型，會包含定義類型之資料庫的名稱。 否則，便為 NULL。|  
|**suggested_user_type_schema**|**sysname Null**|針對 CLR 和別名類型，會包含定義類型之結構描述的名稱。 否則，便為 NULL。|  
|**suggested_user_type_name**|**sysname Null**|針對 CLR 和別名類型，會包含類型的名稱。 否則，便為 NULL。|  
|**suggested_assembly_qualified_type_name**|**Nvarchar （4000） Null**|針對 CLR 類型，會傳回定義類型之組件與類別的名稱。 否則，便為 NULL。|  
|**suggested_xml_collection_id**|**int Null**|包含參數資料類型的 xml_collection_id，如 sys.databases 中所指定。 如果傳回的類型沒有與 XML 結構描述集合相關聯，這個資料行將傳回 NULL。|  
|**suggested_xml_collection_database**|**sysname Null**|包含定義與這個類型相關聯之 XML 結構描述集合的資料庫。 如果傳回的類型沒有與 XML 結構描述集合相關聯，這個資料行將傳回 NULL。|  
|**suggested_xml_collection_schema**|**sysname Null**|包含定義與這個類型相關聯之 XML 結構描述集合的結構描述。 如果傳回的類型沒有與 XML 結構描述集合相關聯，這個資料行將傳回 NULL。|  
|**suggested_xml_collection_name**|**sysname Null**|包含與這個類型相關聯之 XML 結構描述集合的名稱。 如果傳回的類型沒有與 XML 結構描述集合相關聯，這個資料行將傳回 NULL。|  
|**suggested_is_xml_document**|**位 NOT Null**|如果正要傳回的類型是 XML，而且該類型保證是 XML 文件，則傳回 1。 否則傳回 0。|  
|**suggested_is_case_sensitive**|**位 NOT Null**|如果資料行是區分大小寫的字串類型，則傳回 1，否則傳回 0。|  
|**suggested_is_fixed_length_clr_type**|**位 NOT Null**|如果資料行是固定長度的 CLR 類型，則傳回 1，否則傳回 0。|  
|**suggested_is_input**|**位 NOT Null**|如果參數用於指派左邊以外的任何地方，則傳回 1。 否則傳回 0。|  
|**suggested_is_output**|**位 NOT Null**|如果參數用在指派的左邊，或傳遞至預存程序的輸出參數，則傳回 1。 否則傳回 0。|  
|**formal_parameter_name**|**sysname Null**|如果參數是預存程序或使用者定義函數的引數，則傳回對應型式參數的名稱。 否則，便傳回 NULL。|  
|**suggested_tds_type_id**|**int NOT Null**|供內部使用。|  
|**suggested_tds_length**|**int NOT Null**|供內部使用。|  
  
## <a name="remarks"></a>Remarks  
 **sp_describe_undeclared_parameters**一律會傳回零的傳回狀態。  
  
 最常見的用法是在應用程式中提供可能包含參數且必須以特定方式處理的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。 其中一個範例是使用者介面（例如 ODBCTest 或 RowsetViewer），使用者可在其中提供具有 ODBC 參數語法的查詢。 應用程式必須動態探索參數數目，並提示使用者提供每個參數值。  
  
 另一個例子是，當沒有使用者輸入的情況下，應用程式必須在參數上執行迴圈，並從其他位置 (例如資料表) 為它們取得資料。 在這種情況下，應用程式不必一次傳遞所有參數資訊。 相反地，應用程式可以從提供者取得所有參數資訊，並自行從資料表取得資料。 使用**sp_describe_undeclared_parameters**的程式碼較為通用，如果資料結構之後變更，則較不可能需要修改。  
  
 **sp_describe_undeclared_parameters**會在下列任何情況下傳回錯誤。  
  
-   如果輸入 \@tsql 不是有效的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次。 有效性是藉由剖析和分析 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次來判斷。 判斷 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次是否有效時，批次在查詢優化期間或執行期間所造成的任何錯誤都不會列入考慮。  
  
-   如果 \@params 不是 Null，而且包含的字串不是以語法表示的有效宣告字串，或其包含的字串會宣告任何參數一次以上，則為。  
  
-   如果輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次宣告的區域變數名稱與 \@params 中所宣告的參數相同。  
  
- 如果語句參考臨時表，則為。

- 查詢包含建立隨後要查詢的永久資料表。
  
 如果 \@tsql 沒有參數（而不是在 \@params 中宣告），則程式會傳回空的結果集。  
  
## <a name="parameter-selection-algorithm"></a>參數選取演算法  
 針對具有未宣告之參數的查詢，在三個步驟中進行未宣告之參數的資料類型推算。  
  
 **步驟1**  
  
 針對具有未宣告之參數的查詢，資料類型推算的第一步是找出資料類型不相依於未宣告的參數之所有子運算式的資料類型。 可判斷下列運算式的類型：  
  
-   資料行、常數、變數和宣告的參數。  
  
-   使用者定義函數 (UDF) 呼叫的結果。  
  
-   資料類型不相依於所有輸入中未宣告的參數之運算式。  
  
 例如，請考量 `SELECT dbo.tbl(@p1) + c1 FROM t1 WHERE c2 = @p2 + 2` 查詢。 運算式 dbo.tbl （\@p1） + c1 和 c2 具有資料類型，而 expression \@p1 和 \@p2 + 2 則否。  
  
 在此步驟之後，如果任何運算式 (UDF 呼叫以外) 有兩個不含資料類型的引數，類型推算會失敗並出現錯誤。 例如，下列範例都會產生錯誤：  
  
```sql
SELECT * FROM t1 WHERE @p1 = @p2  
SELECT * FROM t1 WHERE c1 = @p1 + @p2  
SELECT * FROM t1 WHERE @p1 = SUBSTRING(@p2, 2, 3)  
```  
  
 下列範例不會產生錯誤：  
  
```sql
SELECT * FROM t1 WHERE @p1 = dbo.tbl(c1, @p2, @p3)  
```
  
 **步驟2**  
  
 若為指定的未宣告參數 \@p，類型推算演算法會尋找包含 \@p 且為下列其中一項的最內層運算式 E （\@p）：  
  
-   比較或指派運算子的引數。  
  
-   使用者定義函數 (包括資料表值 UDF)、程序或方法的引數。  
  
-   **INSERT**語句的**VALUES**子句的引數。  
  
-   **CAST**或**CONVERT**的引數。  
  
 類型推算演算法會尋找 E （\@p）的目標資料類型 TT （\@p）。 上述範例的目標資料類型如下所示：  
  
-   比較或指派另一端的資料類型。  
  
-   傳遞此引數之目標參數的已宣告資料類型。  
  
-   插入此值之資料行的資料類型。  
  
-   陳述式轉型或轉換成的資料類型。  
  
 例如，請考量 `SELECT * FROM t WHERE @p1 = dbo.tbl(@p2 + c1)` 查詢。 然後，E （\@p1） = \@p1，E （\@p2） = \@p2 + c1，TT （\@p1）是宣告的傳回資料類型 dbo.tbl，TT （\@p2）是 dbo.tbl 的宣告參數資料類型。  
  
 如果 \@p 並未包含在步驟2開頭所列的任何運算式中，則類型推算演算法會判斷 E （\@p）是包含 \@p 的最大純量運算式，而類型推算演算法不會計算目標資料針對 E （\@p）輸入 TT （\@p）。 例如，如果查詢是 SELECT `@p + 2` 則 E （\@p） = \@p + 2，而且沒有 TT （\@p）。  
  
 **步驟3**  
  
 現在已識別 E （\@p）和 TT （\@p），類型推算演算法會以下列兩種方式之一，會推算 \@p 的資料類型：  
  
-   簡單推算  
  
     如果 E （\@p） = \@p 和 TT （\@p）存在，也就是如果 \@p 直接是步驟2開頭所列其中一個運算式的引數，則類型推算演算法會將 \@p 的資料類型會推算為 TT （\@p）。 例如：  
  
    ```sql
    SELECT * FROM t WHERE c1 = @p1 AND @p2 = dbo.tbl(@p3)  
    ```  
  
     \@p1、\@p2 和 \@p3 的資料類型會分別是 c1 的資料類型、dbo.tbl 的傳回資料類型，以及 dbo.tbl 的參數資料類型。  
  
     在特殊情況下，如果 \@p 是 \<、>、\<= 或 > = 運算子的引數，則不適用簡單的推算規則。 類型推算演算法會使用下一節所述的一般推算規則。 例如，如果 c1 是資料類型 char(30) 的資料行，請考慮下列兩個查詢：  
  
    ```sql
    SELECT * FROM t WHERE c1 = @p  
    SELECT * FROM t WHERE c1 > @p  
    ```  
  
     在第一個案例中，類型推算演算法會會推算**char （30）** 做為根據本主題稍早規則 \@p 的資料類型。 在第二個案例中，類型推算演算法會根據下一節中的一般推算規則來會推算**Varchar （8000）** 。  
  
-   一般推算  
  
     如果不適用簡單推算，針對未宣告的參數，下列資料類型會列入考量：  
  
    -   整數資料類型（**bit**、 **Tinyint**、 **Smallint**、 **int**、 **Bigint**）  
  
    -   Money 資料類型（**smallmoney**， **money**）  
  
    -   浮點資料類型（**float**、 **real**）  
  
    -   **數位（38，19）** -不考慮其他數值或十進位資料類型。  
  
    -   **Varchar （8000）** 、 **Varchar （max）** 、 **Nvarchar （4000）** 和**Nvarchar （max）** -不考慮其他字串資料類型（例如**text**、 **char （8000）** 、 **Nvarchar （30）** 等等）。  
  
    -   **Varbinary （8000）** 和**Varbinary （max）** -不考慮其他二進位資料類型（例如**image**、 **binary （8000）** 、 **Varbinary （30）** 等等）。  
  
    -   **date**、 **time （7）** 、 **Smalldatetime**、 **datetime**、 **datetime2 （7）** 、 **datetimeoffset （7）** -不考慮其他日期和時間類型，例如**time （4）** 。  
  
    -   **sql_variant**  
  
    -   **xml**  
  
    -   CLR 系統定義的類型（**hierarchyid**、 **geometry**、 **geography**）  
  
    -   CLR 使用者定義型別  
  
### <a name="selection-criteria"></a>選取準則  
 在候選資料類型中，會導致查詢失效的任何資料類型都會遭到拒絕。 在剩餘的候選資料類型中，類型推算演算法會根據下列規則來選取其中一個資料類型。  
  
1.  選取的資料類型會在 E （\@p）中，產生最小的隱含轉換數目。 如果特定資料類型針對 E （\@p）產生與 TT （\@p）不同的資料類型，則類型推算演算法會將此視為從 E （\@p）的資料類型到 TT （\@p）的額外隱含轉換。  
  
     例如：  
  
    ```sql
    SELECT * FROM t WHERE Col_Int = Col_Int + @p  
    ```  
  
     在此情況下，E （\@p）是 Col_Int + \@p 和 TT （\@p）是**Int**。已為 \@p 選擇**int** ，因為它不會產生隱含轉換。 任何其他資料類型選擇會產生至少一個隱含轉換。  
  
2.  如果多個資料類型有相同的最小轉換數目，則會使用具有較高優先順序的資料類型。 例如：  
  
    ```sql
    SELECT * FROM t WHERE Col_Int = Col_smallint + @p  
    ```  
  
     在此情況下， **int**和**Smallint**會產生一個轉換。 所有其他的資料類型都會產生一個以上的轉換。 因為**int**的優先順序高於**Smallint**，所以會將**int**用於 \@p。 如需資料類型優先順序的詳細資訊，請參閱[資料&#40;類型優先順序 transact-sql&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)。  
  
     只有在依據規則 1 每個候選資格相同的資料類型與具有最高優先順序的資料類型之間發生隱含轉換時，才會套用此規則。 如果沒有隱含轉換，資料類型推算會失敗並出現錯誤。 例如，在查詢 `SELECT @p FROM t`中，資料類型推算會失敗，因為 \@p 的任何資料類型都同樣好用。 例如，沒有從**int**到**xml**的隱含轉換。  
  
3.  如果兩個類似的資料類型系結在規則1下（例如**Varchar （8000）** 和**Varchar （max）** ），則會選擇較小的資料類型（**Varchar （8000）** ）。 相同的原則也適用于**Nvarchar**和**Varbinary**資料類型。  
  
4.  為執行規則 1，類型推算演算法會偏好特定轉換。 從最佳到最差的轉換順序如下：  

    1.  不同長度的同一個基本資料類型之間的轉換。  
  
    2.  在固定長度和可變長度版本的相同資料類型（例如**char**到**Varchar**）之間進行轉換。  
  
    3.  **Null**和**int**之間的轉換。  
  
    4.  任何其他轉換。  
  
 例如，針對查詢 `SELECT * FROM t WHERE [Col_varchar(30)] > @p`，會選擇**Varchar （8000）** ，因為轉換（a）是最佳做法。 針對查詢 `SELECT * FROM t WHERE [Col_char(30)] > @p`，仍然會選擇**Varchar （8000）** ，因為它會導致類型（b）轉換，而且因為另一個選擇（例如**Varchar （4000）** ）會導致類型（d）轉換。  
  
 最後一個範例是，假設查詢 `SELECT NULL + @p`，就會為 \@p 選擇**int** ，因為它會導致類型（c）轉換。  
  
## <a name="permissions"></a>[權限]  
 需要執行 \@tsql 引數的許可權。  
  
## <a name="examples"></a>範例  
 下列範例會傳回未宣告之 `@id` 和 `@name` 參數的預期資料類型相關資訊。  
  
```sql
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR name = @name'  
  
```  
  
 當提供 `@id` 參數做為 `@params` 參考時，結果集中會省略 `@id` 參數，而只描述 `@name` 參數。  
  
```sql
sp_describe_undeclared_parameters @tsql =   
N'SELECT object_id, name, type_desc   
FROM sys.indexes  
WHERE object_id = @id OR NAME = @name',  
@params = N'@id int'  
  
```  
  
## <a name="see-also"></a>請參閱  
 [sp_describe_first_result_set &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [_exec_describe_first_result_set &#40;transact-sql&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)   
 [sys.databases _exec_describe_first_result_set_for_object &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md)
