---
title: "使用 FOR JSON 將查詢結果格式化為 JSON (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON"
  - "JSON, 匯出"
  - "匯出 JSON"
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# 使用 FOR JSON 將查詢結果格式化為 JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  將 **FOR JSON** 子句加入至 **SELECT** 陳述式，以將資料從 SQL Server 匯出為 JSON，或將查詢結果格式化為 JSON。  
  
 當您使用 **FOR JSON** 子句，您可以明確指定輸出的架構，或讓 SELECT 陳述式的架構決定輸出。  
  
-   **使用 PATH 模式搭配 FOR JSON 子句**。 當您使用 **PATH** 模式搭配 **FOR JSON** 子句時，您保有 JSON 輸出格式的完整控制權。 您可以建立包裝函式物件和巢狀複雜屬性。  
  
-   **使用 AUTO 模式搭配 FOR JSON 子句**。 當您使用 **AUTO** 模式搭配 **FOR JSON** 子句時，JSON 輸出會根據 SELECT 陳述式的結構自動格式化。  
  
 使用 **FOR JSON** 子句，將來自用戶端應用程式的 JSON 輸出格式設定委派給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如需詳細資訊，請參閱[在 SQL Server 和用戶端應用程式中使用 FOR JSON 輸出 &#40;SQL Server&#41;](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)。  
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png "FOR JSON")  
  
## 使用 PATH 模式搭配 FOR JSON 子句  
 以下是使用 **PATH** 模式搭配 **FOR JSON** 子句的範例。

在 **PATH** 模式中，您可以使用點語法 (例如 `'Item.Price'`) 來格式化巢狀的輸出。 此範例也會使用 **ROOT** 選項來指定具名根項目。  
-   如需詳細資訊和範例，請參閱[以 PATH 模式格式化巢狀的 JSON 輸出 &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md)。
-   如需語法和使用方式，請參閱 [FOR Clause &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)。  
  
 ![Diagram of flow of FOR JSON output](../../relational-databases/json/media/forjson-example1.png "Diagram of flow of FOR JSON output")  
  
## 使用 AUTO 模式搭配 FOR JSON 子句  
 以下是使用 **AUTO** 模式搭配 **FOR JSON** 子句的範例查詢。

在 **AUTO** 模式中，SELECT 陳述式的結構決定 JSON 輸出的格式。 根據預設， **null** 值不會包含在輸出中。 您可以使用 **INCLUDE_NULL_VALUES** 來變更此行為。  
  
-   如需詳細資訊和範例，請參閱[使用 AUTO 模式自動格式化 JSON 輸出 &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md)。
-   如需語法和使用方式，請參閱 [FOR Clause &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)。  
  
 **查詢：**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **結果**  
  
```json  
[   
   { "name": "John" },  
   { "name": "Jane", "surname": "Doe" }  
]  
  
```  
  
## 利用選項搭配 FOR JSON 子句控制 JSON 輸出  
 使用下列選項控制 **FOR JSON** 子句的輸出。  
  
 [將根節點與根選項加入至 JSON 輸出 &#40;SQL Server&#41;](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md)  
 若要將單一最上層元素新增至 JSON 輸出，請指定 **ROOT** 選項。 如果您未指定 **ROOT** 選項，則 JSON 輸出不會有根項目。  
  
 [使用 INCLUDE_NULL_VALUES 選項在 JSON 輸出中包含 Null 值 &#40;SQL Server&#41;](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md)  
 若要在 JSON 輸出中包含 Null 值，請指定 **INCLUDE_NULL_VALUES** 選項。 如果您未指定此選項，輸出就不會在查詢結果中包含 NULL 值的 JSON 屬性。  
  
 [使用 WITHOUT_ARRAY_WRAPPER 選項從 JSON 輸出移除方括弧 &#40;SQL Server&#41;](../../relational-databases/json/remove square brackets from json - without_array_wrapper option.md)  
 若要移除預設圍住 **FOR JSON** 子句之 JSON 輸出的方括弧，請指定 **WITHOUT_ARRAY_WRAPPER** 選項。 使用此選項以產生單一 JSON 物件做為輸出。 如果您未指定此選項，JSON 輸出會以方括弧括住。  
  
 如需您在 **FOR JSON** 子句的輸出中所看到之項目的詳細資訊，請參閱本章節中的下列主題。  
  
 [FOR JSON 如何將 SQL Server 資料類型轉換為 JSON 資料類型 &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server.md)  
 **FOR JSON** 子句使用本主題中描述的規則，在 JSON 輸出中將 SQL 資料類型轉換為 JSON 類型。  
  
 [FOR JSON 如何逸出特殊字元和控制字元 &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)  
 **FOR JSON** 子句會逸出特殊字元，並在 JSON 輸出中代表控制字元，如本主題中所描述。  
  
## FOR JSON 子句的輸出  
 **FOR JSON** 子句的輸出具有下列特性。  
  
1.  結果集包含單一資料行。 小型結果集會包含單一資料列。 大型結果集包含多個資料列。  
  
     ![Example of FOR JSON output](../../relational-databases/json/media/forjson-example2.png "Example of FOR JSON output")  
  
2.  結果會格式化為 JSON 物件陣列。  
  
    -   陣列中的元素數目等於結果中的資料列數目。  
  
    -   結果集中的每個資料列會成為陣列中個別的 JSON 物件。  
  
    -   結果集中的每個資料行會成為 JSON 物件的屬性。  
  
3.  資料行名稱與其值會根據 JSON 語法逸出。  
  
 以下是示範 JSON 輸出格式的範例。  
  
 **查詢結果**  
  
|||||  
|-|-|-|-|  
|**A**|**B**|**C**|**D**|  
|10|11|12|X|  
|20|21|22|Y|  
|30|31|32|Z|  
  
 **JSON 輸出**  
  
```json  
[  
  { "A":10, "B":11, "C":12, "D":"X" },  
  { "A":20, "B":21, "C":22, "D":"Y" },  
  { "A":30, "B":31, "C":32, "D":"Z" }  
]  
```  
  
## 深入了解 SQL Server 中的 FOR JSON 與內建 JSON 支援  
 [Microsoft 專案經理 Jovan Popovic 的部落格文章](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## 另請參閱  
 [FOR 子句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)   
 [在 SQL Server 和用戶端應用程式中使用 FOR JSON 輸出 &#40;SQL Server&#41;](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  