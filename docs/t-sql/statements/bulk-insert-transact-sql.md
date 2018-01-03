---
title: "BULK INSERT (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 01/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BULK_TSQL
- BULK INSERT
- BULK_INSERT_TSQL
- BULK
dev_langs: TSQL
helpviewer_keywords:
- tables [SQL Server], importing data into
- inserting files
- views [SQL Server], importing data into
- BULK INSERT statement
- views [SQL Server], exporting data from
- importing data, bulk import
- bulk importing [SQL Server], BULK INSERT statement
- file importing [SQL Server]
ms.assetid: be3984e1-5ab3-4226-a539-a9f58e1e01e2
caps.latest.revision: "153"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5900878e440a0ae821655adea764eaebad8fddf2
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2018
---
# <a name="bulk-insert-transact-sql"></a>BULK INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  依照 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用者指定的格式，將資料檔案匯入資料庫資料表或檢視表中  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
BULK INSERT   
   [ database_name . [ schema_name ] . | schema_name . ] [ table_name | view_name ]   
      FROM 'data_file'   
     [ WITH   
    (   
   [ [ , ] BATCHSIZE = batch_size ]   
   [ [ , ] CHECK_CONSTRAINTS ]   
   [ [ , ] CODEPAGE = { 'ACP' | 'OEM' | 'RAW' | 'code_page' } ]   
   [ [ , ] DATAFILETYPE =   
      { 'char' | 'native'| 'widechar' | 'widenative' } ]   
   [ [ , ] DATASOURCE = 'data_source_name' ]
   [ [ , ] ERRORFILE = 'file_name' ]
   [ [ , ] ERRORFILE_DATASOURCE = 'data_source_name' ]   
   [ [ , ] FIRSTROW = first_row ]   
   [ [ , ] FIRE_TRIGGERS ]   
   [ [ , ] FORMATFILE_DATASOURCE = 'data_source_name' ]
   [ [ , ] KEEPIDENTITY ]   
   [ [ , ] KEEPNULLS ]   
   [ [ , ] KILOBYTES_PER_BATCH = kilobytes_per_batch ]   
   [ [ , ] LASTROW = last_row ]   
   [ [ , ] MAXERRORS = max_errors ]   
   [ [ , ] ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) ]   
   [ [ , ] ROWS_PER_BATCH = rows_per_batch ]   
   [ [ , ] ROWTERMINATOR = 'row_terminator' ]   
   [ [ , ] TABLOCK ]   

   -- input file format options
   [ [ , ] FORMAT = 'CSV' ]
   [ [ , ] FIELDQUOTE = 'quote_characters']
   [ [ , ] FORMATFILE = 'format_file_path' ]   
   [ [ , ] FIELDTERMINATOR = 'field_terminator' ]   
   [ [ , ] ROWTERMINATOR = 'row_terminator' ]   
    )]   
```  
  
## <a name="arguments"></a>引數  
 *database_name*  
 這是指定的資料表或檢視表所在的資料庫名稱。 如果未指定，這就是目前的資料庫。  
  
 *schema_name*  
 這是資料表或檢視表結構描述的名稱。 *schema_name*如果執行大量匯入作業之使用者的預設結構描述會指定的資料表或檢視的結構描述是選擇性的。 如果*結構描述*未指定，而且執行大量匯入作業之使用者的預設結構描述指定的資料表或檢視中，從不同[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]傳回錯誤訊息，並在大量匯入作業已取消。  
  
 *table_name*  
 這是要大量匯入資料到其中之資料表或檢視表的名稱。 您只能使用所有資料行都參考相同基底資料表的檢視表。 詳細資料載入到檢視表的限制的詳細資訊，請參閱[INSERT &#40;TRANSACT-SQL &#41;](../../t-sql/statements/insert-transact-sql.md).  
  
 **'** *data_file* **'**  
 這是含有要匯入至指定的資料表或檢視表中之資料的資料檔案完整路徑。 BULK INSERT 可以從磁碟中匯入資料 (其中包括網路、磁碟片、硬碟等)。   
 
 *data_file*必須指定有效的路徑，從伺服器所在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]正在執行。 如果*data_file*是一個遠端檔案中，指定通用命名慣例 (UNC) 名稱。 UNC 名稱有表單\\ \\*系統名稱*\\*ShareName*\\*路徑*\\ *FileName*。 例如， `\\SystemX\DiskZ\Sales\update.txt`。   
**適用於：** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1。   
開頭為[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP1.1，data_file 可保留在 Azure blob 儲存體中。

**'** *data_source_name* **'**   
**適用於：** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1。   
具名的外部資料來源會指向 Azure Blob 儲存體位置，將匯入的檔案。 必須建立外部資料來源，使用`TYPE = BLOB_STORAGE`選項加入[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1。 如需詳細資訊，請參閱[CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)。    
  
 BATCHSIZE  **=**  *batch_size*  
 指定批次中的資料列數。 每個批次都會當做一筆交易複製到伺服器中。 如果失敗，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會認可或回復每個批次的交易。 依預設，指定之資料檔中的所有資料都是單一批次。 如需有關效能考量的詳細資訊，請參閱本主題稍後的「備註」。  
  
 CHECK_CONSTRAINTS  
 指定在大量匯入作業期間，必須檢查目標資料表或檢視表的所有條件約束。 當沒有 CHECK_CONSTRAINTS 選項時，會忽略所有 CHECK 和 FOREIGN KEY 條件約束，而且在作業之後，會將資料表的條件約束標記為不受信任。  
  
> [!NOTE]  
>  一律強制實施 UNIQUE 和 PRIMARY KEY 條件約束。 當匯入到使用 NOT NULL 條件約束所定義的字元資料行中時，BULK INSERT 會在文字檔中沒有任何值時插入空白字串。  
  
 在某個點上，您必須檢查整份資料表的條件約束。 如果在大量匯入作業之前，資料表不是空的，重新驗證條件約束的成本可能會超出在累加資料上套用 CHECK 條件約束的成本。  
  
 如果輸入資料包含違反條件約束的資料列，您可能會想停用條件約束 (預設行為)。 當停用 CHECK 條件約束時，您可以先匯入資料，再利用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式來移除無效的資料。  
  
> [!NOTE]  
>  MAXERRORS 選項不適用於條件約束檢查。  
  
 字碼頁 **=**  { **'**ACP**'** | **'**OEM**'**  | **'**RAW**'** | **'***字碼頁***'** }  
 指定資料檔案中之資料的字碼頁。 字碼頁才會相關的資料包含**char**， **varchar**，或**文字**字元值大於資料行**127**小於或等於比**32**。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]建議您指定在每個資料行的定序名稱[格式檔案](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)。  
  
|CODEPAGE 值|描述|  
|--------------------|-----------------|  
|ACP|資料行的**char**， **varchar**，或**文字**資料型別會從轉換[!INCLUDE[vcpransi](../../includes/vcpransi-md.md)] / [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 字碼頁 (ISO 1252)[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]字碼頁。|  
|OEM (預設值)|資料行的**char**， **varchar**，或**文字**資料型別會從系統 OEM 字碼頁轉換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]字碼頁。|  
|RAW|不進行字碼頁之間的轉換；這是最快的選項。|  
|*code_page*|特定字碼頁編號，如 850。<br /><br /> **\*\*重要\* \*** 之前的版本[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]不支援字碼頁 65001 （utf-8 編碼）。|  
  
 DATAFILETYPE  **=**  { **'char'** | **'native'** | **'widechar'**  |  **'widenative'** }  
 指定 BULK INSERT 利用指定的資料檔案類型值來執行匯入作業。  
  
|DATAFILETYPE 值|所有資料的表示方式如下：|  
|------------------------|------------------------------|  
|**char** （預設值）|字元格式。<br /><br /> 如需詳細資訊，請參閱[使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)。|  
|**原生**|原生 (資料庫) 資料類型。 建立原生資料檔案大量匯入的資料來[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用**bcp**公用程式。<br /><br /> 原生值提供了效能比 char 值更高的替代項。<br /><br /> 如需詳細資訊，請參閱[使用原生格式匯入或匯出資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)。|  
|**widechar**|Unicode 字元。<br /><br /> 如需詳細資訊，請參閱 [使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)。|  
|**widenative**|原生 （資料庫） 資料類型，除非在**char**， **varchar**，和**文字**資料行，會以 Unicode 儲存資料。 建立**widenative**資料檔案大量匯入的資料來[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用**bcp**公用程式。<br /><br /> **Widenative**值提供了較高的效能的替代方案**widechar**。 如果資料檔案會包含[!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]擴充字元，請指定**widenative**。<br /><br /> 如需詳細資訊，請參閱 [使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)。|  
  
  ERRORFILE **='***file_name***'**  
 指定用來收集格式錯誤且無法轉換成 OLE DB 資料列集之資料列的檔案。 這些資料列會「依照原狀」，從資料檔複製到這個錯誤檔中。  
  
 當執行命令時，便會建立這個錯誤檔。 如果檔案已經存在，會發生一則錯誤。 另外，還會建立一個副檔名為 .ERROR.txt 的控制檔。 這會參考錯誤檔中的每個資料列，且會提供錯誤診斷。 錯誤更正之後，就能夠載入資料。   
**適用於：** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1。
開頭為[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]、`error_file_path`可保留在 Azure blob 儲存體中。

' errorfile_data_source_name'   
**適用於：** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1。
具名的外部資料來源會指向 Azure Blob 儲存體的位置將包含匯入期間發現錯誤的檔案時發生錯誤。 必須建立外部資料來源，使用`TYPE = BLOB_STORAGE`選項加入[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1。 如需詳細資訊，請參閱[CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)。
 
 FIRSTROW  **=**  *first_row*  
 指定要載入之第一個資料列的號碼。 預設值是指定之資料檔案中的第一個資料列。 FIRSTROW 是以 1 為基底。  
  
> [!NOTE]  
>  FIRSTROW 屬性不是用來略過資料行標頭。 BULK INSERT 陳述式不支援略過標頭。 如果略過資料列，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 就只會查看欄位結束字元，而且不會驗證已略過之資料列中欄位的資料。  
  
 FIRE_TRIGGERS  
 指定在大量匯入作業期間，執行目的地資料表上所定義的任何插入觸發程序。 如果在目標資料表上定義了 INSERT 作業的觸發程序，便會針對每個已完成的批次引發觸發程序。  
  
 如果未指定 FIRE_TRIGGERS，就不會執行任何插入觸發程序。  

FORMATFILE_DATASOURCE  **=**  'data_source_name'   
**適用於：** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 1.1。   
具名的外部資料來源指向 Azure Blob 儲存體的位置會定義結構描述匯入資料的格式檔案。 必須建立外部資料來源，使用`TYPE = BLOB_STORAGE`選項加入[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1。 如需詳細資訊，請參閱[CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)。
  
 KEEPIDENTITY  
 指定識別欄位要使用匯入之資料檔案中的一個或多個識別值。 如果未指定 KEEPIDENTITY，就會驗證這個資料行的識別值但不會匯入它，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會根據建立資料表期間所指定的種子值和遞增值來自動指派唯一值。 如果資料檔案中沒有資料表或檢視表中之識別欄位的值，請利用格式檔來指定，在匯入資料時略過資料表或檢視表中的識別欄位；[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會自動指派資料行的唯一值。 如需詳細資訊，請參閱 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)。  
  
 如需詳細資訊，請參閱有關保留識別值，請參閱[保留識別值時大量匯入資料 &#40;SQL Server &#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md).  
  
 KEEPNULLS  
 指定在大量匯入作業期間，空白資料行應該保留 Null 值，而不是插入資料行的任何預設值。 如需詳細資訊，請參閱[大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)。  
  
 KILOBYTES_PER_BATCH  **=**  *kilobytes_per_batch*  
 指定的位元組 (KB) 的每個批次為資料的近似數目*kilobytes_per_batch*。 依預設，KILOBYTES_PER_BATCH 是未知的。 如需有關效能考量的詳細資訊，請參閱本主題稍後的「備註」。  
  
 LASTROW**=***last_row*  
 指定要載入之最後一個資料列的號碼。 預設值是 0，表示指定之資料檔案中的最後一個資料列。  
  
 MAXERRORS  **=**  *max_errors*  
 指定取消大量匯入作業之前所允許的資料語法錯誤數目上限。 大量匯入作業所無法匯入的每個資料列都會被忽略，且會當做一項錯誤來計算。 如果*max_errors*未指定，預設值為 10。  
  
> [!NOTE]  
>  MAX_ERRORS 選項不適用於條件約束檢查，或轉換**money**和**bigint**資料型別。  
  
 順序 ({*資料行*[ASC |DESC]} [ **，**...*n* ] )  
 指定如何排序資料檔案中的資料。 如果匯入資料時是依照資料表的叢集索引來排序，將可提升大量匯入的效能。 如果資料檔案是依據不同於叢集索引鍵順序的其他順序來進行排序，或是資料表上沒有任何叢集索引，便會略過 ORDER 子句。 提供的資料行名稱必須是目的地資料表中的有效資料行名稱。 依預設，大量插入作業會假設資料檔案沒有排序。 為了達到最佳的大量匯入效果， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也會驗證匯入的資料是否已排序。  
  
 *n*  
 這是一個預留位置，表示可以指定多個資料行。  
  
 ROWS_PER_BATCH  **=**  *rows_per_batch*  
 指出資料檔案中大約有多少資料列。  
  
 依預設，資料檔案中的所有資料都會當做單一交易來傳給伺服器，而且查詢最佳化工具並不知道批次中的資料列數。 如果您指定 ROWS_PER_BATCH (利用 > 0 的值)，伺服器會利用這個值來最佳化大量匯入作業。 ROWS_PER_BATCH 指定的值應該與實際的資料列數大約相同。 如需有關效能考量的詳細資訊，請參閱本主題稍後的「備註」。  
  
 
 TABLOCK  
 指定在大量匯入作業期間，取得資料表層級鎖定。 如果資料表沒有索引，且指定了 TABLOCK，多個用戶端便可以同時載入這份資料表。 根據預設，鎖定行為是由資料表選項 **table lock on bulk load**所決定。 在大量匯入作業期間保留鎖定，會減少競爭資料表鎖定的情況，在某些情況下，可以大幅提升效能。 如需有關效能考量的詳細資訊，請參閱本主題稍後的「備註」。  
  
 資料行存放區索引。 鎖定行為是不同的因為它在內部分割成多個資料列集。  每個執行緒會以獨佔方式將每個資料列集資料載入所允許的並行資料載入工作階段的平行處理資料載入的資料列集上取得 X 鎖定。 使用 TABLOCK 選項將會導致執行緒進行 （不同於傳統的資料列集的 BU 鎖定） 會造成其他並行執行緒來同時載入資料之資料表上的 X 鎖定。  

### <a name="input-file-format-options"></a>輸入的檔案格式選項
  
格式 **=**  'CSV'   
**適用於：** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1。   
指定逗號分隔的值檔案符合[遵循 RFC 4180](https://tools.ietf.org/html/rfc4180)標準。

FIELDQUOTE  **=**  'field_quote'   
**適用於：** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1。   
指定將用於做為 CSV 檔案中的引號字元的字元。 如果未指定，引號字元 （"） 會用作引號字元如中所定義[遵循 RFC 4180](https://tools.ietf.org/html/rfc4180)標準。
  
 FORMATFILE **='***f***'**  
 指定格式檔的完整路徑。 格式檔案描述資料檔包含由使用預存的回應**bcp**公用程式相同的資料表或檢視。 在下列情況下，應該使用格式檔：  
  
-   資料檔案包含比資料表或檢視表更多或更少的資料行。  
  
-   資料行的順序不同。  
  
-   資料行分隔符號不同。  
  
-   資料格式有其他變更。 格式檔案通常藉由建立**bcp**公用程式和以文字編輯器，視需要修改。 如需相關資訊，請參閱 [bcp Utility](../../tools/bcp-utility.md)。  

**適用於：** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1。   
開頭為[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1 f 可保留在 Azure blob 儲存體中。

 FIELDTERMINATOR **='***field_terminator***'**  
 指定要用於中的欄位結束字元**char**和**widechar**資料檔案。 預設欄位結束字元是 \t (定位字元)。 如需詳細資訊，請參閱 [指定欄位與資料列結束字元 &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)。  

 ROWTERMINATOR **='***row_terminator***'**  
 指定要用於資料列結束字元**char**和**widechar**資料檔案。 預設的資料列結束字元是**\r\n** （換行字元）。  如需詳細資訊，請參閱 [指定欄位與資料列結束字元 &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)。  

  
## <a name="compatibility"></a>相容性  
 對於從檔案中讀取的資料，BULK INSERT 會強制進行嚴格的資料驗證和資料檢查，而當現有的指令碼針對無效資料執行時，這些作業可能會造成指令碼失敗。 例如，BULK INSERT 會驗證：  
  
-   原生表示法**float**或**真實**是有效的資料型別。  
  
-   Unicode 資料的長度是否為偶數位元組。  
  
## <a name="data-types"></a>資料型別  
  
### <a name="string-to-decimal-data-type-conversions"></a>字串到十進位資料類型轉換  
 用於 BULK INSERT 的字串到十進位資料類型轉換，請遵循相同的規則[!INCLUDE[tsql](../../includes/tsql-md.md)][轉換](../../t-sql/functions/cast-and-convert-transact-sql.md)函式，會拒絕代表使用科學記號標記法之數值字串。 因此，BULK INSERT 會將這類字串視為無效的值，並報告轉換錯誤。  
  
 若要解決這個問題，請使用格式檔案大量匯入科學記號標記法**float**到十進位資料行的資料。 在格式檔案中，明確描述做為資料行**真實**或**float**資料。 如需有關這些資料類型的詳細資訊，請參閱[float 和 real &#40;TRANSACT-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
> [!NOTE]  
>  格式檔案代表**真實**資料做為**SQLFLT4**資料型別和**float**資料做為**SQLFLT8**資料型別。 如需非 XML 格式檔案的資訊，請參閱[使用 bcp &#40; 指定檔案儲存類型SQL Server &#41;](../../relational-databases/import-export/specify-file-storage-type-by-using-bcp-sql-server.md).  
  
#### <a name="example-of-importing-a-numeric-value-that-uses-scientific-notation"></a>匯入使用科學記號標記法之數值的範例  
 這個範例使用下列資料表：  
  
```  
CREATE TABLE t_float(c1 float, c2 decimal (5,4));  
```  
  
 使用者想要將大量資料匯入 `t_float` 資料表中。 資料檔案 C:\t_float-c.dat 包含科學記號標記法**float**資料; 例如：  
  
```  
8.0000000000000002E-28.0000000000000002E-2  
```  
  
 不過，BULK INSERT 無法直接將此資料匯入 `t_float` 中，因為它的第二個資料行 `c2` 使用 `decimal` 資料類型。 因此，格式檔案是必要的。 格式檔案必須對應科學記號標記法**float**十進位格式的資料行的資料`c2`。  
  
 下列格式檔案使用 `SQLFLT8` 資料類型，將第二個資料欄位對應到第二個資料行：  
  
 ```
 <?xml version="1.0"?> 
 <BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> 
 <RECORD> 
 <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="30"/> 
 <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="30"/>  </RECORD>  <ROW> 
 <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLFLT8"/> 
 <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLFLT8"/>  </ROW> </BCPFORMAT> 
 ```
  
 若要使用此格式檔案 (使用檔案名稱 `C:\t_floatformat-c-xml.xml`) 將測試資料匯入測試資料表，請發出下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：  
  
```  
BULK INSERT bulktest..t_float  
FROM 'C:\t_float-c.dat' WITH (FORMATFILE='C:\t_floatformat-c-xml.xml');  
GO  
```  
  
### <a name="data-types-for-bulk-exporting-or-importing-sqlxml-documents"></a>大量匯出或匯入 SQLXML 文件的資料類型  
 若要大量匯出或匯入 SQLXML 資料，請在格式檔案中使用下列其中一種資料類型：  
  
|資料類型|效果|  
|---------------|------------|  
|SQLCHAR 或 SQLVARCHAR|資料是使用用戶端字碼頁或定序所隱含的字碼頁所傳送。 其效果等同於指定 DATAFILETYPE **= 'char'**但不指定格式檔案。|  
|SQLNCHAR 或 SQLNVARCHAR|以 Unicode 格式傳送這份資料。 其效果等同於指定 DATAFILETYPE **= 'widechar'**但不指定格式檔案。|  
|SQLBINARY 或 SQLVARBIN|未經任何轉換即傳送這份資料。|  
  
## <a name="general-remarks"></a>一般備註  
 如需 BULK INSERT 陳述式、INSERT ...選取\*從 （bulk...） 陳述式，而**bcp**命令，請參閱[大量匯入和匯出資料 &#40;SQL Server &#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 有關準備資料進行大量匯入的詳細資訊，請參閱[準備的資料大量匯出或匯入 &#40;SQL Server &#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 您可以在使用者定義交易內部執行 BULK INSERT 陳述式，以便將資料匯入資料表或檢視表。 (選擇性) 若要針對大量匯入資料使用多重比對，交易可以在 BULK INSERT 陳述式中指定 BATCHSIZE 子句。 如果多重批次交易已回復，交易已經傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的每個批次都會回復。  
  
## <a name="interoperability"></a>互通性  
  
### <a name="importing-data-from-a-csv-file"></a>從 CSV 檔案匯入資料  
開頭為[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1、 BULK INSERT 支援 CSV 格式。  
之前[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]CTP 1.1 版中，以逗號分隔值 (CSV) 檔案不會受到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]大量匯入作業。 不過，在某些情況下，CSV 檔案可用來當做資料檔案，以便將資料大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 從 CSV 資料檔匯入資料之需求的相關資訊，請參閱[準備的資料大量匯出或匯入 &#40;SQL Server &#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
## <a name="logging-behavior"></a>記錄行為  
 如需大量匯入所執行的資料列插入作業於何時記錄到交易記錄的資訊，請參閱[大量匯入採用最低限度記錄的必要條件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)。  
  
##  <a name="Limitations"></a> 限制  
 使用格式檔案搭配 BULK INSERT 時，最多只能指定 1024 個欄位。 這與資料表中允許的資料行數目上限相同。 如果您使用 BULK INSERT 搭配包含超過 1024 個欄位的資料檔案，則 BULK INSERT 會產生 4822 錯誤。 [Bcp 公用程式](../../tools/bcp-utility.md)沒有這項限制，因此，針對包含超過 1024 個欄位的資料檔案，使用**bcp**命令。  
  
## <a name="performance-considerations"></a>效能考量  
 如果要在單一批次中排清的頁數超出內部臨界值，可能會發生緩衝集區的完整掃描，以識別批次認可時要排清的頁面。 這個完整掃描可能會損及大量匯入效能。 當大型緩衝集區與緩慢的 I/O 子系統結合時，可能會超出內部臨界值。 為避免大型電腦發生緩衝區溢位，請不要使用 TABLOCK 提示 (將會移除大量最佳化) 或使用較小的批次大小 (可保留大量最佳化)。  
  
 電腦會不斷變化，因此，我們建議您利用您的資料負荷量測試各種批次大小來找出最適合您的狀況。  
  
## <a name="security"></a>Security  
  
### <a name="security-account-delegation-impersonation"></a>委派安全性帳戶 (模擬)  
 如果使用者是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，則會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序帳戶的安全性設定檔。 使用 SQL Server 驗證的登入無法於 Database Engine 外部進行驗證。 因此，一旦使用 SQL Server 驗證的登入起始 BULK INSERT 命令，將會使用 SQL Server 處理序帳戶 (即 SQL Server Database Engine 服務所使用的帳戶) 的安全性內容建立與資料的連接。 為了能夠成功讀取來源資料，您必須授與 SQL Server Database Engine 所使用的帳戶對來源資料的存取權。相反地，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者是使用 Windows 驗證登入，則該使用者只能讀取其使用者帳戶可存取的檔案，而與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序的安全性設定檔無關。  
  
 執行 BULK INSERT 陳述式使用時**sqlcmd**或**osql**，從一部電腦，將資料插入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上第二部電腦，並指定*data_file*第三個在電腦上使用 UNC 路徑，您可能會收到 4861 錯誤。  
  
 若要解決這個錯誤，請使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證，並指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用的安全性設定檔的登入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]處理序帳戶，或設定 Windows 來啟用安全性帳戶委派。 如需有關如何使某個使用者帳戶受到信任而委派的詳細資訊，請參閱 Windows 說明。  
  
 如需有關這個主題以及使用 BULK INSERT 其他安全性考量的詳細資訊，請參閱[使用 BULK INSERT 或 OPENROWSET &#40; 匯入大量資料BULK_ &#41;&#40;SQL Server &#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="permissions"></a>Permissions  
 需要 INSERT 和 ADMINISTER BULK OPERATIONS 權限。 另外，如果以下一個或多個狀況成立，則需要 ALTER TABLE 權限：  
  
-   有條件約束存在而且未指定 CHECK_CONSTRAINTS 選項。  
  
    > [!NOTE]  
    >  停用條件約束是預設行為。 若要明確檢查條件約束，請使用 CHECK_CONSTRAINTS 選項。  
  
-   有觸發程序存在而且未指定 FIRE_TRIGGER 選項。  
  
    > [!NOTE]  
    >  依預設不會引發觸發程序。 若要明確引發觸發程序，請使用 FIRE_TRIGGER 選項。  
  
-   您利用 KEEPIDENTITY 選項，從資料檔案中匯入識別值。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-pipes-to-import-data-from-a-file"></a>A. 利用垂直線來匯入檔案資料  
 下列範例利用垂直線 (`AdventureWorks2012.Sales.SalesOrderDetail`) 做為欄位結束字元，並利用 `|` 做為資料列結束字元，從指定的資料檔中，將訂單詳細資訊匯入 `|\n` 資料表中。  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM 'f:\orders\lineitem.tbl'  
   WITH   
      (  
         FIELDTERMINATOR =' |',  
         ROWTERMINATOR =' |\n'  
      );  
```  
  
### <a name="b-using-the-firetriggers-argument"></a>B. 使用 FIRE_TRIGGERS 觸發程序  
 下列範例指定 `FIRE_TRIGGERS` 引數。  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM 'f:\orders\lineitem.tbl'  
   WITH  
     (  
        FIELDTERMINATOR =' |',  
        ROWTERMINATOR = ':\n',  
        FIRE_TRIGGERS  
      );  
```  
  
### <a name="c-using-line-feed-as-a-row-terminator"></a>C. 利用換行字元做為資料列結束字元  
 下列範例利用換行字元做為資料列結束字元來匯入檔案，如 UNIX 輸出：  
  
```  
DECLARE @bulk_cmd varchar(1000);  
SET @bulk_cmd = 'BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
FROM ''<drive>:\<path>\<filename>''   
WITH (ROWTERMINATOR = '''+CHAR(10)+''')';  
EXEC(@bulk_cmd);  
```  
  
> [!NOTE]  
>  由於 Microsoft Windows 如何處理文字檔**(\n**自動取得取代**\r\n)**。  
  
### <a name="d-specifying-a-code-page"></a>D. 指定字碼頁  
 下列範例會示範如何指定字碼頁。  
  
```  
BULK INSERT MyTable  
FROM 'D:\data.csv'  
WITH  
( CODEPAGE = '65001',  
    DATAFILETYPE = 'char',  
    FIELDTERMINATOR = ','  
);  
```  
### <a name="e-importing-data-from-a-csv-file"></a>E. 從 CSV 檔案匯入資料   
下列範例顯示如何指定 CSV 檔案。   
```
BULK INSERT Sales.Invoices
FROM '\\share\invoices\inv-2016-07-25.csv'
WITH (FORMAT = 'CSV'); 
```

### <a name="f-importing-data-from-a-file-in-azure-blob-storage"></a>F. 從 Azure blob 儲存體中的檔案匯入資料   
下列範例會示範如何從 csv 檔案，在 Azure blob 儲存體位置中，已設定為外部資料來源載入資料。 這需要使用資料庫範圍認證使用共用的存取簽章。    

```sql
BULK INSERT Sales.Invoices
FROM 'inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoices',
     FORMAT = 'CSV'); 
```

對於完成`BULK INSERT`範例包括設定認證和外部資料來源，請參閱[範例的大量資料的存取 Azure Blob 儲存體](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md)。
  
### <a name="additional-examples"></a>其他範例  
 其他`BULK INSERT`中的下列主題提供範例：  
  
-   [大量匯入與匯出 XML 文件的範例 &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [大量匯入資料時保留識別值 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [指定欄位與資料列結束字元 &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [使用格式檔案大量匯入資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [使用字元格式匯入或匯出資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [使用原生格式匯入或匯出資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [使用 Unicode 字元格式匯入或匯出資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [使用 Unicode 原生格式匯入或匯出資料 &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [使用格式檔案略過資料表資料行 &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>請參閱  
 [資料的大量匯入及匯出 &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [bcp 公用程式](../../tools/bcp-utility.md)   
 [匯入或匯出資料 &#40; 的格式檔案SQL Server &#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [準備大量匯出或匯入 &#40; 的資料SQL Server &#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)   
 [sp_tableoption &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
