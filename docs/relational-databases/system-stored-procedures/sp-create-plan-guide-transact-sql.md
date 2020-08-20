---
description: sp_create_plan_guide (Transact-SQL)
title: sp_create_plan_guide (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_create_plan_guide
- sp_create_plan_guide_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_create_plan_guide
ms.assetid: 5a8c8040-4f96-4c74-93ab-15bdefd132f0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0595885b12cc70d5634058eeb9650ee323921ba5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489526"
---
# <a name="sp_create_plan_guide-transact-sql"></a>sp_create_plan_guide (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  建立將查詢提示或實際查詢計畫關聯於資料庫中查詢的計畫指南。 如需有關計畫指南的詳細資訊，請參閱 [計畫指南](../../relational-databases/performance/plan-guides.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
sp_create_plan_guide [ @name = ] N'plan_guide_name'  
    , [ @stmt = ] N'statement_text'  
    , [ @type = ] N'{ OBJECT | SQL | TEMPLATE }'  
    , [ @module_or_batch = ]  
      {   
                    N'[ schema_name. ] object_name'  
        | N'batch_text'  
        | NULL  
      }  
    , [ @params = ] { N'@parameter_name data_type [ ,...n ]' | NULL }   
    , [ @hints = ] { N'OPTION ( query_hint [ ,...n ] )'   
                 | N'XML_showplan'  
                 | NULL }  
```  
  
## <a name="arguments"></a>引數  
 [ \@ name =] N '*plan_guide_name*'  
 計畫指南的名稱。 計畫指南名稱僅限於目前的資料庫。 *plan_guide_name* 必須符合 [識別碼](../../relational-databases/databases/database-identifiers.md) 的規則，且開頭不能是數位記號 ( # ) 。 *Plan_guide_name*的長度上限為124個字元。  
  
 [ \@ stmt =] N '*statement_text*'  
 這是建立計畫指南所針對的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。 當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢最佳化工具辨識出符合 *statement_text*的查詢時， *plan_guide_name* 會生效。 若要成功建立計劃指南， *statement_text* 必須出現在 \@ type、 \@ module_or_batch 和 params 參數所指定的內容中 \@ 。  
  
 您必須提供*statement_text* ，讓查詢最佳化工具將它與 \@ module_or_batch 和 params 所識別的批次或模組中提供的對應語句相符 \@ 。 如需詳細資訊，請參閱＜備註＞一節。 *Statement_text*的大小只受限於伺服器的可用記憶體。  
  
 [ \@ type =] N ' {OBJECT |SQL |範本} '  
 這是在其中顯示 *statement_text* 的實體類型。 這會指定要*plan_guide_name*之相符*statement_text*的內容。  
  
 OBJECT  
 指出 *statement_text* 會出現在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 目前資料庫中的預存程式、純量函數、多重語句資料表值函數或 DML 觸發程式的內容中 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。  
  
 SQL  
 指出 *statement_text* 會出現在可以透過任何機制提交給之獨立語句或批次的內容中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [!INCLUDE[tsql](../../includes/tsql-md.md)] common language runtime (CLR) 物件或擴充預存程式，或使用 EXEC N '*sql_string*' 提交的語句，在伺服器上會以批次方式處理，因此應該識別為 \@ 類型 **=** ' sql '。 如果指定 SQL，查詢提示參數化 {強制 |SIMPLE} 無法在 \@ 提示參數中指定。  
  
 TEMPLATE  
 指出計劃指南適用于參數化至 *statement_text*中指定之表單的任何查詢。 如果指定了 TEMPLATE，則只會參數化 {強制 |SIMPLE} 查詢提示可以在 \@ 提示參數中指定。 如需有關範本計劃指南的詳細資訊，請參閱 [使用計劃指南指定查詢參數化行為](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)。  
  
 [ \@ module_or_batch =] {N ' [ *schema_name*。 ] *object_name*' |N '*batch_text*' |;  
 指定出現 *statement_text* 的物件名稱，或 *statement_text* 出現的批次文字。 批次文字不能包含 USE*database* 語句。  
  
 若要讓計劃指南比對從應用程式提交的批次， *batch_tex*t 必須以與提交給時相同的格式（字元）來提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 不會執行內部轉換來簡化這個比對作業。 如需詳細資訊，請參閱＜備註＞一節。  
  
 [*schema_name*]。*object_name*指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 包含 statement_text 之預存程式、純量函數、多重語句資料表值函數或 [!INCLUDE[tsql](../../includes/tsql-md.md)] DML 觸發程式的*statement_text*名稱。 如果未指定 *schema_name* ， *schema_name* 會使用目前使用者的架構。 如果指定 Null 且 \@ type = ' SQL '，module_or_batch 的值 \@ 會設定為 stmt 的值 \@ 。如果 \@ type = ' TEMPLATE **\'** ， \@ MODULE_OR_BATCH 必須是 Null。  
  
 [ \@ params =] {N '* \@ parameter_name data_type* [，*.。。n* ] ' |;  
 指定內嵌于 *statement_text*之所有參數的定義。 \@只有在下列其中一項為真時，才適用參數：  
  
-   \@type = ' SQL ' 或 ' TEMPLATE '。 若為 ' TEMPLATE '，則 \@ params 不得為 Null。  
  
-   使用 sp_executesql 提交*statement_text* ，並 \@ 指定 params 參數的值，或在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 參數化之後內部提交語句。 來自資料庫 API (包括 ODBC、OLE DB 及 ADO.NET) 參數化查詢的提交對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而言，視同對 sp_executesql 或對 API 伺服器資料指標常式的呼叫；因此，也可以由 SQL 或 TEMPLATE 計畫指南進行比對。  
  
 * \@ parameter_name 的 data_type*必須以與提交至的格式完全相同，因為它會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 sp_executesql 或在參數化之後在內部提交。 如需詳細資訊，請參閱＜備註＞一節。 如果批次不包含參數，就必須指定 NULL。 參數的大小 \@ 只受限於可用的伺服器記憶體。  
  
 [ \@ 提示 =] {N'OPTION (*query_hint* [，*.。。n* ] ) ' |N '*XML_showplan*' |;  
 N'OPTION (*query_hint* [，*.。。n* ] )   
 指定要附加至符合 stmt 之查詢的 OPTION 子句 \@ 。 \@提示的語法必須與 SELECT 語句中的 OPTION 子句相同，而且可以包含任何有效的查詢提示順序。  
  
 N '*XML_showplan*'  
 要套用為提示之 XML 格式的查詢計畫。  
  
 建議將 XML 執行程序表指派給變數；否則，您必須在單引號前加上另一個單引號，以免除執行程序表中的所有單引號。 請參閱範例 E。  
  
 NULL  
 表示在查詢之 OPTION 子句中指定的任何現有提示沒有套用到查詢中。 如需詳細資訊，請參閱 [&#40;transact-sql&#41;的 OPTION 子句 ](../../t-sql/queries/option-clause-transact-sql.md)。  
  
## <a name="remarks"></a>備註  
 sp_create_plan_guide 的引數必須依照顯示順序提供。 當您提供 **sp_create_plan_guide**的參數值時，必須明確指定所有的參數名稱，或是完全不指定。 例如，如果指定** \@ name =** ，則也必須指定** \@ stmt =** 、 ** \@ type =** 等等。 同樣地，如果省略** \@ name =** ，而且只提供參數值，則還必須省略其餘的參數名稱，並只提供它們的值。 引數名稱僅供描述用途，以協助您了解語法。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會驗證指定的參數名稱是否與使用該名稱之位置中的參數名稱相符。  
  
 您可以針對相同的查詢和批次或模組，建立一個以上的 OBJECT 或 SQL 計畫指南。 但是，在任何指定的時間內，只能啟用一個計畫指南。  
  
 如果 \@ module_or_batch 值參考的預存程式、函數或 DML 觸發程式指定了 WITH ENCRYPTION 子句或是暫時性的，則無法為該值建立 OBJECT 類型的計劃指南。  
  
 試圖卸除或修改計畫指南所參考的函數、預存程序或 DML 觸發程序，不論是已啟用或已停用，都會造成錯誤。 嘗試卸除定義了觸發程序且被計畫指南參考的資料表也會造成錯誤。  
  
> [!NOTE]
> 並非每個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都可使用計劃指南。 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本支援的功能清單，請參閱 [SQL Server 2016 版本支援的功能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)。 在任何版本中都可以看到計畫指南。 您也可以將包含計畫指南的資料庫附加到任何版本中。 當您將資料庫還原或附加至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的升級版本時，計畫指南仍維持不變。 您應該在執行伺服器升級後確認每個資料庫中計畫指南的符合度。  
  
## <a name="plan-guide-matching-requirements"></a>計劃指南符合需求  
 針對指定 \@ type = ' SQL ' 或 \@ type = ' TEMPLATE ' 以成功符合查詢的計劃指南， *batch_text*和 parameter_name 的值* \@ data_type* [，*.。。n* ] 所提供的格式必須與應用程式所提交的對應專案完全相同。 這表示您提供的批次文字必須和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 編譯器所收到的完全相同。 若要擷取實際的批次和參數文字，您可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]。 如需詳細資訊，請參閱 [使用 SQL Server Profiler 建立和測試計劃指南](../../relational-databases/performance/use-sql-server-profiler-to-create-and-test-plan-guides.md)。  
  
 當 \@ type = ' SQL ' 且 \@ module_or_batch 設定為 Null 時，module_or_batch 的值 \@ 會設定為 stmt 的值 \@ 。這表示 *statement_text* 的值必須與提交的格式完全相同，以字元為字元 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 不會執行內部轉換來簡化這個比對作業。  
  
 當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 符合*statement_text*的值與*batch_text*和* \@ parameter_name data_type* [，*.。。n* ] 或如果 \@ type = **\'** OBJECT ' 到*object_name*內對應查詢的文字，則不會考慮下列字串元素：  
  
-   字串內部的空白字元 (定位字元、空格字元、歸位字元或換行字元)。  
  
-   批註 (**--** 或 **/\*   \*/**) 。  
  
-   行尾的分號。  
  
 例如， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以將 *statement_text* 字串符合 `N'SELECT * FROM T WHERE a = 10'` 下列 *batch_text*：  
  
 ```
 N'SELECT *
 FROM T
 WHERE a = 10' 
 ```
 
 不過，相同的字串不會與這個 *batch_text*相符：  
  
 `N'SELECT * FROM T WHERE b = 10'`  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會忽略第一項查詢內的歸位字元、換行字元和空白字元。 在第二項查詢中，順序 `WHERE b = 10` 的解譯與 `WHERE a = 10` 不同。 比對作業會區分大小寫以及區分腔調字 (即使資料庫定序不區分大小寫亦然)，關鍵字例外，它不區分大小寫。 比對作業不區分縮寫格式的關鍵字。 例如，關鍵字 `EXECUTE`、`EXEC` 和 `execute` 被視為相同。  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a>計畫快取的計劃指南效果  
 針對某個模組建立計畫指南時，就會從計畫快取中移除該模組的查詢計畫。 針對某個批次建立 OBJECT 或 SQL 類型的計畫指南時，就會移除具有相同雜湊值之批次的查詢計畫。 建立 TEMPLATE 類型的計畫指南時，就會從該資料庫內部的計畫快取中移除所有單一陳述式批次。  
  
## <a name="permissions"></a>權限  
 若要建立 OBJECT 類型的計劃指南，需要所 `ALTER` 參考物件的許可權。 若要建立類型為 SQL 或 TEMPLATE 的計劃指南，需要 `ALTER` 目前資料庫的許可權。  
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-plan-guide-of-type-object-for-a-query-in-a-stored-procedure"></a>A. 為預存程序中的查詢建立類型為 OBJECT 的計畫指南  
 下列範例會建立與應用程式型預存程序的內容中執行的查詢相符的計畫指南，並將 `OPTIMIZE FOR` 提示套用至這項查詢。  
  
 以下是預存程序：  
  
```sql  
IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
    DROP PROCEDURE Sales.GetSalesOrderByCountry;  
GO  
CREATE PROCEDURE Sales.GetSalesOrderByCountry   
    (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h   
    INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
    INNER JOIN Sales.SalesTerritory AS t   
        ON c.TerritoryID = t.TerritoryID  
    WHERE t.CountryRegionCode = @Country_region;  
END  
GO  
```  
  
 以下是預存程序中查詢所建立的計畫指南：  
  
```sql  
EXEC sp_create_plan_guide   
    @name =  N'Guide1',  
    @stmt = N'SELECT *  
              FROM Sales.SalesOrderHeader AS h   
              INNER JOIN Sales.Customer AS c   
                 ON h.CustomerID = c.CustomerID  
              INNER JOIN Sales.SalesTerritory AS t   
                 ON c.TerritoryID = t.TerritoryID  
              WHERE t.CountryRegionCode = @Country_region',  
    @type = N'OBJECT',  
    @module_or_batch = N'Sales.GetSalesOrderByCountry',  
    @params = NULL,  
    @hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
### <a name="b-creating-a-plan-guide-of-type-sql-for-a-stand-alone-query"></a>B. 為獨立的查詢建立類型為 SQL 的計畫指南  
 下列範例會建立計畫指南來與使用 sp_executesql 系統預存程序的應用程式所提交批次中的查詢比對。  
  
 批次如下：  
  
```sql  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 若要防止這項查詢產生平行執行計畫，請建立下列計畫指南：  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'Guide1',   
    @stmt = N'SELECT TOP 1 *   
              FROM Sales.SalesOrderHeader   
              ORDER BY OrderDate DESC',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = N'OPTION (MAXDOP 1)';  
```  
  
### <a name="c-creating-a-plan-guide-of-type-template-for-the-parameterized-form-of-a-query"></a>C. 為參數化格式的查詢建立類型為 TEMPLATE 的計畫指南  
 下列範例會建立與參數化為特定格式的任何查詢相符的計畫指南，並導引 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以強制執行查詢的參數化作業。 下列兩項查詢在語法上相同，不同的只是兩者的常數值。  
  
```sql  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 以下是參數化格式查詢的計畫指南：  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 在前一個範例中， `@stmt` 參數的值是參數化格式的查詢。 取得這個值以便於 sp_create_plan_guide 中使用的唯一可靠方法，是利用 [sp_get_query_template](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md) 系統預存程序。 下列指令碼可以用來取得參數化查詢，之後再建立參數化查詢的計畫指南。  
  
```sql  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  傳送到 sp_get_query_template 之 `@stmt` 參數中的常數常值，可能會影響針對取代常值的參數所選擇的資料類型。 這會影響計畫指南的比對作業。 您可能需要建立一份以上的計畫指南，來處理不同的參數值範圍。  
  
### <a name="d-creating-a-plan-guide-on-a-query-submitted-by-using-an-api-cursor-request"></a>D. 建立藉由使用 API 資料指標要求來提交查詢的計畫指南  
 計畫指南可以比對從 API 伺服器資料指標常式提交的查詢。 這些常式包括 sp_cursorprepare、sp_cursorprepexec 和 sp_cursoropen。 使用 ADO、OLE DB 和 ODBC API 的應用程式經常會利用 API 伺服器資料指標與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 互動。 透過檢視 RPC:Starting Profiler 追蹤事件，您可以看見 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤中的 API 伺服器資料指標常式的叫用。  
  
 假設下列資料出現在您想以計畫指南調整之查詢的 RPC:Starting Profiler 追蹤事件中：  
  
```sql  
DECLARE @p1 int;  
SET @p1=-1;  
DECLARE @p2 int;  
SET @p2=0;  
DECLARE @p5 int;  
SET @p5=4104;  
DECLARE @p6 int;  
SET @p6=8193;  
DECLARE @p7 int;  
SET @p7=0;  
EXEC sp_cursorprepexec @p1 output,@p2 output,N'@P1 varchar(255),@P2 varchar(255)',N'SELECT * FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID WHERE h.OrderDate BETWEEN @P1 AND @P2',@p5 OUTPUT,@p6 OUTPUT,@p7 OUTPUT,'20040101','20050101'  
SELECT @p1, @p2, @p5, @p6, @p7;  
```  
  
 您注意到對 `SELECT` 的呼叫中 `sp_cursorprepexec` 查詢的計畫，是使用合併聯結，但您卻想要使用雜湊聯結。 將利用 `sp_cursorprepexec` 提交的查詢參數化，包括查詢字串和參數字串。 透過使用與對 `sp_cursorprepexec` 呼叫中完全相同的查詢和參數字串 (逐字元顯示)，您可以建立下列計畫指南來變更計畫的選擇。  
  
```sql  
EXEC sp_create_plan_guide   
    @name = N'APICursorGuide',  
    @stmt = N'SELECT * FROM Sales.SalesOrderHeader AS h   
              INNER JOIN Sales.SalesOrderDetail AS d   
                ON h.SalesOrderID = d.SalesOrderID   
              WHERE h.OrderDate BETWEEN @P1 AND @P2',  
    @type = N'SQL',  
    @module_or_batch = NULL,  
    @params = N'@P1 varchar(255),@P2 varchar(255)',  
    @hints = N'OPTION(HASH JOIN)';  
```  
  
 這個應用程式對這項查詢的後續執行，將受到這份計畫指南的影響，且會利用雜湊聯結來處理查詢。  
  
### <a name="e-creating-a-plan-guide-by-obtaining-the-xml-showplan-from-a-cached-plan"></a>E. 從快取計畫取得 XML 執行程序表，以建立計畫指南  
 下列範例會針對簡單的特定 SQL 陳述式建立計畫指南。 直接以 `@hints` 參數指定查詢的 XML 執行程序表，就可以在計畫指南中提供此陳述式所需的查詢計畫。 此範例會先執行 SQL 陳述式以便在計畫快取中產生計畫。 基於此範例的目的，假設產生的計畫為所需的計畫，而且不需要額外調整查詢。 查詢的 XML 執行程序表會透過查詢 `sys.dm_exec_query_stats`、 `sys.dm_exec_sql_text`和 `sys.dm_exec_text_query_plan` 動態管理檢視取得，而且會被指派給 `@xml_showplan` 變數。 然後，系統會將 `@xml_showplan` 變數傳遞到 `sp_create_plan_guide` 參數的 `@hints` 陳述式中。 或者，您可以使用 [sp_create_plan_guide_from_handle](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md) 預存程序，從計畫快取的查詢計劃中建立計劃指南。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints =@xml_showplan;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [計劃指南](../../relational-databases/performance/plan-guides.md)   
 [sp_control_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)   
 [sys.plan_guides &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)   
 [&#40;Transact-sql&#41;的資料庫引擎預存程式 ](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [&#40;Transact-sql&#41;的系統預存程式 ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys. dm_exec_sql_text &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [sys. dm_exec_query_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)   
 [sys. fn_validate_plan_guide &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md)   
 [sp_get_query_template &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md)  
  
  
