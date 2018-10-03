---
title: UPDATE、 DELETE 和 INSERT 陳述式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92fb7b0e9722c52c7f1e9fc071d434f531b2fc46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721906"
---
# <a name="update-delete-and-insert-statements"></a>UPDATE、DELETE 以及 INSERT 陳述式
以 SQL 為基礎的應用程式對資料表進行變更，藉由執行**更新**，**刪除**，並**插入**陳述式。 這些陳述式屬於 Minimum SQL 文法的一致性層級，而且必須支援的所有驅動程式和資料來源。  
  
 這些陳述式的語法是：  
  
 **更新***資料表名稱*   
  
 **設定***資料行識別碼* **=** {*運算式* &#124; **NULL**}  
  
 [**，** *資料行識別碼* **=** {*運算式* &#124; **NULL**}]...  
  
 [**何處***搜尋條件*]  
  
 **DELETE FROM** *資料表名稱*[**位置***搜尋條件*]  
  
 **INSERT INTO** *資料表名稱*[**(* * * 資料行識別碼*[* *，** *資料行識別碼*]...**)**]  
  
 {*查詢規格* &#124; **的值 (* * * 插入值*[* *，** *插入值*]...**)**}  
  
 請注意，*查詢規格*項目是只有在核心和 Extended SQL 文法，而且有效*運算式*並*搜尋條件*項目變得更複雜的核心和 Extended SQL 文法。  
  
 像其他 SQL 陳述式中，**更新**，**刪除**，和**插入**陳述式通常會更有效率使用參數時。 例如，下列陳述式可以備妥，並重複執行，以將多個資料列插入 Orders 資料表中：  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 這種效率可以增加所傳遞的參數值的陣列。 如需有關陳述式參數和參數值的陣列的詳細資訊，請參閱[陳述式參數](../../../odbc/reference/develop-app/statement-parameters.md)。
