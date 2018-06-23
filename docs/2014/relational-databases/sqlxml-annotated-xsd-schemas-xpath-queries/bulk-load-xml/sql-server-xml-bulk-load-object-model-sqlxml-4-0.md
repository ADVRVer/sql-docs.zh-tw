---
title: SQL Server XML 大量載入物件模型 (SQLXML 4.0) |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bb60aaf57869dbbd108c0815ed3fc02b07ed4bf5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144909"
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a>SQL Server XML 大量載入物件模型 (SQLXML 4.0)
  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML 大量載入物件模型會包含 SQLXMLBulkLoad 物件。 這個物件支援下列方法和屬性。  
  
## <a name="methods"></a>方法  
 Execute  
 使用當做參數提供的結構描述檔案和資料檔案 (或資料流) 大量載入資料。  
  
## <a name="properties"></a>屬性  
 大量載入  
 指定是否應該執行大量載入。 這個屬性相當實用，如果您想要產生 （請參閱遵循 SchemaGen、 SGDropTables 和 SGUseID 屬性） 的結構描述並不會執行大量載入。 這是布林屬性。 當屬性設定為 TRUE 時，XML 大量載入會執行。 設定為 FALSE 時，XML 大量載入則不會執行。  
  
 預設值為 TRUE。  
  
 CheckConstraints  
 指定當 XML 大量載入將資料插入資料行時，是否要檢查在資料行上指定的條件約束 (例如，由於資料行間之主索引鍵/外部索引鍵關聯性緣故的條件約束)。 這是布林屬性。  
  
 當屬性設定為 TRUE 時，XML 大量載入會檢查插入之每個值的條件約束 (也就是說，條件約束違規會導致錯誤)。  
  
> [!NOTE]  
>  若要將保留此屬性為 FALSE，您必須擁有**ALTER TABLE**目標資料表的權限。 如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。  
  
 預設值為 FALSE。 設定為 FALSE 時，XML 大量載入會在插入作業期間忽略條件約束。 在目前的實作中，您必須以對應結構描述中，主索引鍵和外部索引鍵關聯性的順序定義資料表。 也就是說，具有主索引鍵的資料表必須在具有外部索引鍵的對應資料表之前定義，否則，XML 大量載入會失敗。  
  
 請注意，如果識別碼擴展即將完成，則此選項不會套用，而且條件約束檢查將會保持開啟。 如果 `KeepIdentity=False`，而且有定義一個關聯性，其中父系是識別欄位，並在產生值時將其提供給子系，則會發生這個狀況。  
  
 ConnectionCommand  
 識別現有的連接物件 （例如，ADO 或 ICommand 命令物件），XML 大量載入應該使用。 您可以使用 ConnectionCommand 屬性，而不是使用 ConnectionString 屬性指定的連接字串。 Transaction 屬性必須設定為 TRUE，如果您使用 ConnectionCommand。  
  
 如果您使用 ConnectionString 和 ConnectionCommand 屬性，XML 大量載入會使用最後指定的屬性。  
  
 預設值是 NULL。  
  
 ConnectionString  
 識別 OLE DB 連接字串，提供必要的資訊來建立資料庫執行個體的連接。 如果您使用 ConnectionString 和 ConnectionCommand 屬性，XML 大量載入會使用最後指定的屬性。  
  
 預設值是 NULL。  
  
 ErrorLogFile  
 指定 XML 大量載入記錄錯誤和訊息所在的檔案名稱。 預設為空字串，在此情況下，沒有做任何記錄。  
  
 FireTriggers  
 指定在目標資料表上定義的觸發程序是否應該在大量載入作業期間引發。 預設值為 FALSE。  
  
 設定為 TRUE 時，觸發程序一般將會在插入作業期間引發。  
  
> [!NOTE]  
>  若要將保留此屬性為 FALSE，您必須擁有**ALTER TABLE**目標資料表的權限。 如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。  
  
 請注意，如果識別碼擴展即將完成，則此選項不會套用，而且觸發條件將會保持開啟。 如果 `KeepIdentity=False`，而且有定義一個關聯性，其中父系是識別欄位，並在產生值時將其提供給子系，則會發生這個狀況。  
  
 ForceTableLock  
 指定 XML 大量載入複製資料的目標資料表是否應該在大量載入期間鎖定。 這是布林屬性。 當屬性設定為 TRUE 時，XML 大量載入會取得大量載入期間的資料表鎖定。 設定為 FALSE 時，XML 大量載入會在每次將記錄插入資料表時取得資料表鎖定。  
  
 預設值為 FALSE。  
  
 IgnoreDuplicateKeys  
 指定嘗試在索引鍵資料行中插入重複的值時該怎麼辦。 如果此屬性設定為 TRUE，而且嘗試在索引鍵資料行中插入具有重複值的記錄，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不會插入該記錄。 但是它會插入後續的記錄，因此，大量載入作業不會失敗。 如果此屬性設定為 FALSE，嘗試在索引鍵資料行中插入重複的值時，大量載入會失敗。  
  
 IgnoreDuplicateKeys 屬性設定為 TRUE，當插入資料表中每一筆記錄發出 COMMIT 陳述式。 這會讓效能減慢。 屬性可以設為 true，則只有當交易屬性設定為 FALSE，因為交易行為會使用檔案實作。  
  
 預設值為 FALSE。  
  
 KeepIdentity  
 指定如何處理來源檔案中識別類型資料行的值。 這是布林屬性。 當屬性設定為 TRUE 時，XML 大量載入會將來源檔案中指定的值指派給識別資料行。 當屬性設定為 FALSE 時，大量載入作業會忽略來源檔案中指定的識別資料行值。 在此情況下，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會指派值給識別資料行。  
  
 如果大量載入包含的資料行是參考儲存 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 產生之值所在識別資料行的外部索引鍵，大量載入就會將這些識別值適當地擴展到外部索引鍵資料行。  
  
 此屬性的值會套用到大量載入包含的所有資料行。 預設值為 TRUE。  
  
> [!NOTE]  
>  若要將保留此屬性為 TRUE，您必須擁有**ALTER TABLE**目標資料表的權限。 否則，它必須設定為值 FALSE。 如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。  
  
 KeepNulls  
 指定在 XML 文件中，用於缺少對應屬性或子元素之資料行的值。 這是布林屬性。 當屬性設定為 TRUE 時，XML 大量載入會將 Null 值指派給資料行。 它不會將資料行的預設值指派為伺服器上的值 (如果有的話)。 此屬性的值會套用到大量載入包含的所有資料行。  
  
 預設值為 FALSE。  
  
 SchemaGen  
 指定是否要在執行大量載入作業前，建立所需的資料表。 這是布林屬性。 如果此屬性設定為 TRUE，會建立對應結構描述中所識別的資料表 (資料庫必須存在)。 如果一或多個資料表的資料庫中已經存在，SGDropTables 屬性會決定是否要卸除並重新建立這些預先存在的資料表。  
  
 SchemaGen 屬性的預設值為 FALSE。 SchemaGen 並不會建立新建立的資料表上的主索引鍵條件約束。 SchemaGen，不過，FOREIGN KEY 條件約束在資料庫中建立如果可以找到符合`sql:relationship`和`sql:key-fields`對應結構描述中的註解，而且如果索引鍵欄位組成的單一資料行。  
  
 請注意，是否您將 SchemaGen 屬性設為 TRUE 時，XML 大量載入會下列作業：  
  
-   從元素和屬性名稱建立所需的資料表。 因此，您最好不要將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 保留字用於結構描述中的元素和屬性名稱。  
  
-   傳回溢位資料行指定使用的任何資料[sql: overflow-field-欄位](annotation-interpretation-sql-overflow-field.md)中[xml 資料型別](/sql/t-sql/xml/xml-transact-sql)格式。  
  
 SGDropTables  
 指定應該卸除或重新建立現有的資料表。 SchemaGen 屬性設定為 TRUE 時，您可以使用這個屬性。 如果 SGDropTables 為 FALSE，則會保留現有的資料表。 當此屬性為 TRUE 時，會刪除並重新建立現有的資料表。  
  
 預設值為 FALSE。  
  
 SGUseID  
 指定在建立資料表時，對應結構描述中識別為 `id` 類型的屬性是否可用於建立 PRIMARY KEY 條件約束。 SchemaGen 屬性設定為 TRUE 時，請使用這個屬性。 SGUseID 為 TRUE 時，如果 SchemaGen 公用程式會使用屬性的`dt:type="id"`指定為主要索引鍵資料行，並建立資料表時將適當的主索引鍵條件約束。  
  
 預設值為 FALSE。  
  
 TempFilePath  
 針對交易的大量載入，指定 XML 大量載入建立暫存檔案所在的檔案路徑  (此屬性只有在 Transaction 屬性設定為 TRUE 時才有用)。您必須確定用於 XML 大量載入的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 帳戶具有這個路徑的存取權。 如果未設定此屬性，XML 大量載入會將暫存檔案儲存在 TEMP 環境變數中所指定的位置。  
  
 Transaction  
 指定大量載入是否應該當做交易完成，在此情況下，保證會在大量載入失敗時回復。 這是布林屬性。 如果屬性設定為 TRUE，大量載入會在交易內容中發生。 只有交易設定為 TRUE 時，TempFilePath 屬性才能很有用。  
  
> [!NOTE]  
>  如果您載入二進位資料 (例如，將 bin.hex、 bin.base64 XML 資料類型為二進位，映像[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料型別)，交易屬性必須設定為 FALSE。  
  
 預設值為 FALSE。  
  
 XMLFragment  
 指定來源資料是否為 XML 片段。 XML 片段是沒有單一、最上層 (根) 元素的 XML 文件。 這是布林屬性。 如果來源檔案由 XML 片段所組成，此屬性必須設定為 TRUE。  
  
 預設值為 FALSE。  
  
  
