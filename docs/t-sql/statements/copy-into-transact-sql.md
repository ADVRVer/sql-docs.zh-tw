---
title: COPY INTO (Transact-SQL) (預覽)
titleSuffix: (SQL Data Warehouse) - SQL Server
description: 在 Azure SQL 資料倉儲中使用 COPY 陳述式，從外部儲存體帳戶載入。
ms.date: 11/07/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COPY_TSQL
- COPY INTO
- COPY
- LOAD
dev_langs:
- TSQL
author: kevinvngo
ms.author: kevin
monikerRange: =sqlallproducts-allversions||=azure-sqldw-latest
ms.openlocfilehash: fc26cc0862c7dfb02276738d9424b860d98644e7
ms.sourcegitcommit: 619917a0f91c8f1d9112ae6ad9cdd7a46a74f717
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "73882420"
---
# <a name="copy-transact-sql-preview"></a>COPY (Transact-SQL) (預覽)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

本文說明如何在 Azure SQL 資料倉儲中使用 COPY 陳述式，從外部儲存體帳戶載入。 COPY 陳述式提供最大的彈性，可將高輸送量資料擷取到 SQL 資料倉儲中。

> [!NOTE]  
> COPY 陳述式目前處於公開預覽階段。

## <a name="syntax"></a>語法  

```
COPY INTO [schema.]table_name
[(Column_list)] 
FROM ‘<external_location>’ [,...n]
WITH  
 ( 
 [FILE_TYPE = {'CSV' | 'PARQUET' | 'ORC'} ]
 [,FILE_FORMAT = EXTERNAL FILE FORMAT OBJECT ]  
 [,CREDENTIAL = (AZURE CREDENTIAL) ]
 [,ERRORFILE = '[http(s)://storageaccount/container]/errorfile_directory[/]] 
 [,ERRORFILE_CREDENTIAL = (AZURE CREDENTIAL) ]
 [,MAXERRORS = max_errors ] 
 [,COMPRESSION = { 'Gzip' | 'DefaultCodec'|’Snappy’}] 
 [,FIELDQUOTE = ‘string_delimiter’] 
 [,FIELDTERMINATOR =  ‘field_terminator’]  
 [,ROWTERMINATOR = ‘row_terminator’]
 [,FIRSTROW = first_row]
 [,DATEFORMAT = ‘date_format’] 
 [,ENCODING = {'UTF8'|'UTF16'}] 
 [,IDENTITY_INSERT = {‘ON’ | ‘OFF’}]
)
```

## <a name="arguments"></a>引數  

*schema_name*  
如果執行作業之使用者的預設結構描述是指定之資料表的結構描述，則是選擇性的。 如果未指定*結構描述*，且執行 COPY 作業之使用者的預設結構描述與指定的資料表不同，則會取消 COPY，而且會傳回錯誤訊息。  

*table_name*  
這是要將資料 COPY 到其中之資料表的名稱。 目標資料表可以是暫存資料表或永久資料表。

*(column_list)*  
這是一或多個資料行的選擇性清單，可用來將來源資料欄位對應至目標資料表資料行，以載入資料。 *column_list* 必須以括弧括住，並以逗號分隔。 資料行清單採用以下格式：

[(Column_name [Default_value] [Field_number] [,...n])]

- *Column_name* - 目標資料表中資料行的名稱。
- *Default_value* - 將取代輸入檔中任何NULL 值的預設值。 預設值適用於所有檔案格式。 當資料行清單中省略某個資料行時，或者有空白的輸入檔欄位時，COPY 將會嘗試從輸入檔載入 NULL。
- *Field_number* - 將對應至目標資料行名稱的輸入檔欄位編號。
- 欄位索引會從 1 開始。

未指定資料行清單時，COPY 將會根據來源和目標序數來對應資料行：輸入欄位 1 將會移至目標資料行 1、欄位 2 則會移至資料行 2，以此類推。

*外部位置*</br>
這是包含資料的檔案暫存之處。 目前支援 Azure Data Lake Storage (ADLS) Gen2 和 Azure Blob 儲存體：

- Blob 儲存體的*外部位置*： https://<account>.blob.core.windows.net/<container>/<path>
- ADLS Gen2 的*外部位置*： https://<account>. dfs.core.windows.net/<container>/<path>

> [!NOTE]  
> Blob 端點適用於 ADLS Gen2，而且僅供回溯相容性之用。 將 **dfs** 端點用於 ADLS Gen2 以獲得最佳效能。

- *帳戶* - 儲存體帳戶名稱

- *容器* - Blob 容器名稱

- *路徑* - 資料的資料夾或檔案路徑。 位置會從容器開始。 如果已指定資料夾，COPY 將會從資料夾及其所有子資料夾中擷取所有檔案。 COPY 會忽略隱藏的資料夾，而且除非在路徑中明確地指定，否則不會傳回開頭為底線 (_) 或句號 (.) 的檔案。 即使在使用萬用字元指定路徑時，此行為也是相同的。

萬用字元可以包含在路徑中，其中

- 萬用字元路徑名稱比對會區分大小寫
- 萬用字元可以使用反斜線字元 (\\) 逸出
- 萬用字元展開會以遞迴方式套用。 例如，Customer1 下的所有 CSV 檔案 (包括 Customer1 的子目錄) 都會在下列範例中載入：‘Account/Container/Customer1/*.csv’

> [!NOTE]  
> 為獲得最佳效能，請避免指定會擴展到大量檔案的萬用字元。 如果可能，請列出多個檔案位置，而不是指定萬用字元。

您只能透過逗號分隔清單，從相同的儲存體帳戶和容器中指定多個檔案位置，例如：

- ‘ https://<account>.blob.core.windows.net/<container>/<path>’, ‘ https://<account>.blob.core.windows.net/<container>/<path>’…

*FILE_TYPE = { ‘CSV’ | ‘PARQUET’ | ‘ORC’ }*</br>
*FILE_TYPE* 會指定外部資料的格式。

- CSV：指定符合 [RFC 4180](https://tools.ietf.org/html/rfc4180) 標準的逗號分隔值檔案。
- PARQUET：指定 Parquet 格式。
- ORC：指定 Optimized Row Columnar (ORC) 格式。

>[!NOTE]  
> Polybase 中的檔案類型「分隔符號文字」已由 ' CSV ' 檔案格式所取代，其中預設的逗號分隔符號可以透過 FIELDTERMINATOR 參數設定。 

*FILE_FORMAT = external_file_format_name*</br>
*FILE_FORMAT* 僅適用於 Parquet 和 ORC 檔案，而且會指定儲存外部資料檔案類型和壓縮方法的外部檔案格式物件名稱。 若要建立外部檔案格式，請使用 [CREATE EXTERNAL FILE FORMAT](create-external-file-format-transact-sql.md?view=azure-sqldw-latest)。

*CREDENTIAL (IDENTITY = ‘’, SECRET = ‘’)*</br>
*CREDENTIAL* 會指定存取外部儲存體帳戶的驗證機制。 驗證方法為：

|                          |                CSV                |              Parquet              |                ORC                |
| :----------------------: | :-------------------------------: | :-------------------------------: | :-------------------------------: |
|  **Azure Blob 儲存體**  | SAS/MSI/SERVICE PRINCIPAL/KEY/AAD |              SAS/KEY              |              SAS/KEY              |
| **Azure Data Lake Gen2** | SAS/MSI/SERVICE PRINCIPAL/KEY/AAD | SAS/MSI/SERVICE PRINCIPAL/KEY/AAD | SAS/MSI/SERVICE PRINCIPAL/KEY/AAD |

使用 AAD 或公用儲存體帳戶進行驗證時，不需要指定 CREDENTIAL。 

- 使用共用存取簽章 (SAS) 進行驗證*IDENTITY：值為「共用存取簽章」的常數*
  *SECRET：* [*共用存取簽章*](/azure/storage/common/storage-sas-overview#what-is-a-shared-access-signature)*會提供您儲存體帳戶中資源的委派存取權。*
  所需最小權限：READ 和 LIST

- 使用[*服務主體*](/azure/sql-data-warehouse/sql-data-warehouse-load-from-azure-data-lake-store#create-a-credential)進行驗證

  *IDENTITY：<ClientID>@<OAuth_2.0_Token_EndPoint>* 
  *SECRET：AAD 應用程式服務主體金鑰*所需的最小 RBAC 角色：儲存體 Blob 資料參與者、儲存體 Blob 資料參與者、儲存體 Blob 資料擁有者或儲存體 Blob 資料讀者

  > [!NOTE]  
  > 使用 OAuth 2.0 權杖端點 **V1**

- 使用儲存體帳戶金鑰進行驗證*IDENTITY：值為「儲存體帳戶金鑰」的常數*
  *SECRET：儲存體帳戶金鑰*
  
- 使用[受控識別](/azure/sql-data-warehouse/load-data-from-azure-blob-storage-using-polybase#authenticate-using-managed-identities-to-load-optional) (VNet 服務端點) 進行驗證*IDENTITY：值為「受控識別」的常數*所需的最小 RBAC 角色：適用於 AAD 註冊 SQL Database 伺服器的儲存體 Blob 資料參與者、儲存體 Blob 資料擁有者或儲存體 Blob 資料讀者 
  
- 使用 AAD 使用者進行驗證*不需要 CREDENTIAL*所需的最小 RBAC 角色：適用於 AAD 使用者的儲存體 Blob 資料參與者、儲存體 Blob 資料擁有者或儲存體 Blob 資料讀者

*ERRORFILE = 目錄位置*</br>
*ERRORFILE* 僅適用於 CSV。 指定 COPY 陳述式內，已拒絕資料列和相應錯誤檔案應寫入的目錄。 您可以指定儲存體帳戶的完整路徑，或指定相對於容器的路徑。 如果指定的路徑不存在，則會代表您建立一個路徑。 會建立名稱為 "_rejectedrows" 的子目錄。"_ " 字元可確保該目錄從其他資料處理逸出，除非已明確在位置參數中指名。 

在此目錄中，會有一個根據載入提交時間建立的資料夾，格式為 YearMonthDay -HourMinuteSecond (例如 20180330-173205)。 在此資料夾中，寫入了兩種類型的檔案，分別是原因 (錯誤r) 檔案和資料 (資料列) 檔案，每個檔案都會預先附加 queryID、distributionID 和檔案 guid。 因為資料與原因檔案在不同的檔案中，所以對應的檔案會具有相符首碼。

如果 ERRORFILE 具有已定義之儲存體帳戶的完整路徑，則會使用 ERRORFILE_CREDENTIAL來連線到該儲存體。 否則，將會使用 CREDENTIAL 所提及的值。

*ERRORFILE_CREDENTIAL = (IDENTITY= ‘’, SECRET = ‘’)*</br>
*ERRORFILE_CREDENTIAL* 僅適用於 CSV 檔案。 支援的資料來源和驗證方法為：

- Azure Blob 儲存體 - SAS/SERVICE PRINCIPAL/KEY/AAD
- Azure Data Lake Gen2 -  SAS/MSI/SERVICE PRINCIPAL/KEY/AAD
  
- 使用共用存取簽章 (SAS) 進行驗證
  - *IDENTITY：值為「共用存取簽章」的常數*
  - *SECRET：* [*共用存取簽章*](/azure/storage/common/storage-dotnet-shared-access-signature-part-1#what-is-a-shared-access-signature)*會提供您儲存體帳戶中資源的委派存取權。*
  - 所需最小權限：READ、LIST、WRITE、CREATE、DELETE
  
- 使用[*服務主體*](/azure/sql-data-warehouse/sql-data-warehouse-load-from-azure-data-lake-store#create-a-credential)進行驗證
  - *IDENTITY：<ClientID>@<OAuth_2.0_Token_EndPoint>*
  - *SECRET：AAD 應用程式服務主體金鑰*
  - 所需的最小 RBAC 角色：儲存體 Blob 資料參與者或儲存體 Blob 資料擁有者
  
> [!NOTE]  
> 使用 OAuth 2.0 權杖端點 **V1**

- 使用儲存體帳戶金鑰進行驗證
  - *IDENTITY：值為「儲存體帳戶金鑰」的常數*
  - *SECRET：儲存體帳戶金鑰*
  
- 使用[受控識別](/azure/sql-data-warehouse/load-data-from-azure-blob-storage-using-polybase#authenticate-using-managed-identities-to-load-optional) (VNet 服務端點) 進行驗證
  - *IDENTITY：值為「受控識別」的常數*
  - 所需的最小 RBAC 角色：適用於 AAD 註冊 SQL Database 伺服器的儲存體 Blob 資料參與者或儲存體 Blob 資料擁有者
  
- 使用 AAD 使用者進行驗證
  - *不需要 CREDENTIAL*
  - 所需的最小 RBAC 角色：適用於 AAD 使用者的儲存體 Blob 資料參與者或儲存體 Blob 資料擁有者

> [!NOTE]  
> 如果您要將相同的儲存體帳戶用於 ERRORFILE，並指定相對於容器根目錄的 ERRORFILE 路徑，則不需要指定 ERROR_CREDENTIAL。

*MAXERRORS = max_errors*</br>
*MAXERRORS* 會指定取消 COPY 作業之前在負載中所允許的拒絕資料列數目上限。 COPY 作業無法匯入的每個資料列都會遭到忽略，且會當作一項錯誤來計算。 如果未指定 max_errors，則預設值為 0。

*COMPRESSION = { 'DefaultCodec '| ’Snappy’ | ‘GZIP’ | ‘NONE’}*</br>
*COMPRESSION* 是選用的，而且會指定外部資料的資料壓縮方法。

- CSV 支援 GZIP
- Parquet 支援 GZIP 和 Snappy
- ORC 支援 DefaultCodec 和 Snappy。
- Zlib 是 ORC 的預設壓縮

未指定此參數時，COPY 命令將會根據副檔名，自動偵測壓縮類型：

- .gz  - **GZIP**
- .snappy – **Snappy**
- .deflate - **DefaultCodec**

 *FIELDQUOTE = 'field_quote'*</br>
*FIELDQUOTE* 會套用至 CSV，並指定將在 CSV 檔案中當作引號字元 (字串分隔符號) 使用的單一字元。 如果未指定，則會使用引號字元 (") 當作引號字元，如 RFC 4180 標準中所定義。 FIELDQUOTE 的 UTF-8 不支援擴充的 ASCII 字元。

> [!NOTE]  
> FIELDQUOTE 字元會在有雙 FIELDQUOTE (分隔符號) 存在的字串資料行中逸出。 

*FIELDTERMINATOR = 'field_terminator’*</br>
*FIELDTERMINATOR* 僅適用於 CSV。 指定將在 CSV 檔案中使用的欄位結束字元。 欄位結束字元可以是多個字元。 預設的欄位結束字元為 (,)。
如需詳細資訊，請參閱[指定欄位與資料列結束字元 (SQL Server)](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md?view=sql-server-2017)。

ROW TERMINATOR = 'row_terminator'</br>
*ROW TERMINATOR* 僅適用於 CSV。 指定將在 CSV 檔案中使用的資料列結束字元。 資料列結束字元可以是多個字元。 根據預設，資料列結束字元為 \r\n。 

指定 \n (新行) 時，COPY 命令會加上 \r 字元前置詞，而導致 \r\n。 若只要指定 \n 字元，請使用十六進位 (0x0A)。 使用十六進位指定多字元資料列結束字元時，請不要在每個字元之間指定 0x。

如需有關指定資料列結束字元的其他指引，請參閱下列[文件](https://docs.microsoft.com/sql/relational-databases/import-export/specify-field-and-row-terminators-sql-server?view=sql-server-2017#using-row-terminators)。

*FIRSTROW  = First_row_int*</br>
*FIRSTROW* 會套用至 CSV，並指定在 COPY 命令的所有檔案中第一次讀取的資料列編號。 值會從 1 開始，也就是預設值。 如果將值設定為二，則在載入資料時，會略過每個檔案中的第一個資料列 (標題列)。 如果資料列存在資料列結束字元，就會略過。

*DATEFORMAT = { ‘mdy’ | ‘dmy’ | ‘ymd’ | ‘ydm’ | ‘myd’ | ‘dym’ }*</br>
DATEFORMAT 僅適用於 CSV，而且會指定對應至 SQL Server 日期格式之日期的日期格式。 如需所有 Transact-SQL 日期和時間資料類型與函式的概觀，請參閱[日期和時間資料類型與函式 (Transact-SQL)](../functions/date-and-time-data-types-and-functions-transact-sql.md?view=sql-server-ver15)。 COPY 命令內的 DATEFORMAT 優先於[在工作階段層級設定的 DATEFORMAT](set-dateformat-transact-sql.md?view=sql-server-ver15)。

*ENCODING = ‘UTF8’ | ‘UTF16’*</br>
*ENCODING* 僅適用於 CSV。 預設值為 UTF8。 指定 COPY 命令所載入之檔案的資料編碼標準。 

*IDENTITY_INSERT = ‘ON’ | ‘OFF’*</br>
IDENTITY_INSERT 會指定所匯入資料檔案中的一或多個識別值是否要用於識別資料行。 如果 IDENTITY_INSERT 為 OFF (預設值)，則會驗證這個資料行的識別值，但不會匯入。 SQL DW 將會根據在資料表建立期間所指定的初始值及累加值，自動指派唯一的值。 請注意 COPY 命令的下列行為：

- 如果 IDENTITY_INSERT 為 OFF，且資料表具有識別資料行
  - 必須指定不會將輸入欄位對應到識別資料行的資料行清單。
- 如果 IDENTITY_INSERT 為 ON，且資料表具有識別資料行
  - 如果傳遞資料行清單，則必須將輸入欄位對應到識別資料行。
- 資料行清單中的 IDENTITY COLUMN 不支援預設值。
- 一次只能為一個資料表設定 IDENTITY_INSERT。

### <a name="permissions"></a>權限  

執行 Copy 命令的使用者必須具有下列權限： 

- [ADMINISTER DATABASE BULK OPERATIONS](grant-database-permissions-transact-sql.md?view=azure-sqldw-latest#remarks)
- [INSERT ](grant-database-permissions-transact-sql.md?view=azure-sqldw-latest#remarks)

需要 INSERT 和 ADMINISTER BULK OPERATIONS 權限。 在 Azure SQL 資料倉儲中，需要 INSERT 和 ADMINISTER DATABASE BULK OPERATIONS 權限。

## <a name="examples"></a>範例  

### <a name="a-load-from-a-public-storage-account"></a>A. 從公用儲存體帳戶載入

下列範例是 COPY 命令的最簡單形式，它會從公用儲存體帳戶載入資料。 在此範例中，COPY 陳述式的預設值符合行項目 csv 檔案的格式。

```sql
COPY INTO dbo.[lineitem] FROM 'https://unsecureaccount.blob.core.windows.net/customerdatasets/folder1/lineitem.csv’
```

COPY 命令的預設值為：

- DATEFORMAT = 工作階段 DATEFORMAT 

- MAXERRORS = 0

- COMPRESSION 預設值為未壓縮

- FIELDQUOTE = “” 

- FIELDTERMINATOR = “,” 

- ROWTERMINATOR = ‘\n'

> [!IMPORTANT]
> COPY 在內部會將 ‘\n’ 視為 ‘\r\n’。 如需詳細資訊，請參閱 [ROWTERMINATOR]() 一節。

- FIRSTROW = 1

- ENCODING = ‘UTF8’

- FILE_TYPE = ‘CSV’

- IDENTITY_INSERT = ‘OFF’

### <a name="b-load-authenticating-via-share-access-signature-sas"></a>B. 透過共用存取簽章 (SAS) 載入驗證

下列範例會載入使用換行字元作為資料列結束字元的檔案，如 UNIX 輸出。 此範例也會使用 SAS 金鑰向 Azure Blob 儲存體進行驗證。

```sql
COPY INTO test_1
FROM 'https://myaccount.blob.core.windows.net/myblobcontainer/folder1/'
WITH (
    FILE_TYPE = 'CSV',
    CREDENTIAL=(IDENTITY= 'Shared Access Signature', SECRET='<Your_SAS_Token>'),
    --CREDENTIAL should look something like this:
    --CREDENTIAL=(IDENTITY= 'Shared Access Signature', SECRET='?sv=2018-03-28&ss=bfqt&srt=sco&sp=rl&st=2016-10-17T20%3A14%3A55Z&se=2021-10-18T20%3A19%3A00Z&sig=IEoOdmeYnE9%2FKiJDSHFSYsz4AkNa%2F%2BTx61FuQ%2FfKHefqoBE%3D'),
    FIELDQUOTE = '"',
    FIELDTERMINATOR=';',
    ROWTERMINATOR='0X0A',
    ENCODING = 'UTF8',
    DATEFORMAT = 'ymd',
    MAXERRORS = 10,
    ERRORFILE = '/errorsfolder/',--path starting from the storage container
    IDENTITY_INSERT = ‘ON’
)
```

### <a name="c-load-with-a-column-list-with-default-values-authenticating-via-storage-account-key"></a>C. 以具有預設值的資料行清單載入，並透過儲存體帳戶金鑰進行驗證

此範例會載入使用預設值指定資料行清單的檔案。 

```sql
--Note when specifying the column list, input field numbers start from 1
COPY INTO test_1 (Col_one default 'myStringDefault' 1, Col_two default 1 3)
FROM 'https://myaccount.blob.core.windows.net/myblobcontainer/folder1/'
WITH (
    FILE_TYPE = 'CSV',
    CREDENTIAL=(IDENTITY= 'Storage Account Key', SECRET='<Your_Account_Key>'),
    --CREDENTIAL should look something like this:
    --CREDENTIAL=(IDENTITY= 'Storage Account Key', SECRET='x6RWv4It5F2msnjelv3H4DA80n0PQW0daPdw43jM0nyetx4c6CpDkdj3986DX5AHFMIf/YN4y6kkCnU8lb+Wx0Pj+6MDw=='),
    FIELDQUOTE = '"',
    FIELDTERMINATOR=',',
    ROWTERMINATOR='0x0A',
    ENCODING = 'UTF8',
    FIRSTROW = 2
)
```

### <a name="d-load-parquet-or-orc-using-existing-file-format-object"></a>D. 使用現有的檔案格式物件載入 Parquet 或 ORC

 此範例會使用萬用字元載入某個資料夾下的所有 parquet 檔案。 

```sql
COPY INTO test_parquet
FROM 'https://myaccount.blob.core.windows.net/myblobcontainer/folder1/*.parquet'
WITH (
    FILE_FORMAT = myFileFormat
    CREDENTIAL=(IDENTITY= 'Shared Access Signature', SECRET='<Your_SAS_Token>')
)
```

### <a name="e-load-specifying-wild-cards-and-multiple-files"></a>E. 透過指定萬用字元和多個檔案來載入

```sql
COPY INTO t1
FROM 
'https://myaccount.blob.core.windows.net/myblobcontainer/folder0/*.txt', 
    'https://myaccount.blob.core.windows.net/myblobcontainer/folder1'
WITH ( 
    FILE_TYPE = 'CSV'
    CREDENTIAL=(IDENTITY= '<client_id>@<OAuth_2.0_Token_EndPoint>',SECRET='<key>'),
    FIELDTERMINATOR = '|'
)
```

## <a name="see-also"></a>另請參閱  

 [使用 SQL 資料倉儲載入概觀](/azure/sql-data-warehouse/design-elt-data-loading>) 
