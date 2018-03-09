---
title: "查詢及修改 SQL Server 資料 （SQL 與 R 深入探討） |Microsoft 文件"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 901ae76597dd9a9ab1136a35442cc27b6ea63e61
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2018
---
# <a name="query-and-modify-the-sql-server-data-sql-and-r-deep-dive"></a>查詢及修改 SQL Server 資料 （SQL 與 R 深入探討）
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

本文是資料科學深入探討教學課程中，有關如何使用一部分[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)與 SQL Server。

既然您已將資料載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，便可以在 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]使用您建立的資料來源作為 R 函數的引數，以取得變數的基本資訊，並產生摘要和長條圖。

在此步驟中，您可以重複使用進行一些快速分析，並提升資料的資料來源。

## <a name="query-the-data"></a>查詢資料

首先，取得一份資料行和其資料類型的清單。

1.  使用函數[rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf)並指定您想要分析的資料來源。

    根據您的 RevoScaleR 版本，您也可以使用[rxGetVarNames](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarnames)。 
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **結果**
    
    *Var 1: custID, Type: integer*
    
    *Var 2: gender, Type: integer*
    
    *Var 3: state, Type: integer*
    
    *Var 4: cardholder, Type: integer*
    
    *Var 5: balance, Type: integer*
    
    *Var 6: numTrans, Type: integer*
    
    *Var 7: numIntlTrans, Type: integer*
    
    *Var 8: creditLine, Type: integer*
    
    *Var 9: fraudRisk, Type: integer*


## <a name="modify-metadata"></a>修改中繼資料

所有的變數會儲存為整數，但某些變數代表類別的資料 – 在 R 中稱為「因素變數」。例如，資料行 *state* 包含數字，用來作為 50 個州再加上華盛頓哥倫比亞特區的識別碼。  為了讓您更輕鬆地了解資料，您將數字取代為各州縮寫的清單。

在此步驟中，建立包含縮寫的字串向量，然後將這些類別的值對應至原始的整數識別碼。 然後使用中的新變數*colInfo*引數，以指定此資料行，做為因數處理。 每當您分析資料，或將它移，使用縮寫，而且資料行處理做為因數。

將資料行對應至縮寫，然後才使用它作為因數，實際上也能改善效能。 如需詳細資訊，請參閱[R 和資料最佳化](..\r\r-and-data-optimization-r-services.md)。

1. 一開始先建立 R 變數 *stateAbb*，以及定義要新增給它的字串向量，如下所示︰
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. 接下來，建立名為 *ccColInfo*的資料行資訊物件，指定現有整數值對類別層級 (各州的縮寫) 的對應。
  
    此陳述式也會建立針對 gender 和 cardholder 的因素變數。
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. 若要建立使用更新資料的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源，請如之前一樣呼叫 **RxSqlServerData** 函數，但新增 *colInfo* 引數。
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - 針對 *table* 參數，傳入變數 *sqlFraudTable*，其中包含您稍早建立的資料來源。
    - 針對 *colInfo* 參數，傳入 *ccColInfo* 變數，其中包含資料行資料類型和因素層級。

4.  您現在可以使用 **rxGetVarInfo** 函數檢視新資料來源中的變數。
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **結果**
    
    *Var 1: custID, Type: integer*
    
    *Var 2： 性別 2 因素層： 男性女性*
    
    *Var 3： 狀態 51 因素層級： AK AL AR AZ CA...VT WA WI WV WY*
    
    *Var 4： 持卡人 2 因素層級： 主體次要資料庫*
    
    *Var 5: balance, Type: integer*
    
    *Var 6: numTrans, Type: integer*
    
    *Var 7: numIntlTrans, Type: integer*
    
    *Var 8: creditLine, Type: integer*
    
    *Var 9: fraudRisk, Type: integer*

現在您指定的三個變數 (_gender_、 _state_和 _cardholder_) 被視為因素。

## <a name="next-step"></a>下一步

[定義及使用計算內容](../../advanced-analytics/tutorials/deepdive-define-and-use-compute-contexts.md)

## <a name="previous-step"></a>上一個步驟

[使用 RxSqlServerData 建立 SQL Server 資料物件](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
