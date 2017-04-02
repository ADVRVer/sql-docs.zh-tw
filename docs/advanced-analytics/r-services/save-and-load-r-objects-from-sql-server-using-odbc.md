---
title: "從 SQL Server 使用 ODBC 儲存和載入 R 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 6ac2e971-6b4f-4c73-ba57-29c716abd057
caps.latest.revision: 8
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# 從 SQL Server 使用 ODBC 儲存和載入 R 物件
SQL Server R Services 可以將序列化的 R 物件儲存到資料表中，並視需要從資料表載入物件；您不必重新執行 R 程式碼，或是重新定型模型。 這項可在資料庫中儲存 R 物件的功能，對下列案例來說至關重要：定型和儲存模型，以於稍後用來進行評分或分析等案例。 

為了改善這項重要步驟的效能，**RevoScaleR** 套件現已包含新的序列化和還原序列化函式，可大幅改善效能，並更精簡地儲存物件。 此外，您可以使用 *RxOdbcData* 以透過 ODBC 連接呼叫這些新的函式，直接從 R 環境將 R 物件儲存到 SQL Server。

## <a name="overview"></a>概觀

**RevoScaleR** 套件現已包含新的函式，可讓您更輕鬆地將 R 物件儲存到 SQL Server，然後從 SQL Server 資料表中讀取物件。 使用這些函式時，必須具備使用 *RxOdbcData* 資料來源與 SQL Server 建立的連線。

一般情況下，在簡單的索引鍵值儲存之後，系統會將函式呼叫模型化，其中，索引鍵即為物件的名稱，而與索引鍵相關聯的值即為要移入或移出資料表的 varbinary R 物件。 

- 根據預設，您從 R 呼叫要移至 SQL Server 的任何物件，皆會受到序列化與壓縮處理。 
- 反之，當您從 SQL Server 資料表載入物件以用於 R 程式碼時，即會將物件還原序列化與解壓縮。
- 或者，您可以指定不要序列化物件，亦可選擇新的壓縮演算法，而不使用預設壓縮演算法。


## <a name="new-functions"></a>新函式

- `rxWriteObject` 可使用 ODBC 資料來源，將 R 物件寫入 SQL Server。 

- `rxReadObject` 可使用 ODBC 資料來源，從 SQL Server 資料庫讀取 R 物件。

- `rxDeleteObject` 可將 ODBC 資料來源中指定的 R 物件，從 SQL Server 資料庫中刪除。 如果索引鍵/版本組合識別出多項物件，則會將其全部刪除。

- `rxListKeys` 會以索引鍵/值組的格式列出所有可用物件。 這可協助您決定 R 物件的名稱和版本。

如需每個函式語法的詳細說明，請參閱 R 說明。 MSDN 上的 [ScaleR 參考](https://msdn.microsoft.com/microsoft-r/scaler/scaler)會於日後提供詳細資料。

## <a name="how-to-store-r-objects-in-sql-server-using-odbc"></a>如何使用 ODBC 將 R 物件儲存到 SQL Server 中

此程序示範如何使用新的函式建立模型，並將它儲存到 SQL Server 中。

1. 設定 SQL Server 的連接字串。
   ```R
   conStr <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. 使用連接字串，在 R 中建立 *rxOdbcData* 資料來源物件。
   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr)
   ```

3. 如果該物件已存在，而且您不想要追蹤物件的舊版本，請刪除資料表。

   ```R
   if(rxSqlServerTableExists(ds@table, ds@connectionString)) {
       rxSqlServerDropTable(ds@table, ds@connectionString)
       }
   ```
   
4. 定義可用來儲存二進位物件的資料表。

   ```R
   ddl <- paste(" CREATE TABLE [", ds@table, "] 
      (","  [id] varchar(200) NOT NULL,
       "," [value] varbinary(max),
       "," CONSTRAINT unique_id UNIQUE (id))", 
       sep = "") 
   ```
5. 開啟 ODBC 連線以建立資料表，並在 DDL 陳述式完成時，關閉連線。

   ```R
    rxOpen(ds, "w") 
    rxExecuteSQLDDL(ds, ddl) 
    rxClose(ds)
    ```
6. 產生您想要儲存的 R 物件。

   ```R
   infertLogit <- rxLogit(case ~ age + parity + education + spontaneous + induced, 
     data = infert)
   ```
6. 使用稍早建立的 *RxOdbcData* 物件，將模型儲存至資料庫。

   ```R
   rxWriteObject(ds, "logit.model", infertLogit)
   ```

## <a name="how-to-read-r-objects-from-sql-server-using-odbc"></a>如何使用 ODBC 從 SQL Server 讀取 R 物件

此程序示範如何使用新的函式，從 SQL Server 載入模型。

1. 設定 SQL Server 的連接字串。

   ```R
   conStr2 <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. 使用連接字串，在 R 中建立 *rxOdbcData* 資料來源物件。

   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr2)
   ```
3. 指定模型的 R 物件名稱，以從資料表中讀取該模型。

   ```R
    infertLogit2 <- rxReadObject(ds, "logit.model")
   ```

## <a name="see-also"></a>另請參閱

[R Services 功能及工作](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)
