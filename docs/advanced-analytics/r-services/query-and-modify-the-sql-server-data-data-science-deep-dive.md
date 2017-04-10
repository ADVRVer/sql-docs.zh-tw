---
title: "查詢及修改 SQL Server 資料 (資料科學深入探討) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 8c7007a9-9a8f-4dcd-8068-40060d4f6444
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# 查詢及修改 SQL Server 資料 (資料科學深入探討)
既然您已將資料載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，便可以在 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 使用您建立的資料來源作為 R 函數的引數，以取得變數的基本資訊，並產生摘要和長條圖。  
  
在此步驟中，您將會重複使用資料來源來進行一些快速分析，然後提升資料︰  
  
## 查詢資料  
首先，取得一份資料行和其資料類型的清單。  
  
1.  使用函數 *rxGetVarInfo* 並指定您想要分析的資料來源︰  
  
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
  
## 修改中繼資料  
所有的變數會儲存為整數，但某些變數代表類別的資料 – 在 R 中稱為「因素變數」。例如，資料行 *state* 包含數字，用來作為 50 個州再加上華盛頓哥倫比亞特區的識別碼。  為了讓您更輕鬆地了解資料，您將數字取代為各州縮寫的清單。  
  
在此步驟中，您將提供包含縮寫的字串向量，然後將這些類別的值對應至原始的整數識別碼。 此變數就緒之後，您將在 *colInfo* 引數使用它，指定要將此資料行視為因素來處理。 之後，每次分析或匯入此資料時，將使用縮寫，並將資料行視為因素來處理。  
  
1.  一開始先建立 R 變數 *stateAbb*，以及定義要新增給它的字串向量，如下所示︰  
  
    ```R  
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",     
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",   
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",   
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",   
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")  
  
    ```  
  
2.  接下來，建立名為 *ccColInfo* 的資料行資訊物件，指定現有整數值對類別層級 (各州的縮寫) 的對應。  
  
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
  
3.  若要建立使用更新資料的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源，請如之前一樣呼叫 *RxSqlServerData* 函數，但新增 *colInfo* 引數。  
  
    ```R  
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,  
    table = sqlFraudTable, colInfo = ccColInfo,  
    rowsPerRead = sqlRowsPerRead)   
    ```  
  
    -   針對 *table* 參數，傳入變數 *sqlFraudTable*，其中包含您稍早建立的資料來源。    
    -   針對 *colInfo* 參數，傳入 *ccColInfo* 變數，其中包含資料行資料類型和因素層級。
    -   將資料行對應至縮寫，然後才使用它作為因數，實際上也能改善效能。 如需詳細資訊，請參閱 [R 和資料最佳化](https://msdn.microsoft.com/library/mt723575.aspx)  
  
4.  您現在可以使用 *rxGetVarInfo* 函數檢視新資料來源中的變數。  
  
    ```R  
    rxGetVarInfo(data = sqlFraudDS)   
    ```  
  
**結果**  
  
*Var 1: custID, Type: integer*  
*Var 2: gender       2 factor levels: Male Female*  
*Var 3: state       51 factor levels: AK AL AR AZ CA ...VT WA WI WV WY*  
*Var 4: cardholder       2 factor levels: Principal Secondary*  
*Var 5: balance, Type: integer*  
*Var 6: numTrans, Type: integer*  
*Var 7: numIntlTrans, Type: integer*  
*Var 8: creditLine, Type: integer*  
*Var 9: fraudRisk, Type: integer*  
  
現在您指定的三個變數 (_gender_、_state_ 和 _cardholder_) 被視為因素。  
  
## 下一個步驟  
[定義及使用計算內容 &#40;資料科學深入探討&#41;](../../advanced-analytics/r-services/define-and-use-compute-contexts-data-science-deep-dive.md)  
  
## 上一個步驟  
[使用 RxSqlServerData 建立 SQL Server 資料物件](../../advanced-analytics/r-services/create-sql-server-data-objects-using-rxsqlserverdata.md)  
  
## 另請參閱  
[資料科學深入探討︰使用 RevoScaleR 套件](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
