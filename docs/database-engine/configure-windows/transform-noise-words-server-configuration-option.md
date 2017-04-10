---
title: "轉換非搜尋字伺服器組態選項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "全文檢索查詢 [SQL Server], 效能"
  - "轉換非搜尋字選項"
  - "非搜尋字 [全文檢索搜尋]"
  - "全文檢索搜尋 [SQL Server] 停用字詞"
  - "停用字詞 [全文檢索搜尋]"
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# 轉換非搜尋字伺服器組態選項
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  如果屬於[停用字詞](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)的非搜尋字造成全文檢索查詢的布林運算傳回零個資料列，請使用 [轉換非搜尋字] 伺服器組態選項來隱藏錯誤訊息。 若全文檢索查詢使用的 CONTAINS 述詞中，布林運算或 NEAR 運算有包括非搜尋字，則這個選項很有幫助。 下表說明可能的值。  
  
|值|描述|  
|-----------|-----------------|  
|0|不轉換非搜尋字 (或停用字詞)。 當全文檢索查詢包含非搜尋字時，此查詢會傳回零個資料列，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會引發警告。 這是預設行為。<br /><br /> 注意：這項警告是執行階段的警告。 因此，如果查詢中的全文檢索子句並未執行，就不會引發此警告。 若為本機查詢，只會引發一則警告，即使有多個全文檢索查詢子句也一樣。 若為遠端查詢，連結的伺服器可能不會轉送錯誤。因此，可能不會引發此警告。|  
|1|轉換非搜尋字 (或停用字詞)。 忽略這些字，並評估查詢的其餘部分。<br /><br /> 如果非搜尋字指定在鄰近詞彙中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會將其移除。 例如，非搜尋字 `is` 會從 `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')` 中移除，將搜尋查詢轉換為 `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`。 請注意，`CONTAINS(<column_name>, 'NEAR(hello,is)')` 只會轉換成 `CONTAINS(<column_name>, hello)`，因為只有一個有效的搜尋詞彙。|  
  
## 轉換非搜尋字設定效果  
 本節將說明包含非搜尋字 "`the`" 的查詢行為 (在 [轉換非搜尋字] 的替代設定底下)。  假設範例全文檢索查詢字串會針對包含下列資料的資料表資料列執行：`[1, "The black cat"]`。  
  
> [!NOTE]  
>  所有的這類案例都可以產生非搜尋字警告。  
  
-   轉換非搜尋字設為 0：  
  
    |查詢字串|結果|  
    |------------------|------------|  
    |"`cat`" AND "`the`"|無結果 ("`the`" AND "`cat`" 的行為是相同的)。|  
    |"`cat`" NEAR "`the`"|無結果 ("`the`" NEAR "`cat`" 的行為是相同的)。|  
    |"`the`" AND NOT "`black`"|搜尋支援|  
    |"`black`" AND NOT "`the`"|搜尋支援|  
  
-   轉換非搜尋字設為 1：  
  
    |查詢字串|結果|  
    |------------------|------------|  
    |"`cat`" AND "`the`"|識別碼為 1 之資料列的叫用|  
    |"`cat`" NEAR "`the`"|識別碼為 1 之資料列的叫用|  
    |"`the`" AND NOT "`black`"|搜尋支援|  
    |"`black`" AND NOT "`the`"|識別碼為 1 之資料列的叫用|  
  
## 範例  
 下例會將 [轉換非搜尋字] 設為 `1`。  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## 另請參閱  
 [伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)  
  
  