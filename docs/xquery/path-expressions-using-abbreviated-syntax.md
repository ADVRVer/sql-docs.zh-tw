---
title: 在路徑運算式中使用縮寫語法 |Microsoft Docs
description: 瞭解如何在 XQuery 路徑運算式中使用縮寫語法。
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b8270babb8fe592c050a9352a7fd687660b178e
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920094"
---
# <a name="path-expressions---using-abbreviated-syntax"></a>路徑運算式 - 使用縮寫語法
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]

  [瞭解 XQuery 中路徑運算式](../xquery/path-expressions-xquery.md)的所有範例，都使用未縮寫的路徑運算式語法。 在路徑運算式中軸步的不縮寫語法包含軸名稱與節點測試，並以雙冒號分隔，後面接著零步或多步的限定詞。  
  
 例如：  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 XQuery 支援在路徑運算式中使用下列縮寫：  
  
-   **子**軸是預設軸。 因此，可以從運算式中的步驟省略**child：：** axis。 例如，`/child::ProductDescription/child::Summary` 可以撰寫成 `/ProductDescription/Summary`。  
  
-   **屬性**軸可以縮寫為 @ 。 例如，`/child::ProductDescription[attribute::ProductModelID=10]` 可以撰寫成 `/ProudctDescription[@ProductModelID=10]`。  
  
-   **/Descendant-or-self：： node （）/** 可以縮寫為//。 例如，`/descendant-or-self::node()/child::act:telephoneNumber` 可以撰寫成 `//act:telephoneNumber`。  
  
     上一個查詢擷取了所有儲存在 Contact 資料表中 AdditionalContactInfo 資料行的電話號碼。 AdditionalContactInfo 的架構是以專案 \<telephoneNumber> 可以出現在檔中任何地方的方式定義。 因此，若要擷取所有的電話號碼，您必須搜尋文件中的每個節點。 將會從文件的根節點開始搜尋，並繼續搜尋所有的下階節點。  
  
     下列查詢會擷取特定客戶連絡人的所有電話號碼。  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="https://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     如果您以縮寫語法 `//act:telephoneNumber` 取代路徑運算式，您會收到相同的結果。  
  
-   步驟中的**self：： node （）** 可以縮寫為單一點（.）。 不過，點不等於或可與**self：： node （）** 互換。  
  
     例如，在下列查詢中，點的使用代表是一個值且不是節點：  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   步驟中的**父系：： node （）** 可以縮寫為雙點（..）。  
  
  
