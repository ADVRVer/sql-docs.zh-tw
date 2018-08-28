---
title: 將 Excel 中的資料匯入到 SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: import-export
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8613f9fc6a92519f2ffaf584919ab3d65c88f3de
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43083331"
---
# <a name="import-data-from-excel-to-sql-server-or-azure-sql-database"></a>將 Excel 中的資料匯入到 SQL Server 或 Azure SQL Database
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
有數種方式可以將 Excel 檔案中的資料匯入到 SQL Server 或 Azure SQL Database。 某些方法可讓您只執行一個步驟，便能直接從 Excel 檔案匯入資料；其他方法會要求先將 Excel 資料匯出成文字，然後您再匯入這些文字。 本文摘要說明常用的方法，並提供連結，為您提供更詳細的資訊。

## <a name="list-of-methods"></a>方法清單

-   您可以使用下列其中一種工具，透過單一步驟將資料直接從 Excel 匯入至 SQL：
    -   [SQL Server 匯入和匯出精靈](#wiz)
    -   [SQL Server Integration Services (SSIS)](#ssis)
    -   [OPENROWSET](#openrowset) 函式
-   您可以將資料從 Excel 匯出為文字，然後使用下列其中一種工具來匯入文字檔，透過這兩個步驟來匯入資料：
    -   [匯入一般檔案精靈](#import-wiz)
    -   [BULK INSERT](#bulk-insert) 陳述式
    -   [BCP](#bcp)
    -   [複製精靈 (Azure Data Factory)](#adf-wiz)
    -   [Azure Data Factory](#adf)

如果您想要從 Excel 活頁簿匯入多個工作表，您通常必須針對每個工作表執行每個工具一次。

針對複雜工具和服務 (例如 SSIS 或 Azure Data Factory) 的完整描述不在此清單的涵蓋範圍內。 若要深入了解您感興趣的解決方案，請遵循所提供的連結以取得詳細資訊。

> [!IMPORTANT]
> 如需連接至 Excel 檔案，以及將資料從 Excel 檔案載入或載入至 Excel 檔案的限制與已知問題的詳細資訊，請參閱[使用 SQL Server Integration Services (SSIS) 將資料從 Excel 載入或載入至 Excel](../../integration-services/load-data-to-from-excel-with-ssis.md)。

## <a name="wiz"></a> SQL Server 匯入和匯出精靈

逐步執行 [SQL Server 匯入和匯出精靈] 的頁面，以從 Excel 檔案直接匯入資料。 您也可以將設定儲存為 SQL Server Integration Services (SSIS) 套件，以便日後自訂及重複使用。

若要了解如何啟動精靈，請參閱[啟動 SQL Server 匯入和匯出精靈](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)。

如需使用精靈從 Excel 匯入至 SQL Server 的範例，請參閱[透過這個匯入和匯出精靈的簡單範例來開始使用](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)。

![連線至 Excel 資料來源](media/excel-connection.png)

## <a name="ssis"></a> SQL Server Integration Services (SSIS)

如果您熟悉 SSIS 且不想執行 SQL Server 匯入和匯出精靈，請建立在資料流程中使用 Excel 來源和 SQL Server 目的地的 SSIS 套件。

如需這些 SSIS 元件的詳細資訊，請參閱下列主題：
-   [Excel 來源](../../integration-services/data-flow/excel-source.md)
-   [SQL Server 目的地](../../integration-services/data-flow/sql-server-destination.md)

若要開始學習如何建置 SSIS 套件，請參閱[如何建立 ETL 套件](../../integration-services/ssis-how-to-create-an-etl-package.md)的教學課程。

![資料流程中的元件](media/excel-to-sql-data-flow.png)

## <a name="openrowset"></a> OPENROWSET 和連結的伺服器

> [!NOTE]
> 在 Azure 中，OPENROWSET 與 OPENDATASOURCE 函式僅適用於 SQL Database 受控執行個體 (預覽)。

> [!NOTE]
> 連接至 Excel 資料來源的 ACE 提供者 (先前稱為 Jet 提供者) 是供互動式用戶端使用。 如果您在伺服器上使用 ACE 提供者 (特別是在自動化程序或平行執行的程序中)，可能會看到非預期的結果。

### <a name="distributed-queries"></a>分散式查詢

使用 Transact-SQL `OPENROWSET` 或 `OPENDATASOURCE` 函式，直接從 Excel 檔案匯入資料。 此使用方式稱為「分散式查詢」。

在您可以執行分散式查詢之前，必須啟用 `ad hoc distributed queries` 伺服器設定選項，如下列範例所示。 如需詳細資訊，請參閱[特定分散式查詢伺服器設定選項](../../database-engine/configure-windows/ad-hoc-distributed-queries-server-configuration-option.md)。

```sql
sp_configure 'show advanced options', 1;
RECONFIGURE;
GO
sp_configure 'Ad Hoc Distributed Queries', 1;
RECONFIGURE;
GO
```

下列程式碼範例使用 `Data`，將資料從 Excel `OPENROWSET` 工作表匯入至新的資料庫資料表。

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENROWSET('Microsoft.ACE.OLEDB.12.0',
    'Excel 12.0; Database=D:\Desktop\Data.xlsx', [Data$]);
GO
```

以下是使用 `OPENDATASOURCE` 的相同範例。

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENDATASOURCE('Microsoft.ACE.OLEDB.12.0',
    'Data Source=D:\Desktop\Data.xlsx;Extended Properties=Excel 12.0')...[Data$];
GO
```

若要將匯入的資料「附加」到「現有」的資料表，而不建立新的資料表，請使用 `INSERT INTO ... SELECT ... FROM ...` 語法，而不是上述範例中使用的 `SELECT ... INTO ... FROM ...` 語法。

若要查詢 Excel 資料但不進行匯入，請直接使用標準 `SELECT ... FROM ...` 語法。

如需分散式查詢的詳細資訊，請參閱下列主題：
-   [分散式查詢](https://msdn.microsoft.com/library/ms188721(v=sql.105).aspx)。 (SQL Server 2016 仍支援分散式查詢，但針對此功能的文件尚未更新)。
-   [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)
-   [OPENDATASOURCE](../../t-sql/functions/openquery-transact-sql.md)

### <a name="linked-servers"></a>連結的伺服器

您也可以將針對 Excel 檔案的持續連線設定為「連結的伺服器」。 下列範例會將資料從現有 Excel 連結的伺服器 `EXCELLINK` 的 `Data` 工作表匯入至名為 `Data_ls` 的新資料庫資料表。

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_ls FROM EXCELLINK...[Data$];
GO
```

您可以從 SQL Server Management Studio，或是執行系統預存程序 `sp_addlinkedserver` (如下列範例所示) 來建立連結的伺服器。

```sql
DECLARE @RC int

DECLARE @server     nvarchar(128)
DECLARE @srvproduct nvarchar(128)
DECLARE @provider   nvarchar(128)
DECLARE @datasrc    nvarchar(4000)
DECLARE @location   nvarchar(4000)
DECLARE @provstr    nvarchar(4000)
DECLARE @catalog    nvarchar(128)

-- Set parameter values
SET @server =     'EXCELLINK'
SET @srvproduct = 'Excel'
SET @provider =   'Microsoft.ACE.OLEDB.12.0'
SET @datasrc =    'D:\Desktop\Data.xlsx'
SET @provstr =    'Excel 12.0'

EXEC @RC = [master].[dbo].[sp_addlinkedserver] @server, @srvproduct, @provider,
@datasrc, @location, @provstr, @catalog
```

如需連結的伺服器的詳細資訊，請參閱下列主題：
-   [建立連結的伺服器](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)
-   [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)

如需連結的伺服器和分散式查詢的更多範例及詳細資訊，請參閱下列主題：
-   [如何搭配使用 Excel 以及 SQL Server 連結伺服器和分散式查詢](https://support.microsoft.com/help/306397/how-to-use-excel-with-sql-server-linked-servers-and-distributed-queries)
-   [如何將 Excel 中的資料匯入到 SQL Server](https://support.microsoft.com/help/321686/how-to-import-data-from-excel-to-sql-server)

## <a name="prereq"></a> 必要條件：將 Excel 資料儲存為文字
若要使用此頁面所描述的剩餘方法 (BULK INSERT 陳述式、BCP 工具或 Azure Data Factory)，您必須先將 Excel 資料匯出為文字檔。

在 Excel 中，選取 [檔案 | 另存新檔]，然後選取 [文字檔 (Tab 字元分隔) (\*.txt)] 或 [CSV (逗號分隔) (\*.csv)] 作為目的地檔案類型。

如果您想要從活頁簿匯出多個工作表，請選取每個工作表，然後重複此程序。 **另存新檔**命令只會匯出使用中工作表。

> [!TIP]
> 若要取得資料匯入工具的最佳結果，請儲存僅包含資料行標題和包含資料之資料列的工作表。 如果儲存的資料包含頁面標題、空白行、註解和其他內容，您稍後在匯入資料時可能會看到非預期的結果。

## <a name="import-wiz"></a> 匯入一般檔案精靈

逐步設定「匯入一檔案精靈」的每個頁面，匯入儲存為文字檔的資料。

如先前[必要條件](#prereq)一節中所述，您必須將 Excel 資料匯出成文字，才能使用「匯入一般檔案精靈」將它匯入。

如需「匯入一般檔案精靈」的詳細資訊，請參閱[將一般檔案匯入 SQL 精靈](import-flat-file-wizard.md)。

## <a name="bulk-insert"></a> BULK INSERT 命令

`BULK INSERT` 是您可從 SQL Server Management Studio 執行的 Transact-SQL 命令。 下列範例會將來自 `Data.csv` 逗號分隔檔案的資料載入至現有資料庫資料表。

如先前[必要條件](#prereq)一節中所述，您必須將 Excel 資料匯出成文字，才能使用 BULK INSERT 將它匯入。 BULK INSERT 無法直接讀取 Excel 檔案。

```sql
USE ImportFromExcel;
GO
BULK INSERT Data_bi FROM 'D:\Desktop\data.csv'
   WITH (
      FIELDTERMINATOR = ',',
      ROWTERMINATOR = '\n'
);
GO
```

如需詳細資訊，請參閱下列主題：
-   [使用 BULK INSERT 或 OPENROWSET(BULK...) 匯入大量資料](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
-   [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)

## <a name="bcp"></a> BCP 工具

BCP 是您從命令提示字元執行的程式。 下列範例會將來自 `Data.csv` 逗號分隔檔案的資料載入至現有 `Data_bcp` 資料庫資料表。

如先前[必要條件](#prereq)一節中所述，您必須將 Excel 資料匯出成文字，才能使用 BCP 將它匯入。 BCP 無法直接讀取 Excel 檔案。

```sql
bcp.exe ImportFromExcel..Data_bcp in "D:\Desktop\data.csv" -T -c -t ,
```

如需 BCP 的詳細資訊，請參閱下列主題：
-   [使用 bcp 公用程式匯入及匯出大量資料](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)
-   [bcp 公用程式](../../tools/bcp-utility.md)
-   [準備大量匯出或匯入的資料](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)

## <a name="adf-wiz"></a> 複製精靈 (Azure Data Factory)
逐步設定「Azure Data Factory 複製精靈」的每個頁面，匯入儲存為文字檔的資料。

如先前[必要條件](#prereq)一節中所述，您必須將 Excel 資料匯出成文字，才能使用 Azure Data Factory 將它匯入。 Data Factory 無法直接讀取 Excel 檔案。

如需 [複製精靈] 的詳細資訊，請參閱下列主題：
-   [Data Factory 複製精靈](https://docs.microsoft.com/azure/data-factory/data-factory-azure-copy-wizard)
-   [教學課程：使用 Data Factory 複製精靈建立具有複製活動的管線](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-wizard-tutorial)。

## <a name="adf"></a> Azure Data Factory
如果您熟悉 Azure Data Factory，且不想執行 [複製精靈]，請建立具有 [複製] 活動的管線，以從文字檔複製至 SQL Server 或 Azure SQL Database。

如先前[必要條件](#prereq)一節中所述，您必須將 Excel 資料匯出成文字，才能使用 Azure Data Factory 將它匯入。 Data Factory 無法直接讀取 Excel 檔案。

如需使用這些 Data Factory 來源與接收的詳細資訊，請參閱下列主題：
-   [檔案系統](https://docs.microsoft.com/azure/data-factory/data-factory-onprem-file-system-connector)
-   [[SQL Server]](https://docs.microsoft.com/azure/data-factory/data-factory-sqlserver-connector)
-   [Azure SQL Database](https://docs.microsoft.com/azure/data-factory/data-factory-azure-sql-connector)

若要開始學習如何使用 Azure Data Factory 複製資料，請參閱下列主題：
-   [使用複製活動來移動資料](https://docs.microsoft.com/azure/data-factory/data-factory-data-movement-activities)
-   [教學課程：使用 Azure 入口網站建立具有複製活動的管線](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-from-azure-blob-storage-to-sql-database)

## <a name="see-also"></a>另請參閱
[使用 SQL Server Integration Services (SSIS) 從 Excel 匯入資料，或將資料匯出至 Excel](../../integration-services/load-data-to-from-excel-with-ssis.md)
